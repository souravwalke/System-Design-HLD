**What is a Monolithic Architecture?**

Monolith Design refers to a traditional software architecture where the entire application is built as a single, unified codebase which handles multiple responsibilities within a single process or deployment.

Characteristics of Monolithic Design:

- Single Codebase: All components (e.g., authentication, payment, notifications) are part of the same application.
- The entire application is deployed as one unit.
- All application parts are interdependent, meaning changes to one module often require changes to others.

----------------------------------------------------------------------------------------------------------------------------------------

**What are the advantages and disadvantages of using a Monolithic Architecture?**

Advantages:
- Simplicity in Development: It is easier to build initially, especially for small teams.
- Easier Testing: Only one application to test.
- Simplified Deployment: Deploying the whole application at once avoids integration complexities.

Disadvantages:
- Difficult to scale individual components independently.
- As the codebase grows, making changes becomes complex and error-prone.
- Even minor changes require redeploying the entire application, increasing downtime.
- It is hard to adopt new technologies for specific parts of the system.
- Working as a team on such a codebase creates a lot of conflicts and unforeseen errors.

----------------------------------------------------------------------------------------------------------------------------------------

**What is a Microservices Architecture?**

Microservices Design is an architectural style where an application is structured as a collection of small, autonomous services, each focusing on a specific business capability. These services are loosely coupled, independently deployable, and communicate with each other through lightweight mechanisms like APIs or message queues.

Characteristics of Microservices Design:

- Each service represents a single business function.
- Services can be developed, deployed, and scaled independently without affecting others.
- Each service can use its own technology stack, database, or language based on specific needs.
- Failures in one service don’t necessarily bring down the whole system.
