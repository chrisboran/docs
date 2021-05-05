# Bounded Context Overview Template

## Bounded Context Charter

Please type a brief description of your Bounded Context - please keep it brief but include the criteria by which you define what is in bounds and what is out of bounds for your context - the way that we will decide if new functionality lives in your context. This should be brief and easy to explain in a 5 minute conversation, and clear to all members of your team.

![Sample Bounded Context Dependency Map](SampleBCDMap.png)
## Ubiquitous Language of the Bounded Context

* Term A: definition
* ***Term B: Stars on the term indicate that this is a candidate for elevation to the Ubiquitous Language of entire group, not just this context 
* ...
* Term N: definition

## <Domain Name 1..N>

Please type a brief description of each of the domains contained within your Bounded Context. Most Bounded Contexts will have one Core Domain and several related Domains. You may have a couple of core domains depending on how you break things up. For each Domain, list the Core Domains first, and provide a brief description including what responsibilities lay inside the domain, and which are outside - and what criteria by which to make a decision

### Inbound Domain Dependencies 

* Listens for Event A from Domain X because...
* Listens for Event B from Bounded Context Y because....

### Outbound Domain Dependencies

* Sends Event B to Domain Y to because...
* Calls API C on Domain Z to because...

### Events Produced

* Event A is sent when X occurs...
* Event B is sent when Y occurs...

### Aggregate List

* Root Aggregate
    * Key Attribute 1 w/ explanation
    * Key Attribute ...
    * Key Attribute N
    * Key Action 1 w/ explanation
    * Key Action ...
    * Key Action N
* Aggregate 2
* ...
* Aggregate N

## Issues Needing Attention!!!

In this section please detail decisions that the team has come to that they feel are important to surface that SOMEONE owns, but we do not feel belongs in this bounded context. Ideally we should already have sought out who we think should own it and achieved an agreed handoff. If that hasn't happened, please surface it here ASAP. This should include responsibilities / functionality that are tangential to your Bounded Context, but might not be agreed to, as well as potential cross cutting concerns that you have identified.


