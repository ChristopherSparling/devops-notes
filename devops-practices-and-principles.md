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
