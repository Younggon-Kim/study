## The Google Cloud Platform resource hierarchy
### 1. Choose the correct completion: Services and APIs are enabled on a per-__________ basis.<br/>
- [ ] Billing account
- [ ] Organization
- [x] **Project**
- [ ] Folder
<br/>

### 2. True or false: Google manages every aspect of Google Cloud Platform customers' security. <br/>
- [ ] True
- [x] **False**
<br/>
```
You chose the correct response!
Google Cloud Platform manages the lower layers of the security stack, such as physical security, and gives customers tools for managing the higher layers.
```
<br/>

### 3. Your company has two GCP projects, and you want them to share policies. What is the less error-prone way to set this up?<br/>
- [ ] Duplicate all the policies on one project onto the other. 
- [x] **Place both projects into a folder, and define the policies on the folder.**
<br/><br/>

## Resources and IAM
### 1. When would you choose to have an organization node? (Choose all that are correct. Choose 2 responses.)
- [x] When you want to create folders.
- [ ] When you want to organize resources into projects.
- [x] When you want to apply organization-wide policies centrally.
- [ ] There is no choice; organization nodes are mandatory.
```
Folders require an organization node. Organization nodes are optional, but if you want to create folders, having one is mandatory.

Organization nodes let you apply policies centrally.
Organization nodes are optional, but if you want to define policies that apply to all the projects in your organization, having one is mandatory.
```
<br/>

### 2. Order these IAM role types from broadest to finest-grained.
- [x] **Primitive roles, predefined roles, custom roles**
- [ ] Custom roles, predefined roles, primitive roles
- [ ] Predefined roles, custom roles, primitive roles
<br/>

### 3. Can IAM policies that are implemented higher in the resource hierarchy take away access that is granted by lower-level policies?
- [ ] Yes.
- [x] **No.**


## Quiz : Getting Started with Google Cloud Platform
### 1. Consider a single hierarchy of GCP resources. Which of these situations is possible? (Choose all that are correct. Choose 3 responses.)
- [x] **There is an organization node, and there are no folders.**
- [x] **There is no organization node, and there are no folders.**
- [ ] There is no organization node, but there is at least one folder.
- [x] **There is an organization node, and there is at least one folder.**
- [ ] There are two or more organization nodes

### 2. Service accounts are used to provide which of the following? (Choose all that are correct. Choose 3 responses.)
- [x] **A way to restrict the actions a resource (such as a VM) can perform**
- [x] **Authentication between Google Cloud Platform services**
- [ ] A set of predefined permissions
- [x] **A way to allow users to act with service account permissions**

### 3. Which statement is true about billing for solutions deployed using Cloud Marketplace (formerly known as Cloud Launcher)?
- [ ] Cloud Marketplace solutions are always free.
- [x] **You pay only for the underlying GCP resources you use, with the possible addition of extra fees for commercially licensed software.**
- [ ] You pay only for the underlying GCP resources you use; Google pays the license fees for commercially licensed software.
- [ ] After a trial period, each Cloud Marketplace solution assesses a fixed recurring monthly fee.

### 4. How do GCP customers and Google Cloud Platform divide responsibility for security?
- [ ] All aspects of security are the customer's responsibility.
- [x] **Google takes care of the lower parts of the stack, and customers are responsible for the higher parts.**
- [ ] Google takes care of the higher parts of the stack, and customers are responsible for the lower parts.
- [ ] All aspects of security are Google's responsibility.

### 5. *True or False*: In Google Cloud IAM: if a policy applied at the project level gives you Owner permissions, your access to an individual resource in that project might be restricted to View permission if someone applies a more restrictive policy directly to that resource.
- [ ] True
- [x] **False**
```
Correct! Policies are a union of those applied on resource itself and those inherited from higher levels in the hierarchy.
If a parent policy is **less** restrictive, it overrides a more restrictive policy applied on the resource.
If a parent policy is **more** restrictive, it does not override a less restrictive policy applied on the resource.
Therefore, access granted at a higher level in the hierarchy cannot be taken away by policies applied at a lower level in the hierarchy.
```

### 6. What is the difference between IAM primitive roles and IAM predefined roles?
- [ ] Primitive roles only apply to the owner of the GCP project. Predefined roles can be associated with any user.
- [x] **Primitive roles affect all resources in a GCP project. Predefined roles apply to a particular service in a project.**
- [ ] Primitive roles only allow viewing, creating, and deleting resources. Predefined roles allow any modification.
- [ ] Primitive roles can only be granted to single users. Predefined roles can be associated with a group.
- [ ] Primitive roles are changeable once assigned. Predefined roles can never be changed.

### 7. *True or False*: All Google Cloud Platform resources are associated with a project.
- [x] **True**
- [ ] False
```
Correct! All Google Cloud Platform resources are associated with a project.
```

### 8. Which of these values is globally unique, permanent, and unchangeable, but chosen by the customer?
- [ ] The project number
- [x] **The project ID**
- [ ] The project name
- [ ] The project's billing credit-card number
