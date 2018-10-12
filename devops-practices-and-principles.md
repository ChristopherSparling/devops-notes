# Devops Practices and Principles
## **Module 1: DevOps Fundamentals**
### **Definitions:**
_Release Pipeline_ 
> Process that dictates how you deliver software to your end users; practically, an implementation of that pattern. Begins with code in VC and ends with deployed code
  
_Artifact_
>  One of many kinds of tangible by-products produced during the development of software. 
> 
> Some artifacts (e.g., use cases, class diagrams, and other Unified Modeling Language (UML) models, requirements and design documents) help describe the function, architecture, and design of software. Other artifacts are concerned with the process of development itself—such as project plans, business cases, and risk assessments. [Wiki](https://en.wikipedia.org/wiki/Artifact_(software_development))

_Continuous Delivery_
>Means that deployments are triggered automatically after a build completes

_Continuous Testing_
> Execution of tests repeatedly against a code base and deployment environment

_Idempotence_
> the property that a deployment command always sets the target environment into the same configuration, regardless of starting state

_Build Agent_
> A process that checks out source code, downloads artifacts of related builds, and executes the build process

_Toolchain_
> A set or combination of tools that aid in the delivery, development, and management of applications throughout the systems development life cycle, as coordinated by an organisation that uses DevOps practices.

## DevOps Practices and Habits
**Seven key DevOps practices:**
- Configuration management
    - Understanding what is being deployed, how it is deployed, and the *configuration* of what's entering production
- Release management
    - Understanding and controlling how a release pipeline we can trust is being built
- Continuous integration
    - The idea of continously testing code, compiling on check in and every version control commit
- Continuous deployment
    - Moving changes into a test environment minimally, and potentially out to production, on a rapid cadence
- Infrastructure as Code
    - The making sure that when code is deployed there is related infrastructure and that code is checked into version control
- Test automation
    - Automation of deployment tests, integration tests, UI tests, UX tests, etc.
- Application performance monitoring
    - Observing production applications for usage information in addition to performance and error data
 
**Seven DevOps habits:**
- Team autonomy and enterprise alignment
- Rigorous management of technical debt
- Focus on flow of customer value
- Hypothesis-driven development
- Evidence gathered in production
- Live-site culture
- Manage infrastructure as a flexible resource

[Sam Guckenheimer Talk](https://devops.com/11626/)

## Version Control
Oft overlooked VC strategies:
- Setting up an appropriate branching strategy
- Enabling transparency by linking work items to code

## Testing in DevOps
**Automation is the key**. Automated unit, integration, coded UI, and load tests are common
**Use and iterative and incremental approach**. Depth of testing often progresses as an environment gets closer to production.
**Beta Testing**. Form of external user acceptance testing with release to limited audience to accumulate product feedback.
**Progressive Exposure**. Entails switching small numbers of users over to a new version of software for feedback, then increasing those exposed to it over time.
_Types of Testing_:
- Unit testing
    - Test units of system in isolation
- Integration testing
    - Test components together in scenarios
- UI Testing
    - Test components together in scenarios through the UI
- Load and Performance Testing
    - Test system at scale
- Manual and Exploratory Testing
    - Human intelligence waged against the application
Benefits: Quality gates, increased confidence in code quality

**Don't Tolerate Broken Tests**

---
## **Module 2: Standardizing Environments**
### Configuration Management
- less formal than traditional config management
- emphasizes encapsulation of configuration in code over formal documentation
- entails lighter weight, executable configs that allow config and environments as code


*Infrastructure as Code*: - entails defining environments, including networks, servers, and other compute resources, as a text file checked into CV and used as the base source for creating and updating those environments

*Configuration as Code*: define config of servers, code, and other resources as a text file checked into VC used as a base source for creating or updating those configs

### Ansible
- A config management and automation, open-source tool made with Python
- Uses YAML config files (*playbooks*) to describe a state or policy you want your remote systems to enforce or execute. They are the config, deployment, and orchestration language
- Uses SSH to execute commands on remote machines; i.e. it is agentless
- used to automate various tasks like cloud provisioning and workloads
- can provision and manage the lifecycle of a VM, manage different services and resources

*Example Playbook*
```yaml
- name: Create Azure VM
  hosts: localhost
  connection: local
  tasks:
  - name: Create VM
    azure_rm_virtualmachine:
      resource_group: myResourceGroup
      name: myVM
      vm_size: Standard_GS5-8
      admin_username: azureuser
      ssh_password_enabled: false
      ssh_public_keys: 
        - path: /home/azureuser/.ssh/authorized_keys
          key_data: "ssh-rsa CCDDV2aZ...WXhad10h"
      image:
        offer: UbuntuServer
        publisher: Canonical
        sku: '16.04-LTS'
        version: latest
```
Can include multiple configurations in the same playbook

## Benefits of Configuration Management
1. More maintainable
2. Fewer locations to update
3. Fewer mistakes
4. More secure
5. More reliable

*Advantages of Configuration as Code*
- Bugs easily reproducible
- Consistent configuration
- Increase deployment cadence to reduce amount of incremental change
- Treat environment and config scripts as executable documentation

*Types of IaC*
1. Declarative (functional)
    - states *what* the final state should be
2. Imperative (procedural)
    - states the how for the final state of the machine by executing through the steps in order to reach said state

*Two Configuration Methods in IaC*
1. Push
    - master server pushs configuration to the target machine
2. Pull
    - slave machine will pull configuration from master server
  
### IaaS, PaaS, and Containers
**IaaS:**
- Machines generally hosted
- Chosen env depends on application
- Scaling by machines, instead of percentage
- Example tools: Puppet, Chef, Vagrant, Ansible, Azure Resource Manage, PowerShell DSC

**PaaS:**
- Hosted platform to develop, manage, and run apoplications without maintaining infrastructure
- Chosen env depends on application
- Scaling by percentage, instead of machines
- Example tools: Config files, Powershell, shell scripts

**Container Environments (Docker)**
- Containers:
    - Partition into multiple environments with shared OS
    - Many containers can run on one instance of OS
- Tools orchestrate multiple Docker containers to create managed environments
- Example Tools: Mesosphere DCOS, Kubernetes, Azure Container Service, Docker Swarm

---
## Module 3: Building and Deploying to Production
**Continuous Integration:**
- Anyone can queue a build
- Consistency
- Includes tests and build quality
- Fast feedback
- Merging code when fresh
- Increasing use of automated tests
- Faster check-in cadence

**Application Deployment: Continuous Deployment**
- Anyone can queue a deployment
- automated tests are part of release
- Fast feedback
- Increasing cadence of deployment to production
- Use of blue/green deployments: use load balance to progressively expose users to new production server, if problem is detected redirect them to previous server

**Continuous Delivery**
- Encourages IaC and CaC
- Enables automated testing throughout the pipeline
- Provides visibility and fast feedback cycles
- Makes going to production a low-stress activity



