## Microservice Design pattern & architecture
### What is the difference between Design Architecture & Design Pattern
Differences between design and architecture patterns reflect their different uses. Architecture represents scaffolding, the frameworks that everything else sits upon. Design patterns represent a way to structure classes to solve common problems.

**Architecture Patterns** cocurs at higher level, no longer look at small piece of application but what defines the application.

**Design Pattern** dont tell us how the application should build, it only tell us what a specfic piece of code must do & what other piece of code should interact with it.
<br>
![image](https://user-images.githubusercontent.com/56182367/186626222-eb0cdf76-5db9-41a0-83bc-abba4b9926ca.png)

### Type Of Application Landscape Patterns
- **Monolith**: <br>Monolithic application describes a single-tiered software application in which the user interface and data access code are combined into a single program from a single platform. A monolithic application is self-contained and independent from other computing applications
<br>**Advantages**:
  - Easy to understand, implement & test
  - Easy Deployment
  - Ideal for limited Scope


  **Disadvantage**: (As application starts to grow)
  - Tight Coupling (Making it harder to move pieces of logic to other applications later
  - Easily leads to complex code (developer find it hard to modify or extend the application)
  - Can leads to **One size fits all for every subdomain**
  
**Example**:
![image](https://user-images.githubusercontent.com/56182367/186792681-beb448e4-34b0-4c33-b731-36e9e8c9ba45.png)

- **N-tier**: <br> It splits up the application into mulitple tiers. Each tier is resposible for a certain function to perform specific task,and it can be physically separated from the other tiers. Common N-tier application: 3-Tier (Presentation tier, Business logic tier, Data tier)<br>
 <br> **Advantages:**
  - Independent development
  - Scalability
  
  **Disadvantages:**
  - Changes ripple through tiers (Eg: New field in a form will require changes in User interface, business logic & database)
  
![image](https://user-images.githubusercontent.com/56182367/186804002-fe886341-e39f-49f6-96b4-2bdfeed32422.png)


![image](https://user-images.githubusercontent.com/56182367/186792107-8fc4dcb0-944a-46c4-b8dc-1a94915bc80c.png)

**Example:** ![image](https://user-images.githubusercontent.com/56182367/186792494-9f4deb90-8be3-4f78-8aa4-d144925feeb1.png)

- **Service-oriented:** An architecture that consist of multiple services that each service is a business activity.Separate services may consist of other underlying services.Service-oriented architecture will often includes standardization of data contracts between sevices & enterprise service bus.

  **Advantages:**
  - Services are loosely coupled
  - Scalability
  - No duplication of functionality
  
  **Disadvantages:**
  - Reduced aglity and team autonomy of separate teams as it requires some central governance
  - Costly (in terms of money, time & effort)
  - Many differing views. ( there's no clear view of what a true service-oriented architecture is)
  
  (Enterprise standardisation bus is the middleman betweent the different services providing standardisation throughtout the service)
  
  ![image](https://user-images.githubusercontent.com/56182367/186794042-183bd688-2f30-47fe-b044-44a15c1fed54.png)

**(ExploreCalifornia.ESB is the enterprise standardisation bus)**
![image](https://user-images.githubusercontent.com/56182367/186795755-b2460c1d-1f89-4e78-999a-63a0cd3682dc.png)

- **Microservices** Is an evolution of **Service-oriented architecture**.Its not only build the services but also responsible for running and maintaining it.This is in contrast with finishing the software and hand it over to another team. Services can called to another services point to point using a well known protocol like HTTP. There's no logic-heavy service bus **(ESB)** and modern microservices automate as much as possible, thus instead of just **automated test**, it also includes **automated deployment** & **monitoring**. The services are always running in containers like **Dockers** for eassy deployment and run the services

  **Advantages:**
  - Services are loosely coupled and easily scalable
  - Increased agility
  - Reliability (automation help reduces the chance of human errors)
  - Designed to handle errors from other services (Designed with failure in mind)
  
  **Disadvantages:**
  - Boundaries not always clear (even if it's clear now, it may change over time,thus not easy to refactor multiple microservices together)
  - Communication patterns can become complex. (can easily lose overview of all those separate services)
  
![image](https://user-images.githubusercontent.com/56182367/186803076-36f97a52-0a9d-4839-ba5d-42a5a9f8dc45.png)

**Example:**<br>
![image](https://user-images.githubusercontent.com/56182367/186804301-db5c5d51-8a6c-4457-9106-2d03889f6515.png)

- **Serverless:** Serverless architecture is an approach to software design that allows developers to build and run services without having to manage the underlying infrastructure. Developers can write and deploy code, while a cloud provider provisions servers to run their applications, databases, and storage systems at any scale. It can either have **Backend** as a service or **Function** as a service.

  **Advantages:**
  - Scale very easily(if there's a peak in the request, the platform can just spin up new instances of your function.
  - Reduce costs in development and operation
  - Very easy to experiment with new IDs because a new function is easily written & deployed
  
  **Disadvantages:**
  - Have to work with the constraints that the vendor enforce. Eg: the vendor might stop supporting a version of framework that you using & and is not easy to switch vendor
  - Tricky in maintain state in memory (Does not have a persistent state thus can be a problem for developers who need persistent data)
  - Suffer from cold start as the platform has to spin up new container.
 
 ### Backend as a Service(BaaS)
 - BaaS is a previously famous cloud-based computing model, that automates and manages the backend side of a web or mobile application development. Wll still have the application in traditional sense for the business logic, but it uses alot of third party services for other concerns. Eg: Cloud Services for Authentication, External Logging Service, External Database Provider.
  
 ### Function as a Service (FaaS)
 FaaS or Function as a Service is a platform that lets you run self-contained functions (code snippets) in the cloud.It Helps developers in creating or updating codes on the fly that could be executed with any interaction with its element on the page.

 ![image](https://user-images.githubusercontent.com/56182367/186810512-26fc7c32-e609-4879-81f5-b2abe9d42a9a.png)

  ![image](https://user-images.githubusercontent.com/56182367/186809152-b599b830-f91d-4402-9b12-ddf1773080c5.png)

- **Peer-to-peer:**
 Are a network of applications that communicate with each other without a central server in between them. The individual application dont have to be online all the time, they can connect and disconnect as they please and this means they need to **Wait** to discover each other as they might not have fixed URLs or IP addresses. Peer-to-peer applications serve a specific purpose,they are ideal for application that want to share their resources like **processing power, data, memory or storage**.

  **Advantages:**
  - Very cost effective because there is no central server. (Especially when organisation dont have to run all individual applications or machine.
  - Scaling is easy. 
  
  **Disadvantages:**
  - Possible security issues because the system is decentralized. (Eg: data sharing network=> Viruses can transfer more easily)
  = Only for specific scenario.
  - Is not easy to write this architecture.
  - Non trival to code

#### How Do We design these individual applications?
Ans: Application Structure Patterns
**Application Structure Patterns**are a category of patterns that defines how a single executable should be built.It is about the structure of a single exectuable and it can be part of a large application landscape.

Application Structure Patterns:
- Layered
- Microkernel
- Command Query Responsibility Segregation (CQRS)
- Event Sourcing
- Command Query Responsibility Segregation & event sourcing combined

**User Interface pattern (getting into details of how the user interacts with the application)**
- Model-view-controller (MVC)
- Model-view-presenter (MVP)
- Model-view-viewmodel(MVVM)

**Application Structure Patterns => User Interface Patterns => Decide which Application Landscape Patterns to use**



