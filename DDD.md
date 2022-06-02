# Building Microservices Notes from Training

## Glossary
* Bounded Context
* BFF: Backend for Frontend (Makes so FE does not directly call BE); API gateway or Service Layer with stable API.

## Domain logic patterns

Patterns of Enterprise Application Architecture
Martin Fowler et al

* Transaction script
* Domain model (ObjOriented)
* Table module
* Serverless approach

## Backend for frontend

## Data access patterns

* ORMs
* Document databases: Whole document operations. Limited support for joins.
* CQRS: Command query responsibility Segregation.  Separate read and update models.
* Event Sourcing: Store state changes as events. Eventual Consistency.

## Microservice Code Responsibilities

* Handle Incoming Requests (HTTP or Messages)
* Domain Logic (Business Rules, e.g. Sales Tax)
* Data Access
* Integrate with other services (pulishing, third party)

#Dangers to Avoid

* Duplicating business logic across multiple microservices
* Giving too many responsibilities to a single microservice
* Too much chatty communication between microservices
