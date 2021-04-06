# Micro-service Cross Cutting Concerns

## Problem

When a team develops a micro-service, there is a large body of contextual work that is necessary for creating a well-engineered and supportable service, but that is independent of the core of the service. For most services, this work is almost identical from service to service and represents a considerable portion of the overall work deploying a new service — sometimes as much as 75% of the effort involved. If we want to start speeding our development cycles and deploying new services quickly, we need to reduce this cost dramatically and allow our teams to focus on the core IP of our business.

## Potential Solution

One pattern for reducing the cost to the business is to develop a “Micro-services Chassis” (http://microservices.io/patterns/microservice-chassis.html) - a framework of reusable templates and components that can be used as libraries by service teams, but maintained by a single team. 

By having a single team become responsible for the maintenance of the cross cutting concerns, the overall cost of new service development is reduced dramatically. Additionally this gives the business common control points across services where we can enforce standards such as security, particular productivity or quality tooling, or operational standards.

Examples of cross cutting concerns:

* Infrastructure (IaaS) Resource Templates (ie. Terraform modules for AWS resources)
* Security Configuration (ie. VPC, Subnets, IAM, & SecurityGroups)
* Orchestration (ie. Kubernetes deployment & configuration)
* Configuration & Secrets Management
* Logging & Monitoring hookups
* Common Application Framework base configuration (ie. Scone or DropWizard)

As the set of cross cutting concerns grows there might be more added - API Gateways registration, ServiceMesh Interaction, CircuitBreakers, MessageBus access, etc. — effectively anything that would transcend a particular service, but be utilized by many services. 

## Avoiding the Dependency Pitfall

By assigning ownership to a team and a technical leader early, that team can start to define the components and architecture that will be used for the future. Once that vision is in place, teams can start to follow the plans defined by the 'chassis' team in order to contribute their work for the good of the whole division. By establishing the contribution and acceptance process up front, the long term responsible team can feel more ownership of the contributions and the teams under deadlines are enabled to move forward without taking a dependency on another team. 


