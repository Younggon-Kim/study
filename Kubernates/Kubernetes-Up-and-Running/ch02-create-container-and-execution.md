# Ch2. Create Container & Execution

## Introduction
----
쿠버네티스는 분산 애플리케이션을 생성, 배포, 관리하기 위한 플랫폼
- 애플리케이션 컨테이너 이미지의 빌드 및 분산 시스템 구성 방법을 고려해야 함
<br/><br/>

일반 애플리케이션 개발의 문제점
- 특정 머신에 설치한 OS 의 외부 shared libraries 에 영향을 받음
- 다른 머신 혹은 운영체제로 이관했을 때, shared libraries 에 대한 의존성 때문에 문제가 발생함

전통적인 해결 방법
- 모든 프로그램이 시스템 상에서 동일한 버전의 shared libraries 를 공유하는 것
- 개발 팀/프로그램 간에 결합이 강해지고 복잡도 증가

Docker 로 해결!
- 기본 컨테이너 런타임 엔진인 Docker 를 사용하면 실행파일을 쉽게 패키징하고
- 다른 사람이 쉽게 내려 받을 수 있도록 레지스트리(registry; 컨테이너 이미지 저장소) 로 push 할 수 있음
- 컨테이너 레지스트리
  - 모든 주요 퍼블릭 클라우드에서 사용 가능
  - 클라우드 환경에서 이미지르르 빌드하는 서비스 또한 사용 가능
  - 오픈 소스나 상용 시스템을 사용해 자체 컨테이너 레지스트리를 구축 및 실행 가능
<br/><br/>

- 컨테이너 이미지는 애플리케이션과 관련된 의존성들을 root filesystem 에서 하나의 artifact 로 패키징함
- 가장 많이 사용되는 컨테이너 이미지는 Docker 이미지 포맷
  - OCI(Open Container Initiative) 에 의해 표준화
- 쿠버네티스는 Docker 및 기타 런타임 환경을 제공하여 Docker 및 OCI 호환 이미지 모두를 지원
- Docker 이미지
  - 컨테이너 이미지 내용을 기반으로 실행 애플리케이션이 구동될 수 있도록 컨테이너 런타임이 사용하는 메타데이터를 포함
<br/><br/>

## 컨테이너 이미지
----
컨테이너 이미지
- OS 컨테이너 내부에서 프로그램을 실행하는데 필요한 모든 파일을 캡슐화하는 바이너리 패키지

### Docker 이미지 포맷
- 가장 많이 사용하는 컨테이너 이미지 포맷
- OCI 프로젝트에서 Docker 및 여러 업체가 컨테이너 이미지 포맷을 표준화
  - 사실상 Docker 가 표준
- Docker 명령어로 컨테이너를 패키징, 배포, 실행
- 이련의 파일시스템 계층으로 구성됨
  - 각 계층은 이전 계층으로부터 파일을 추가, 제거, 수정한다 => 오버레이(overlay) 파일시스템

### 컨테이너 계층화
- '도커 이미지 포맷'?? '컨테이너 이미지'??
- 이미지
  - 단일 파일이 아니라 다른 파일을 가리키는 manifest 파일의 specification
- 컨테이너 이미지
  - 일련의 파일시스템 계층으로 구성
  - 각 계층은 이전 계층을 상속하고 수정함
  - 계층 순서는 상향식(아래에서 위쪽으로)

계층 순서는 상향식으로 아래에서 위쪽 방향이지만, 이해를 위해 bottom-up 방식으로 설명하면 다음과 같다.
B 과 C 는 A 에서 fork 되며, 기본 컨테이너 파일 외에는 서로 아무것도 공유하지 않음
```
.
├── A container : Debian 같은 기본적인 운영체제만 존재 
    ├── B container : A 컨테이너를 기반으로 Ruby v2.1.10 추가
    └── C container : A 컨테이너를 기반으로 Golang v1.6 추가
```

### 컨테이너 configuration
- features
  - 컨테이너 환경 설정
  - 애플리케이션의 엔트리 포인트를 실행하는 방법에 대한 지침을 제공
  - 네트워크 설정
  - 네임스페이스 격리
  - 리소스 제약 조건(cgroup) 및 실행 중인 컨테이너 인스턴스의 syscall 제한하는 방법

### 컨테이너 범주
1. 시스템 컨테이너
   - 가상 머신처럼 동작
   - 전체 부팅 프로세스를 실행
   - ssh, cron, syslog 같은 서비스를 포함
2. 애플리케이션 컨테이너
   - 단일 프로그램을 실행한다는 점에서 시스템 컨테이너와 다름
   - 컨테이너당 하나의 프로그램을 실행
<br/><br/>

## Docker 를 활용한 애플리케이션 이미지 빌드하기
----
Kubernets 같은 컨테이너 오케스트레이션 시스템
- 컨테이너로 구성된 분산 시스템을 구축하고 배포

### Docker file
컨테이너 이미지 생성을 자동화

Node.js 예제 프로그램

package.json
```json
{
    "name": "simple.json",
    "version": "1.0.0",
    "description": "A sample simple application for Kubernetes Up & Running",
    "main": "server.js",
    "scripts": {
        "start": "node server.js"
    },
    "author": ""
}
```
server.js
```javascript
var express = require('express');
var app = express();

app.get('/', function(req, res) {
    res.send('Hello World!')
});
app.listen(3000, function() {
    console.log('Listening on port 3000!');
    console.log('http://localhost:3000');
})
```

도커 이미지 패키징
- .dockerignore 와 도커 파일 2개의 파일을 추가로 생성해야 함
  - 도커 파일
    - 컨테이너 이미지를 작성하는 방법에 대한 레시피
  - .dockerignore
    - 이미지에 복사할 때 무시해야 하는 파일을 정의

.dockerignore
```
node_modules
```

도커 파일
```docker
# Node.js 10 이미지에서 시작
FROM node:10

# 모든 명령이 실행될 이미지 내부의 디렉토리를 지정
WORKDIR /usr/src/app

# 패키지 파일 복사 및 디펜던시 설치
COPY package*.json ./
RUN npm install

# 모든 앱 파일을 이미지에 복사
COPY . . 

# 컨테이너를 시작할 때 실행할 기본 커맨드 지정
CMD [ "npm", "start" ]


```