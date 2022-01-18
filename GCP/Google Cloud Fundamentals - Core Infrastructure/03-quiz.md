## Virtual Private Cloud (VPC) Network
### 1. True or false? In Google Cloud VPCs, subnets have regional scope.
- [x] **True**
- [ ] False
```
That's correct.
VPC subnets can span the zones that make up a region. 
This is beneficial because your solutions can incorporate fault tolerance without complicating your network topology.
```
<br/><br/>

### 2. True or false: If you increase the size of a subnet in a custom VPC network, the IP addresses of virtual machines already on that subnet might be affected.
- [ ] True
- [x] **False**
```
That's correct. 
You can dynamically increase the size of a subnet in a custom network by expanding the range of IP addresses allocated to it. 
Doing that doesn’t affect already configured VMs.
```
<br/><br/>


## Compute Engine
### 1. True or false: You can create Compute Engine virtual machines from the command line.
- [x] **True**
- [ ] False 
```
Correct! 
It's advantageous to create virtual machines from a command line when you want their configurations to be scripted and repeatable.
The gcloud command, provided by Google Cloud as part of the GCP SDK, can create virtual machines with parameters you specify.
```
<br/><br/>

### 2. What is the main reason customers choose Preemptible VMs?
- [x] **To reduce cost.**
- [ ] To improve performance.
```
That's correct!
The per-hour price of preemptible VMs incorporates a substantial discount.
```
<br/><br/>

## Quiz Answers
### 1. Name 3 networking services available to your applications on Google Cloud Platform.
- Cloud Virtual Network
- Cloud Interconnect
- Cloud DNS
- Cloud Load Balancing
- Cloud CDN.
<br/><br/>

### 2. Name 3 Compute Engine pricing features.
- Per-second billing
- custom machine types
- preemptible instances.

### 3. True or False: Google Cloud Load Balancing lets you balance HTTP traffic across multiple Compute Engine regions.
- [x] **True**
- [ ] False 
<br/><br/>

## Quiz : Google Compute Engine and Networking
### 1. *True or False*: Google Cloud Load Balancing allows you to balance HTTP-based traffic across multiple Compute Engine *regions.*
- [x] **True**
- [ ] False
```
Correct! With global Cloud Load Balancing, your application presents a single front-end to the world.
```
<br/><br/>

### 2. An application running in a Compute Engine virtual machine needs high-performance scratch space. Which type of storage meets this need?
- [x] **Local SSD**
- [ ] SSD persistent
- [ ] Local standard
- [ ] Standard persistent
<br/><br/>

### 3. How do Compute Engine customers choose between big VMs and many VMs?
- [x] **Use big VMs for in-memory databases and CPU-intensive analytics; use many VMs for fault tolerance and elasticity**
- [ ] Use big VMs for fault tolerance and elasticity; use many VMs for in-memory databases and CPU-intensive analytics
<br/><br/>

### 4. How do VPC routers and firewalls work?
- [x] **They are managed by Google as a built-in feature.**
- [ ] They are managed by Google in virtual machines, which customers may tune or turn off.
- [ ] They are managed by Google in virtual machines, which customers may never modify.
- [ ] Customers provision virtual machines and run their routers and firewalls in them.
<br/><br/>

### 5. Choose an application that would be suitable for running in a Preemptible VM.
- [x] **A batch job that can be checkpointed and restarted**
- [ ] An interactive website
- [ ] An online relational database
- [ ] A batch job that cannot be checkpointed and restarted
<br/><br/>

### 6. A GCP customer wants to load-balance traffic among the back-end VMs that form part of a multi-tier application. Which load-balancing option should this customer choose?
- [ ] The regional load balancer
- [ ] The global SSL proxy
- [ ] The global HTTP(S) load balancer
- [ ] The global TCP proxy
- [x] **The regional internal load balancer**
<br/><br/>

### 7. For which of these interconnect options is a Service Level Agreement available?
- [x] **Dedicated Interconnect**
- [ ] Direct Peering
- [ ] Carrier Peering
- [ ] VPNs with Cloud Router
<br/><br/>

### 8. Which statement is true about Google VPC networks and subnets?
- [x] **Networks are global; subnets are regional**
- [ ] Networks are regional; subnets are zonal
- [ ] Networks are global; subnets are zonal
- [ ] Networks and subnets are global
<br/><br/>