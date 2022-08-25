## Microservice Design pattern & architecture
### What is the difference between Design Architecture & Design Pattern
Differences between design and architecture patterns reflect their different uses. Architecture represents scaffolding, the frameworks that everything else sits upon. Design patterns represent a way to structure classes to solve common problems.

**Architecture Patterns** cocurs at higher level, no longer look at small piece of application but what defines the application.

**Design Pattern** dont tell us how the application should build, it only tell us what a specfic piece of code must do & what other piece of code should interact with it.
<br>
![image](https://user-images.githubusercontent.com/56182367/186626222-eb0cdf76-5db9-41a0-83bc-abba4b9926ca.png)

### Type Of Application Landscape Patterns
- Monolith: <br>Monolithic application describes a single-tiered software application in which the user interface and data access code are combined into a single program from a single platform. A monolithic application is self-contained and independent from other computing applications
<br>**Advantages**:
  - Easy to understand, implement & test
  - Easy Deployment
  - Ideal for limited Scope


  **Disadvantage**: (As application starts to grow)
  - Tight Coupling (Making it harder to move pieces of logic to other applications later
  - Easily leads to complex code (developer find it hard to modify or extend the application)
  - Can leads to **One size fits all for every subdomain**

- N-tier


- Service-oriented


- Microservices


- Serverless


- Peer-to-peer

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



