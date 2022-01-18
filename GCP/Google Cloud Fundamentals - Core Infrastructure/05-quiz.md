## Quiz : Containers
### 1. Containers are loosely coupled to their environments. What does that mean? Choose all the statements that are true. (3 correct answers)
- [x] **Containers are easy to move around.**
- [ ] Containers don't require any particular runtime binary.
- [x] **Deploying a containerized application consumes less resources and is less error-prone than deploying an application in virtual machines.**
- [ ] Containers package your application into equally sized components.
- [x] **Containers abstract away unimportant details of their environments.**
<br/>

### 2. True or false: each container has its own instance of an operating system.
- [x] **False.**
- [ ] True
```
Correct! Containers start much faster than virtual machines and use fewer resources, because each container does not have its own instance of the operating system.
```
<br/>

## Quiz : Kubernetes
### 1. What is a Kubernetes cluster?
- [ ] A group of containers that provide high availability for applications
- [x] **A group of machines where Kubernetes can schedule workloads**
```
That's correct. A Kubernetes cluster is a group of machines where Kubernetes can schedule containers in pods. The machines in the cluster are called “nodes.”
```
<br/>

### 2. What is a Kubernetes pod?
- [ ] A group of clusters
- [ ] A group of nodes
- [x] **A group of containers**
```
That's correct. In Kubernetes, a group of one or more containers is called a pod. Containers in a pod are deployed together. They are started, stopped, and replicated as a group. The simplest workload that Kubernetes can deploy is a pod that consists only of a single container.
```
<br/>

## Quiz : Kubernetes Engine
### 1. True or false: Google keeps Kubernetes Engine refreshed with successive versions of Kubernetes.
- [x] **True.**
- [ ] False.
```
That's correct! The Kubernetes Engine team periodically performs automatic upgrades of your cluster master to newer stable versions of Kubernetes, and you can enable automatic node upgrades too.
```
<br/>

### 2. Where do the resources used to build Kubernetes Engine clusters come from?
- [x] **Compute Engine**
- [ ] App Engine
- [ ] Bare-metal servers
```
Correct! Because the resources used to build Kubernetes Engine clusters come from Compute Engine, Kubernetes Engine gets to take advantage of Compute Engine’s and Google VPC’s capabilities.
```
<br/>

## Quiz : Containers, Kubernetes, and Kubernetes Engine
### 1. Does Google Cloud Platform offer its own tool for building containers (other than the ordinary docker command)?
- [ ] No; all customers use the ordinary docker command.
- [x] **Yes; the GCP-provided tool is an option, but customers may choose not use it.**
- [ ] Kubernetes Engine customers must use the GCP-provided tool.
<br/>

### 2. In Kubernetes, what does "pod" refer to?
- [ ] A popular management subsystem
- [x] **A group of containers that work together**
- [ ] A group of clusters that work together
- [ ] A popular logging subsystem
<br/>

### 3. Identify two reasons for deploying applications using containers. (Choose 2 responses.)
- [x] **Simpler to migrate workloads**
- [x] **Consistency across development, testing, production environments**
- [ ] Tight coupling between applications and operating systems
- [ ] No need to allocate resources in which to run containers
<br/>

### 4. Where do your Kubernetes Engine workloads run?
- [ ] In clusters implemented using Cloud Functions
- [x] **In clusters built from Compute Engine virtual machines**
- [ ] In clusters that are built into GCP, not separately manageable
- [ ] In clusters implemented using App Engine
<br/>

### 5. *True or False:* Kubernetes allows you to manage container clusters in multiple cloud providers.
- [x] **True**
- [ ] False
<br/>

### 6. *True or False:* Google Cloud Platform provides a secure, high-speed container image storage service for use with Kubernetes Engine.
- [x] True
- [ ] False
<br/>
