## Quiz : App Engine
### 1. True or false: App Engine is a better choice for a web application than for long-running batch processing.
- [ ] **True.**
- [ ] False.
```
That's correct! App Engine will scale your application automatically in response to the amount of traffic it receives. That’s why App Engine is especially suited for applications where the workload is highly variable, like a web application.
```
<br/>

### 2. True or false: App Engine just runs applications; it doesn't offer any services to the applications it runs.
- [ ] True.
- [x] **False.**
```
That's correct! App Engine offers NoSQL databases, in-memory caching, load balancing, health checks, logging, and user authentication to applications running in it.
```
<br/>

## Quiz : App Engine Flexible and Standard Environments
### 1. Which of these criteria would make you choose App Engine Flexible Environment, rather than Standard Environment, for your application? Choose all that are correct (2 correct responses).
- [ ] Daily free usage quota
- [ ] Finer-grained scaling
- [x] **Wider range of choices for application language**
- [x] **Ability to ssh in**
```
That's correct! At the time of this writing, App Engine Standard Environment supports Java, Python, PHP, and Go, but in the Flexible Environment, you upload your own runtime to run code in a language of your choice.
```
```
That's correct. App Engine Flexible Environment lets you ssh into the virtual machines in which your application runs.
```
<br/>

### 2. True or false: App Engine Flexible Environment applications let their owners control the geographic region where they run.
- [x] **True.**
- [ ] False.
```
That's correct! You get to choose which region your applications run in.
```
<br/>

## Quiz : Applications in the Cloud
### 1. Name 3 advantages of using the App Engine Flexible Environment over App Engine Standard. Choose all that are true (3 correct answers).
- [x] **You can SSH in to your application**
- [x] **Your application can write to local disk**
- [ ] Google provides automatic in-place security patches
- [ ] Your application can execute code in background threads
- [x] **You can install third-party binaries**
<br/>

### 2. Name 3 advantages of using the App Engine Standard Environment over App Engine Flexible. Choose all that are true (3 correct answers).
- [x] **Google provides and maintains runtime binaries**
- [x] **Billing can drop to zero if your application is idle**
- [x] **Scaling is finer-grained**
- [ ] You can install third-party binaries
- [ ] You can choose any programming language
<br/>

### 3. You want to support developers who are building services in GCP through API logging and monitoring. Which GCP service should you choose?
- [x] **Cloud Endpoints**
- [ ] Apigee Edge
<br/>

### 4. Which statements are true about App Engine? Choose all that are true (2 correct answers).
- [x] **App Engine manages the hardware and networking infrastructure required to run your code.**
- [x] **It is possible for an App Engine application's daily billing to drop to zero.**
- [ ] App Engine charges you based on the resources you pre-allocate rather than based on the resources you use.
- [ ] Developers who write for App Engine do not need to code their applications in any particular way to use the service.
- [ ] App Engine requires you to supply or code your own application load balancing and logging services.
<br/>

### 5. You want to gradually decompose a pre-existing monolithic application, not implemented in GCP, into microservices. Which GCP service should you choose?
- [x] **Apigee Edge**
- [ ] Cloud Endpoints
<br/>

### 6. You want to do business analytics and billing on a customer-facing API. Which GCP service should you choose?
- [x] **Apigee Edge**
- [ ] Cloud Endpoints
<br/>