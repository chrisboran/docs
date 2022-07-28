# On Designing & Deploying Internet Scale Service 
by James Hamilton
## Reading Notes

## Top Line Outcomes
1. Deliver operations-friendly services quickly
2. 2. Avoid early morning phone calls and meetings with unhappy customers that non-operations-friendly services tend to yeild

Data from paper collected from learnings by Microsoft team: Windows Live, Microsoft Exchange, MSN Spaces, XBox Live, Rackable Systems Engineering, Messenger Ops and Global Foundation Services

## Guiding Principles
1. Expect failures - always everywhere. Handle all failures gracefully
2. Keep it simple - complex systems fail more frequently in harder ways to fix and avoid. Simple systems are easy to get right. Reduce dependencies rigorously.
3. Automate Everything - people make mistakes - unavoidable. Automate all things a human might fat finger - even verifications.

## Recommendations
* Design for operationalizing not for features 
* Tight alignment in the dev->test->ops cycles are critical

* **Design for failures** - at scale everything fails constantly - human intervention cannot be required to recover from failures cost effectively 
* **Redeundancy** - SLAs must assume that you can crash systems and still have the overall service meet SLA. Use a threat-modeling like process to do failure mode analysis. Document all failure modes and plan for the contingencies explicitly
* **Unreliabile Infrastructure** - assume all of the infra can and will fail
* **Single-Version Software** - same software, many regions & environments. Do not snowflake
* **Multi-tenancy Only** - cattle not pets, we need to be able to move customer workloads across servers, not tie an anchor around a cusomer
* **Fast Health Checks** - must be *fast* and only test the elements critical to ensure this service is operational, not its dependencies 
* **Realistic Dev (Integration) Environment** - must be reasonable facsimilie of production - as close as you can get
* **No Trust of underlying services** - assume all networked attached resources will fail and your service should continue to function in degraded mode if possible
* **DRY** - parallel code in microservices is VERY hard to coordinate fixing - don't try to do it
* **Pod / Cluster Isolation** - pods & clusters should not be able to impact each other 
* **Avoid Human intervention** - should be a rare exception and not a SOP - the system should operate itself but you must leave a break-the-glass procedure for emergencies
* **Premature Optimization is the root of all evil** - do the simple things well and fault tolerantly. Optimize only when absolutely necessary - optimizations tend to breed compliexity which is a killer
* **Leverage Admission Control** - use proactive service protections (rate limiting, load shedding, etc) rather than trying to soak the load
* **Partition to decrease plast radius** - decide on a partition size and create pools of isolation to avoid complete system failures
* **Understand Your Network** - networks matter in distributed systems and can't be ignored
* **Throughput and Latency Observability** - being 'up' isn't enough, you need to track the customer's experience 
* **Operations Utilities are Part of your service** - operations isn't an after thought, its a critical part of your service and should be treated like it using the same code-safety processes
* **Understand Access Patterns** - analyze proposed data flows BEFORE building anything. Understand what impact the new features will have on the existing systems
* **Version Everything** - production in a large company is chaotic. Versioning helps you understand what you are really seeing and gives you tools to automate activities more easily in a mixed version environment
* **Run Test Sensors Against Production** - regressions can pop up outside the deployment pipelines (which you should ALWAYS have) - run test probes in production to catch end-2-end errors more rapidly - know before the customers do
* **Avoid Single Points of Failure** - track your points of concentration where the blast radius of a failure is large and work to eliminate/mitigate those agressively

## Automation Best Practices
* **Restartable & Redundant** - workloads should be reentrant and state stores redundant 
* **Redunant-Distributed** - spread services across multiple failure zones
* **Provision Fast** - all installation and provisioning should be automated and fast to scale-out new instances
* **Configuration and code as testable units** - both should be tested together and deployed together as a unit
* **Cattle not Pets** - we should know the role of a server not its instance
* **Multi-system failures** - expect one failure to lead to cascades
* **Recover services not hosts** - recovery should be in the application level, not lower level infra 
* **Replicate all non-ephemeral state** - do not rely on local storage for durable state
* **Keep deployment simple & fast** - avoid complex deployment in production - prefer immutable deployments
* **Fail Proactively** - do not wait for services to fail, organize regular rotations/tests as part of normal operations. Make failures non-events

## Dependency Management Best Practices
* **Latency is normal** - expect it. Narrow fault tolerances on latency leads to fragile systems
* **Isolate Fialures** - fail-fast when possible and replace nodes rather than trying to recover them
* **Use Boring Tech** - you have enough trouble with your own code, you don't need multiple moving targets
* **Contract Driven Deplendnecies** - dependent services must agree on contracts up front
* **Decouple components** - minimize coupling to achieve better stability

## Release & Testing Best Pracitices
### Principles of safe deployment
1. Must have sufficient redundency to recover from new service deployment failure QUICKLY
2. data corruption and other state-related must have their risks mitigated as much as posible because this kind of failure is hard to recover from quickly (more scrutiny for changes that can corrupt state)
3. post deployment errors must be detected by eng team -- not customers or ops
4. changes must be able to be rolled back quickly 

* Ship early & often - Deployment should be a non-event
* Observe Customer Experience as a release metric - watch the real world and alert when customer experience SLO drops
* Set Realistic Targets, Revise to Raise the Bar - don't get hung up on unrealisitc targets to start - set reasonable targets and raise the bar as you hit them
* Minimize False Positives - they sap confidence in the tests and alerts and kill a team
* Watch Trends - don't wait for failure, watch for trending twoards failure 
* Visibility - make sure everyone is watching the system health all the time
* Good Engineering Rigor - its like an apple a day - keeps the outage away
* Support N-1 rollbacks
* No single version breaking changes - every change that introduces a break should be done stepwise to avoid breaking N-1 and N+1
* Single Server deployment - system should be deployable on docker on a single machine to test at micro-scale
* Stress Test - make sure to test at 2x intended load so you both test your system meeting requirements, but also the behavior as it scales beyond intended limits
* Performance & Capacity test each new release - automate the process to avoid surprises on deployment
* Shallow deploys iteratively - do not change too much at once - favor many small deployments over massive complex deployments
* Canaries are your friends - they let you shuttle off traffic to test with real data while not putting the overall system at risk. Consider parralel production services that prove a new service is ready before mixing it into the hot path
* Test in a production-like staging environment and run system-level tests to ensure everything is working

-- Ommitted sections on Hardware, Ops and Capacity planning -- out of date and not applicable in cloud environments really 

## Auditing, Monitoring & Alerting Best Practices
* Instrument Everything - visibilty rules
* Data drives decision making
* Customer-Centric View of the service
* Instrument for Production Testing
* Latencies are the hardest problem - pay special attention to instrumentation here
* Audit all operations
* Keep performance counters for everything
* Track all fault tolernance executions
* Track all operations against vital entities
* Favor asserts to fail when you exceed boundary conditions
* Keep historical operations data
* Configurable logging is critical
* Health monitoring visibile to everyone
* Make all reported errors actionable








 
