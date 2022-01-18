## Quiz : Development in Cloud
### 1. Why would a developer choose to store source code in Cloud Source Repositories? Choose all the answers that are correct (2 correct answers).
- [x] **To keep code private to a GCP project**
- [x] **To reduce work**
- [ ] To have total control over the hosting infrastructure
```
That's correct! Cloud Source Repositories integrates with Google Cloud IAM.
```
```
That's right! Cloud Source Repositories manages the hosting infrastructure for you.
```
<br/>

## Quiz : Cloud Functions
### 1. What is the advantage of putting event-driven components of your application into Cloud Functions?
- [ ] Cloud Functions means that processing always happens free of charge.
- [x] **Cloud Functions handles scaling these components seamlessly.**
```
Correct! Your code executes whenever an event triggers it, no matter whether it happens rarely or many times per second. That means you don't have to provision compute resources to handle these operations.
```
<br/>

## Quiz : Developing, Deploying, and Monitoring in the Cloud
### 1. Which statements are true about Stackdriver Logging? Choose all that are true (2 statements)
- [x] **Stackdriver Logging lets you view logs from your applications, and filter and search on them.**
- [x] **Stackdriver Logging lets you define metrics based on your logs.**
- [ ] Stackdriver Logging lets you define uptime checks.
- [ ] Stackdriver Logging requires that you store your logs in BigQuery or Cloud Storage.
- [ ] Stackdriver Logging requires the use of a third-party monitoring agent.
<br/>

### 2. Why might a GCP customer choose to use Cloud Functions?
- [x] **Their application contains event-driven code that they don't want to have to provision compute resources for.**
- [ ] Cloud Functions is the primary way to run Node.js applications in GCP.
- [ ] Their application has a legacy monolithic structure that they want to break apart into microservices with little developer effort.
- [ ] Cloud Functions is a free service for hosting compute operations.
<br/>

### 3. Why might a GCP customer choose to use Cloud Source Repositories?
- [x] **They don't want to host their own git instance, and they want to integrate with IAM permissions.**
- [ ] They want to host and manage their own git instance, and they want to integrate with IAM permissions.
- [ ] They want to host and manage their own git instance, and they don't want to integrate with IAM permissions.
- [ ] They don't want to host their own git instance, and they don't want to integrate with IAM permissions.
<br/>

### 4. Why might a GCP customer choose to use Deployment Manager?
- [x] **Deployment Manager is an infrastructure management system for GCP resources.**
- [ ] Deployment Manager is a version control system for your GCP infrastructure layout.
- [ ] Deployment Manager enforces maximum resource utilization and spending limits on your GCP resources.
- [ ] Deployment Manager is an infrastructure management system for Kubernetes pods.
<br/>

### 5. You want to define alerts on your GCP resources, such as when health checks fail. Which is the best GCP product to use?
- [x] **Stackdriver Monitoring**
- [ ] Stackdriver Debugger
- [ ] Stackdriver Trace
- [ ] Deployment Manager
- [ ] Cloud Functions
<br/>