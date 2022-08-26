## Microservice Design pattern & architecture
Reference from https://www.linkedin.com/learning/software-architecture-patterns-for-developers/event-sourcing?autoSkip=true&autoplay=true&resume=false&u=2276065
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
 - FaaS or Function as a Service is a platform that lets you run self-contained functions (code snippets) in the cloud.It Helps developers in creating or updating codes on the fly that could be executed with any interaction with its element on the page.

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
![image](https://user-images.githubusercontent.com/56182367/186834080-fd3bcf50-4623-4d2b-a938-b296603242af.png)


#### How Do We design these individual applications?
Ans: **Application Structure Patterns**

**Application Structure Patterns**are a category of patterns that defines how a single executable should be built.It is about the structure of a single exectuable and it can be part of a large application landscape.

**Application Structure Patterns:**

- **Layered:**
  **Advanatages:**
  - Well known among developers
  - Easy to organize
  
  **Disadvantages:**
  - Can lead to monolithic applications that makes it hard to maintain
  - Need to write lots of coede
  - Because it is separate layer, it can be difficult to take a specific business functionality and split it off into a new application.
  
  **Example:**<br>
  ![image](https://user-images.githubusercontent.com/56182367/186835161-4c7e5d2b-d93d-4234-a601-38ace9b022e3.png)

- **Microkernel:** It's also called the plugin pattern.The application consist of a piece of core logic that can be extended to plugins. The core defines the contracts that the extension need to adhere(believe in and follow the practices of) but other than that, the core doesnt need to know much about the extensions.
- Great use cases are Task Scheduler, Workflow, Data processing applications, browser extension, plugin for graphic design applications.

  **Advanatages:**
  - Great flexibility (Don't need to know the required features upfront because it can be added as extension later)
  - Clean separation from the core logic
  - Separate teams at their own pace and own style
  - Add and remove functionality at runtime (don't need to restart the core)
  
  **Disadvantages:**
  - Core API might not fit future plugins
  - Can the plugins be trusted? (the core must also trust the extension but it is possible that the plugin destroy the entire application)
  - Not always clear what belongs in the core and what belongs to the extension.


![image](https://user-images.githubusercontent.com/56182367/186848106-77e730c9-16be-4fea-94f8-41d094c66b3d.png)

**Example:**<br>
![image](https://user-images.githubusercontent.com/56182367/186848248-1ba590bb-dbd5-452d-9fb3-688959ab9247.png)
![image](https://user-images.githubusercontent.com/56182367/186848352-27bea782-41a1-4dac-b75d-ed7704677781.png)

- **Command Query Responsibility Segregation (CQRS):** Is a pattern that has two entirely separate models.It allows for scenario-specific queries that could improve performance and reduce the amount of complex queries you have. It could even have separate database for your queries.However it requires us to synchronize the tables or database. It is often implement together with event sourcing.
  - Two Models: 
      - Read/query
      - Write/command
![image](https://user-images.githubusercontent.com/56182367/186854115-28b48839-06c0-42b5-be62-1aeffd46ede8.png)
  **Advanatages:**
  - Simpler Queries (eg: less join statement)
  - Faster and more scalable read queries
  - Easier to communicate with stakeholders
  
  **Disadvantages:**
  - Added complexity
  - Learning curve 
  - Possiblity of data inconsistencies (May have small delay between the read database & the write database)
  - Eventual consistency. (The database will be insync but not immediately. Eg: UI might not be updated immediately after the user made changes)

**Example:**<br>
![image](https://user-images.githubusercontent.com/56182367/186855325-5d0a4ad5-02c2-42b5-9d41-fc798e111ca7.png)
![image](https://user-images.githubusercontent.com/56182367/186856334-87f08b21-e4b9-454a-8035-45382523aa2c.png)

- **Event Sourcing:**
  The Event Sourcing pattern defines an approach to handling operations on data that's driven by a sequence of events, each of which is recorded in an append-only store. Application code sends a series of events that imperatively describe each action that has occurred on the data to the event store, where they're persisted. Each event represents a set of changes to the data (such as AddedItemToOrder).
  
  **Advanatages:**
  - Trace of events
  - Audit trail
  - Business language (able to communicate with stakeholders)
  - Event replay (if there's a bug in the handling of an event which leads to wrong state of an entity, we can simply fix the bug in the event handler. & next time we replay the events, our entity, it will be in the correct state, dont need to manually fix the data in the database)

  **Disadvantages:**
  - Replay and external systems (if the events leads to update in external system, it could lead to an issue in external systems,so should be aware that replaying the events,could lead to issues in those systems. **Need to know whether is a new event or just part of a replay** ) 
  - Event Structure changes (changes to the code of events or event handlers can be tricky.Eg: Renaming a property, the code needs a way of handling this correctly because the events stored in the database will still using the old property name)
  - When have large amount of events that takes some time to replay, it can make the application slow to load new objects from the database (Solution of this issue will be using Snapshots)
  - Learning curve. (many developer are unfamilar with this architecture
  ![image](https://user-images.githubusercontent.com/56182367/186869561-b17af467-1a96-48a4-bec7-fa4d69ccf331.png)

- **Command Query Responsibility Segregation & event sourcing combined:**
  Combining CQRS & Event-sourcing pattern
  ![image](https://user-images.githubusercontent.com/56182367/186866656-2e028687-ef25-48bf-874c-a3379037d3ad.png)

   **Advanatages:**
  - Simpler & faster queries (involves much less complex queries than without CQRS)
  - Scalable (The event source in part give u trace of events that happed in the system)
  - Trace of events
  - Provide Audit trail
  - Business langauge. (easier to write code using the language that the end user speaks, they speaks in terms of commands & events)
  
  **Disadvantages:**
  - Added complexity (more components that interact with each other)
  - Learning curve (slightly more difficult to learn)
  - Data inconsistencies (because of CQRS pattern, read model can become out of sync)
  - Event structure changes (eg: renaming a property, the code needs a way of handling this correctly because the events stored in the database will still using the old property name)

**Why to use CQRS &/ Or Event Sourcing?**
<br> Ans:
- Not for simple domains.
- You can start with event sourcing without CQRS
- Add CQRS later
(Because it is much harder to add Event Sourcing to the traditional system as compared to adding CQRS to an event sourcing system)

### User Interface pattern (getting into details of how the user interacts with the application)
- Model-view-controller (MVC)
- Model-view-presenter (MVP)
- Model-view-viewmodel(MVVM)

**Application Structure Patterns => User Interface Patterns => Decide which Application Landscape Patterns to use**



