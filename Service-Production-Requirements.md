# Service Production Requirements

As we continue to become more distributed it is important to set some ground rules for how we look at Service Ownership in order to ensure that we uphold Customer Trust. Our customers have high expectations related to latency, response times, persistence, and throughput guarantees. They also expect that when a problem arrives that we are able to recover as quickly as possible. This all is part of the Trust our customers have in our platform.

To live up to these expectations we must ensure that as we take dependencies our overall experience when using our platform offering does not degrade.  We MUST also understand that we have just as much to gain (or lose) due to the performance characteristics of our platform - we share our customers successes.

The format of this document is designed to give an indication of requirements in [Moscow Method](https://en.wikipedia.org/wiki/MoSCoW_method) (Must, Should, Could, Won’t) to make it clear to teams how to prioritize their investments. In order to help teams self-determine progress in preparing to launch a new service as customer GA ready, we have prepared a *Service Production-Readiness Self Assessment* to help remind them of what the critical things that they should be thinking about are. The assessment is built against these requirements and should be performed at least annually, and an up-to-date copy should be linked from their service documentation for external visibility. 

## Tiers of Service

We propose 3 “Tiers” of service that each may have different requirements based on the criticality they have to the business. A service for our purposes is any cohesive system of components owned and operated by a single team that work together to deliver a value to the business - the important part that we are measuring here is the contract that the service makes with the business. That is to say the internal components of your service need not be classified, just the cohesive service.

**Tier 0 (T0) Services** are the most critical to our system. A service is considered Tier 0 if:

* it goes down it disrupts the functioning of the core pieces of functionality for the business
* if its latency degrades, customers would be unable to perform core operations of the system
* it goes down our ability to successfully bring the system back to a stable condition would be delayed by more than 15 minutes
* it goes down your Sr. Director is likely to be engaged within 30 minutes

*Examples:  {}

**Tier 1 (T1) Services** are defined as all services that do not meet Tier 0 criteria, but exist within the flow of *any* customer interaction. Or whose outage may have an adverse effect on customer operations 

* any customer facing functionality where the customer would perceive the degradation

*Examples: {}

**Tier 2 (T2) Services** are defined as all other services that are not Tier 0 or Tier 1. Most frequently these are internal services that are used for actions such as data mining, analytics, etc. Such systems could generally be down for 12 or more hours without any impact to our business

* any service that could successfully be down for multiple hours without a customer preceving a change to their level of service

*Examples: {}

# Cross Cutting Service Requirements

These requirements are used to evaluate the ‘readiness’ of all services. Individual teams should decide for themselves when they are Pilot, Closed Beta, Open Beta, and GA ready when viewed through the level of risk associated with not satisfying any of these requirements **but** they must make these risk decisions transparent both to management and to anyone who may take a dependency on their service.

## Code Quality

* All services **must** make use of automated quality and security [static analysis](https://searchwindevelopment.techtarget.com/definition/static-analysis) tools on their codebase
* All 3rd party artifacts **must** be scanned using a security approved tool (for example sonatype). 
* All services **should** require at least 2 reviewers other than the author to approve a pull request
    * At least one reviewer **must** be from the service team
    * All services **should** have a documented team checklist and procedure for ensuring quality of reviews 
* All services **should** using automated [lint checking](https://en.wikipedia.org/wiki/Lint_(software))tools in an effort to improve the base quality of their code
* All services **must** use automated unit tests and obtain a minimum code coverage of 80%

## Service Quality

* All services **must** perform clear-box style [integration testing](http://softwaretestingfundamentals.com/integration-testing/) in a production-like staging environment (with production controls etc applied)
    * All T0/T1 services **must** provide API access in this staging environment to its dependent services
* All services **must** provide a versioned interface that supports at least one version back
    * All services **should** use [Semantic Versioning](https://semver.org/)
    * All T0/T1 services **must** provide no less than 6 months of backwards compatible interfaces (except in the case of Trust P0-P1-P2 required changes), which should be tested in your integration testing phase before ever reaching a shared production-like staging environment

* All services **should** perform opaque-box style [end-to-end](https://www.softwaretestinghelp.com/what-is-end-to-end-testing/) testing in a production-like staging environment
* All services **should** provide a formal versioned contract for their service 
    * All T0/T1 services **must** provide such a contract and test to ensure it every release
* All services **should** provide local testing mocks for other teams to use in their local development
* All services **should** use [synthetic tests](https://dzone.com/articles/what-is-synthetic-testing-a-definition-and-how-it) in production to continuously validate their functionality
    * All T0/T1 services **must** perform synthetic testing in production

## High Availability

* All services **must** document [failure modes](https://support.minitab.com/en-us/minitab/18/help-and-how-to/modeling-statistics/reliability/supporting-topics/basics/what-is-a-failure-mode/) and explicitly test system behavior under those conditions 
* All services **should** proactively deploy means of Service Protection (ie Rate Limiting, Load Shedding, etc.) 
    * All T0 services **must** proactively deploy means of Service Protection (ie Rate Limiting, Load Shedding, etc.) 
* All services **should** proactively protect itself from outages in downstream dependent services by employing techniques such as Circuit Breaking
* All services **should** design to run across 3 availability zones in a public cloud substrate 
* All services **must** document all dependencies and have tested to ensure they have a mitigation plan for when these dependencies suffer performance degradations or outages
* All services **must** document and report on their own [SLOs](https://en.wikipedia.org/wiki/Service-level_objective) (internal) and [SLAs](https://en.wikipedia.org/wiki/Service-level_agreement) (external)
    * All T0 services **must** target an SLA minimum of 99.99% non-degraded performance availability
    * All T1 services **must** target an SLA minimum of 99.9% non-degraded performance availability
    * All T2 service **must** target an SLA of minimum of 99.5% non-degraded performance availability
* All services **must** supply a highly available staging environment for others to test against, which is treated as c, with a defined SLO and SLA that dependents can rely on
    * All T0/T1 services **must** target an SLA of 99.9% availability, but performance could degrade while tests are running against the staging environment
* All services **should** perform [chaos testing](https://boyter.org/2016/07/chaos-testing-engineering/) in a production-like staging environment to ensure your service can survive outages 
    * All T0 services **must** perform [chaos testing](https://boyter.org/2016/07/chaos-testing-engineering/) in a production-like staging environment to ensure your service can survive outages 
* All services **could** automate their chaos tests under low grade load in a production-like staging environment in order to continuously test for availability

## Performance Assurance

* All T0/T1 services **must** define a target P50 and P95 response times for each service access point they offer (ie. each API Endpoint) and test to prove them
* All services **must** perform baseline [load testing](https://www.testingperformance.org/definitions/what-is-load-testing) in a production-like staging environment to simulate load from many sources at the same time
* All services **must** perform [stress testing](https://www.geeksforgeeks.org/stress-testing-software-testing/) in a production-like staging environment to simulate burst traffic
* All services **must** perform [soak testing](https://www.katalon.com/resources-center/blog/soak-testing/) over an extended period of time in a production-like staging environment to catch slow-building issues
* All services **must** perform automated performance regression testing.
    * All services **should** run their performance regression as part of their CI/CD pipelines.
* All services **should** alert when performance deviates from normal thresholds to create visibility into real user performance in production and staging for the service team
* All services **could** automate performance tests to run against a production-like environment in order to continuously test their performance 

## Scale Assurance

* All services **must** document their dominating scale factors (IO, cpu, memory, etc) and design testing plans according to these bottlenecks - both vertical (bigger machines) and horizontal (more machines) scale factors
* All services **must** define and test their throughput capacity limits
* All Services **should** have hard service-level rate limits documented and enforced
    * All T0/T1 Services **must** have hard service-level rate limits documented, tested, and enforced
    * All T0/T1 Services **must** have soft per-tenant rate limits documented, tested, and enforced
* All services **must** define [SLIs](https://en.wikipedia.org/wiki/Service_level_indicator) that are leading indicators of needing to take a scaling action and they must be proven via testing 
* All services **must** have a defined plan of how the service will scale when SLIs have been approached/surpassed
* All services **must** have some means (manual permitted) of triggering scale actions as they approach their SLI limits
    * All services **should** automate their scale actions to a point where they could use their well understood signals in order to build true autoscaling
* All services **must** **** perform [capacity testing](https://www.apicasystems.com/blog/load-testing-vs-stress-testing-vs-capacity-testing/) in a production-like staging environment to ensure that their SLIs and mitigation plans function as expected

## Deployment Quality

* All services **must** build immutable artifacts for deployment - code, infrastructure and configuration
* All services **should** aim to make deployments small and frequent to limit the surface area of change
* All services **must** prevent artifacts that have failed a test in the pipeline from being deployed into a production environment
* All services **must** ensure that all production change is initiated from pipelines
* All services **must** deploy and test in a production-like staging environment prior to a change being permitted into production
* All service **must** provide a basic health checking endpoint to be used to assess [base service health](https://microservices.io/patterns/observability/health-check-api.html) post deployment in addition to any infrastructure health checking they may do 
* All services **should** attempt to maintain the minimum parity gap they can between their different deployment environments (dev, staging and production)
* All services **must** clearly document which Compliances they are in scope of (ie SOX, SOC2, PCI) 
* All services **must** use standard company audit records to release new versions of their software in order to enable reporting for Compliance (for traceability of changes)
* All services **must** maintain in their service documentation a copy of their deployment pipeline design
* All services **must** onboard with the standard Change Management Process and use auditable change logs
* All services **must** have a documented and audited formal process for approving deployments into production environments to achieve Compliance requirements of having at least 2 individuals involved in approving any change making it to production (Separation of Duties) 
* All services **must** respect posted change windows for their product if their deployments could have potential to disrupt customer service.
* All T0/T1 services **must** respect the moratoriums and exception processes of all services that depend on them (e.g. thanksgiving holiday). 
* All services **must** define and implement a rollout strategy that appropriately manages the blast radius of a mistake at each stage of deployment, and have reviewed worst case scenarios with their management team
    * All T0/T1 services **must** have a [canary deployment strategy](https://martinfowler.com/bliki/CanaryRelease.html) - there can be no grid-wide pushes
    * All T0/T1 services **must** limit the blast radius of any step in their deployment process to not more than 10% of the production tenants 
    * All T0/T1 services **must** have a defined process by which they verify the success of each step in their canary process before proceeding with the next step
* All services **must** have a fast mitigation plan (sub-30min) for rollback of the most recent change to production
* All services **must** provide a fast (sub-30min) roll-forward mitigation plan for remediating problems in production that cannot be rolled back easily
* All services **must** perform a post-deployment automated [smoke-test](http://thethinkingtester.blogspot.com/2018/11/what-to-put-in-smoke-test.html) in all environments

## Observability

* All services **must** monitor the [READS](https://engineering.salesforce.com/reads-service-health-metrics-1bfa99033adc/) metrics: **R**equest Rate, **E**rror Rate, **A**vailability, **D**uration (Latency) and **S**aturation of your SLIs
    * All T0/T1 services **must** actively review their performance monitoring in order to understand normal operations 
* All services **must** issue alerts as it approaches thresholds in all SLIs and when the service is over SLA
    * All T0/T1 services **must** issue alerts against production-like staging environments to provide production-like support for the staging environment
* All services **must** provide sufficient documentation around normal state of all SLIs 
* All services **must** have easy to access logs for service owners, security, and SRE
* All services **must** emit service level metrics and not rely solely on infrastructure level metrics that are accessible for service owners, support, and SRE
* All services **should** provide a mechanism to accept/forward request IDs included in log lines (and possibly other metrics) to facilitate distributed tracing
* All services **could** use structured logging to emit key metrics on a per-request basis 
* All services **must** provide custom dashboards reflecting their service metrics for stakeholders to consume using the well-known supported toolchains
    * All T0/T1 services **must** provide a health overview dashboard visible to all stakeholders (support, SRE, dependent services) for both production and staging environments
* All services **must** **** feed logging and monitoring data to a supported toolchain in order to engage stakeholders outside the team
* All services **could** use augmentative tooling within their service team to get deeper insights
* All services **must** be able to debug in a production-like staging environment without the use of a debugger to prove the observability of their system
* All T0/T1 services **must** publish a quarterly scorecard that provides transparent visibility to:
    * [READS](https://engineering.salesforce.com/reads-service-health-metrics-1bfa99033adc/) metrics: **R**equest Rate, **E**rror Rate, **A**vailability, **D**uration (Latency) and **S**aturation of your SLIs
    * Achieved Performance SLIs compared to defined
    * VOC quotes from within the quarter
    * PRBs and assessments for any SEV1 or higher outages
    * Cost Model vs Actual Costs

## Operations

* All services **must** maintain an up to date record in the Service Catalog
* All services **must** place their design documentation in a common location linked from their Service Catalog Record where others can discover and access it, and must be comprehensive enough for a peer engineer to read and understand the data flows and processes of the service
* All services **must** proactively create run-books for every alert they generate so that the individual receiving an alert has a clear plan of action to minimize customer impact
* All services **must** have a clear plan for how they enable SRE for incident responses and onboard accordingly
* All services **must** define an on-call rotation for emergency support
* All services **must** have a clear 24/7 support plan with an SLA response time for requests for engineering support during Sev0/Sev1 events
    * All T0 services **must** target an SLA of less than 15 minutes for response
    * All T1 services **must** target an SLA of less than 30 minutes for response
* All services **must** have a documented escalation path into management for engineering support requests
    * All T0 services **must** have a clear escalation to the engineering Sr Director or above if an incident exceeds 30 minutes in duration
    * All T1 services **must** have a clear escalation to the engineering Sr Director or above if an incident exceeds 60 minutes in duration
* All T0/T1 services **should** proactively alert the service owning team for visibility even when SRE can handle the incident on their own
* All services **should** have a clear plan for how they onboard with SRE for monitoring and basic response, including enablement training and documentation
* All services **should** conduct [“Game Day”](https://dzone.com/articles/focus-on-readiness-its-a-good-day-for-a-game-day) style exercises in order to validate their observability and documentation

## Security

Here we attempt to summarize the cross-cutting security requirements in order to assist early in a service design phase - these requirements guide but do not replace performing formal security assessments and threat models

### Base Security Best Practices

All services **must** adhere to relevant standard Security Policies
**Detailed resources**

* Apply Defense in Depth
* Use Least Privilege
* Use Secure Defaults
* Minimize Attack Surface

* Use a Positive Security Model
* Fail Securely
* Make Security Usable
* Protect Customer Data

**External Standards and Compliance**
All services **must** adhere to relevant compliance for the scope of their service (ie GDPR, SOC, SOX, PCI, etc.)

### Security Requirements

The following is a list of security requirements, grouped by security control type, that we feel are of particular interest to service owners. It is **not** intended that these are the only security requirements, just a list of common ones that we feel it is of particular interest to highlight because of the effects they can have on the design of your service.


* Account Management and Identity Management (Authentication & Authorization)
    * All services **must** enforce some approved form of explicit identity-based Authentication
    * All services **must** enforce some approved form of explicit identity-based Authorization
* Network Security
    * All services **must** encrypt all data in transit and whitelist accessing inbound connections where possible
    * All services **could** encrypt data client side before serializing to the network (payload level encryption)
* Data and Storage Security
    * All services **must** encrypt all data at rest
    * All services **could** encrypt data client side before serializing to storage 
* Secrets, Key Management and PKI certificates
    * All services **must** store all secret material (ie keys, credentials, certificates) in an approved
    * All services **must not** check secrets into source control
* Logging and Monitoring
    * All services **must** retain a trail to the requesting user when performing an action on behalf of a user
    * [OWASP Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)
    * All services **must** follow [PII management best practices](https://medium.com/@joecrobak/seven-best-practices-for-keeping-sensitive-data-out-of-logs-3d7bbd12904)
* Security Assurance and Secure SW Development Lifecycle
    * All services **must** maintain an up to date [Threat Model](http://www.agilemodeling.com/artifacts/securityThreatModel.htm) 
    * All services **should** work with the security organization to ensure proper [penetration testing](https://searchsecurity.techtarget.com/definition/penetration-testing) is performed at a regular cadence
    * All services **must** include in their documentation set a link to their Security Assessment
    * All service **must** document and classify all of the data they handle and store for security risk assessment
    * All service **must** be covered with automated vulnerability scanning, and **must** adhere to security SLAs
        * If not, appropriate GRC extensions should be in place.
* Operational Security and Build Infrastructure
    * All services **must** maintain an immutable audit trail of changes applied both to the codebase and to production
        * This audit trail **must** include detailed information about what is being changed, when and by whom
    * All services **must** have a defined, documented, and audited process for updating 3rd party dependencies to their latest levels 
        * All services **should** *proactively* update their 3rd party dependencies once per release cycle to reduce risks
        

## Disaster Recovery

* All services **must** enumerate and classify the kinds of disaster they will commit to solving
* All services **must** have a documented and tested disaster recovery plan on a regular cadence (minimum annually)
* All services **must** document and adhere to [RTOs and RPOs](https://phoenixnap.com/blog/rto-vs-rpo-differences) 
* All services **must** consider the effects of regional data residency restrictions on their DR plans
* All services **must not** assume that multiple availability zones (AZs) are an effective DR plan

## Capacity Planning

* All services **must** produce and keep current an Operational Cost Model for their service and a 1 year projection that is up to date
* All services **must** monitor usage growth and plan accordingly for more cells/regions/etc
* All services **must** report and review their actual costs monthly and ensure they are appropriately prioritizing cost-to-serve for their service against other concerns
* All services **should** prepare a forecast of needed resources during Holiday Peak period (Nov 1 - Jan 2) to ensure that capacity needs can be planned for and met


* * *

# FAQs

### service vs dependency Requirements?

Ultimately meeting all requirements are the accountability of the team implementing a solution.  While a team may take a dependency; that does NOT relinquish them from the accountability of meeting (and measuring) their achievement of requirements.

Ultimately the requirements we place on a dependency will be given to the Service Owner on which another team wants to depend; however, it is the style of dependency that is important.  This might be best seen through an example:

* Presume we want to create an API the provides the quantity of inventory that is available to sell.  The API is built with a stated SLA that the inventory quantity returned is heavily cached and consistent within 30 minutes.  There are two potential implementations:
    * On every request we call a dependency on another service to determine the quantity.  If that service cannot be reached we return a **503: Service Unavailable.** 
    * One every request we call into a cache and return the quantity from the in memory cache.  In the background every 5 minutes we refresh the cache of information.  While the service is down we would be notified after 5 minutes and there remains 25 minutes to attempt to work around the problem.  After a full 25 minutes of outage our API continues to return the cached value BUT adds a state of “stale” to the response.

In the above situation the design of the first solution would make the dependency requirements Tier 0 requirements as it is likely our team and Sr. Director will quickly be called.  When we assess if we want to take a dependency on a given service we would use the Tier 0 requirements.  In the 2nd implementation the API continues to function.  While a consumer experience might be degraded there is no impact on the ability to process an order for this API interaction and it will be more than 30 minutes from when the outage begins until a Sr. Director would be paged.  As a result we can look at dependencies that meet the slightly more lenient Tier 1 criteria.

In time we feel that Services should categorize themselves as meeting Tier 0, 1, or 2 requirements to make it easier to identify and take dependencies as this creates an explicit understanding of contract; however, it is ultimately up to the team building a given interaction to properly assess and communicate the requirements necessary for their system to meet our High Availability Standards.

### What are Availability, SLA, and SLO defined?

A **service-level agreement** (**SLA**) is a commitment between a service provider and a client. Particular aspects of the service – quality, availability, responsibilities – are agreed between the service provider and the service user.

A **service-level objective** (**SLO**) is a key element of a [service-level agreement](https://en.wikipedia.org/wiki/Service-level_agreement) (SLA) between a [service provider](https://en.wikipedia.org/wiki/Service_provider) and a [customer](https://en.wikipedia.org/wiki/Customer). SLOs are agreed upon as a means of measuring the performance of the Service Provider and are outlined as a way of avoiding disputes between the two parties based on misunderstanding.

**Availability** is defined internally as our system responding within specifications.  *Note: this can be different from our contractual requirements as defined by our MSA.*  Any time spent outside out a services defined specifications would be consider as the service not being available.  For example, an API Endpoint defined to handle 1000 requests per second with a P95 response time of 100ms would be UNAVAILABLE if the trailing 5 minutes P95 response time was above 100ms.  This service would also be UNAVAILABLE if the trailing 5 minutes requests to serve responded with unexpected ERRORs before hitting 1000 requests per second.

The following is a chart lists the allowed downtime of a service given different targets:

|Availability %	|Downtime per year	|Downtime per month	|Downtime per week	|Downtime per day	|
|---	|---	|---	|---	|---	|
|97%	|10.96 days	|21.92 hours	|5.04 hours	|43.20 minutes	|
|---	|---	|---	|---	|---	|
|98%	|7.31 days	|14.61 hours	|3.36 hours	|28.80 minutes	|
|99% ("two nines")	|3.65 days	|7.31 hours	|1.68 hours	|14.40 minutes	|
|99.5% ("two nines five")	|1.83 days	|3.65 hours	|50.40 minutes	|7.20 minutes	|
|99.80%	|17.53 hours	|87.66 minutes	|20.16 minutes	|2.88 minutes	|
|99.9% ("three nines")	|8.77 hours	|43.83 minutes	|10.08 minutes	|1.44 minutes	|
|99.99% ("four nines")	|52.60 minutes	|4.38 minutes	|1.01 minutes	|8.64 seconds	|
|99.999% ("five nines")	|5.26 minutes	|26.30 seconds	|6.05 seconds	|864.00** **[milliseconds](https://en.wikipedia.org/wiki/Millisecond)	|
|99.9999% ("six nines")	|31.56 seconds	|2.63 seconds	|604.80 milliseconds	|86.40 milliseconds	|

### How do we calculate availability with cascading dependencies

TODO: Joint Probabilities 
TODO: Cascading dependencies as an anti-pattern and what to do instead
