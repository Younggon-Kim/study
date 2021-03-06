# Kubernetes Introduction

## What is Kubernetes
Kubernetes 는 컨테이너화된 애플리케이션을 배포하기 위한 오픈소스 오케스트레이터
- 클라우드 네이티브 애플리케이션을 구축하기 위한 표준 API 로 여겨짐
- 신뢰성과 확장성을 위한 분산 시스템을 구축하고 배포하는데 필요한 소프트웨어를 제공
  - 신뢰성
    - 시스템의 한 부분이 고장 났거나 동작을 멈춘 경우에도 전체 시스템이 실패하면 안된다.
  - 가용성(availability)
    - 소프트웨어가 rollout 되는 동안이나 그 밖의 유지 관리 작업 중에도 시스템은 가용성을 보장해야 한다.
  - 확장성
    - 세계적인 서비스를 제공함으로써 서비스를 구현하는 분산 시스템은 지속적으로 증가하는 사용량을 인지해 근본적인 재설꼐 없이도 시스템 용량을 늘릴 수 있어야 한다.
<br/><br/>

## 속도
- 새로운 컴포넌트 및 기능을 개발할 수 있는 속도
  - 다른 누군가에 의해 이뤄진 혁신에 대응할 수 있는 속도
- 하지만 시간당 혹은 일별(per day)로 제공할 수 있는 기능의 수가 아닌 높은 가용성을 갖는 서비스를 유지하면서 제공할 수 있는 항목의 수

## 컨테이너 & 쿠버네티스의 핵심 개념
- 불변성(immutability)
- 선언형 컨피규레이션(declarative configuration)
- 온라인 자가 치유 시스템(online self-healing system)

## 불변성의 가치
