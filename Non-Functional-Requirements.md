# Non-Functional Requirements

### What are they?

A key to the long term success of any SaaS system at scale is the recognition that there are many expectations on the system are not strictly related to the basic functionality upon which most Product Managers will tend to focus. These expectations have a tendency to be silent, surfacing only after they have not been met in a production environment. 

These requirements can be expressed as **Architectural or Non-Functional Requirements** - requirements that do not relate strictly to the aspects that are immediately apparent, but that are intrinsic to the system and that must be satisfied in order to achieve the unspoken expectations of a cloud-based system operating at scale. 

Agile methodologies, while incredibly effective as an execution framework, have the nasty side effect of discouraging long term thinking. This can often lead teams to declare themselves as 'Done' as soon as they have met all of the **Functional Requirements (FRs)** supplied by their Product Manager. It is therefore incumbent upon the **Engineering Technical Leaders** (Architect, PTMS, LTMS) to help the team by ensuring that **every project** includes a comprehensive set of **Non-Functional Requirements (NFRs)** in their project plan - they must help the teams be kind to their future selves. 

Another way to think about this is that **Functional Requirements** describe what the system should **DO** for the customer, while **Non-Functional Requirements** describe how the system should **BEHAVE** in a range of scenarios.

### Who is responsible for what?

Development of Non-Functional Requirements is an **Engineering** **Team Responsibility**. Every member of the team should be concerned with asking themselves if they have sufficiently thought through the potential failure scenarios and understand how the system should behave in all foreseeable scenarios. These requirements should be developed co-operatively within the team and not imposed from external sources, because failure of the team to grok the NFRs often leads to corner cutting — the team must both **understand** and feel **invested** in the NFRs.

**Technical Leaders** (Architects, PMTS, LMTS) are responsible for leading the team through the process, and then reviewing the requirements with the broader TRB to ensure the completeness of the NFRs. It should be considered a prerequisite to starting any detailed design.  Moving forward with designs that do not account for all of the NFRs must be considered suspect. The Technical Leaders should not write all of the requirements themselves - their job is to ensure that all of the NFRs get discovered and agreed upon. The whole team should be involved in the process.

**Engineering Managers** and **Product Managers** are responsible to make sure that the NFRs are properly prioritized in the project, and that no time commitments are made until the NFRs are understood since they can have such a large impact on the project scope - they are the equal to the Functional Requirements and should be treated as such.

The **Virtual Architecture Team (VAT)** is responsible for providing an outside assessment of the Non-Functional Requirements as part of the TRB preliminary review.  The VAT should assess if the NFRs are complete or there are additional requirements that need to be considered. Additionally the VAT is responsible for building and maintaining the list of thought provoking questions that will help the teams discover the NFRs.

### How do we DISCOVER Non-Functional Requirements?

Luckily NFRs tend to fall into categories. While the requirements themselves are not vanilla and cannot be reused across all projects — the process for their discovery tends very much to be. This process is most effective when the team's **Technical Leader** leads the **Engineering Team** and **Product Manager** through the exercise of discovery so that there is a shared understanding of why each requirement is important. 

To help facilitate these conversations we provide a set of questions to aid in the discovery process for NFRs. This activity should be done before the **Initial Design Review** of the  **High Level Design Document** (HLD).  It is important to take time writing stories to correspond to them during the Epic breakdown phase in project planning - otherwise you will discover late in the cycle that you have missed critical requirements and need to replan your project. The Initial Design Review gives us a great checkpoint in the process to review and certify that we have broad agreement on the NFRs for a new feature.


### What would Non-Functional Requirements Look Like?

Here are some samples from each of the categories of NFRs that we should be thinking about:

* Performance
    * What is the expected range of response times for the servers in this scenario?
    * How do we behave when the max time is exceeded? 
    * What is the plan for performance testing?
* Scale & Capacity Planning
    * What is the expected call volume for this API and how will we behave when it is exceeded?
    * How many items can be returned in a single call and how will we behave when the max is exceeded?
    * How much memory will the containers that run this workload require?
    * What are the scale choke points of this system — memory, cpu, network i/o, disk i/o, storage?
        * Do different components scale against different choke points?
    * Do our containers scale horizontally (we can add more containers if we need to scale) or vertically (we need to buy larger machines to scale)?
    * What is the expected cost model to run this service?
* Resilience 
    * How will we behave if a dependent service goes down?
    * How long will we wait to decide if a service is down?
    * What do we do if a message gets lost?
    * How durable is our backing store? 
    * What happens if the cache gets dumped?
    * If the service restarts, can it resume its work or does it have to start over?
    * Can we safely retry? Are the messages idempotent?
    * What happens if our workload is killed?
    * How is service health going to be determined?
    * What will we do if this service fails during rollout?
    * What happens if a host goes down?
        * Best Practice in AWS: when running in AWS a best practice is to presume that within an AZ you could lose a percentage of your hosts (we presume 1/3). 
    * What happens if an Availability Zone goes down?
    * What happens if there is a network segmentation between our hosts?
        * Many distributed systems have tuning and/or failure modes.  Good reading here would be on the CAP Theorem.  You can also read about “split brain” scenarios in many clustering solutions.
        * In a distributed cache consider any concerns that you may have with consistency when this occurs.
    * When upgrading how many hosts will you upgrade at a time and how will this impact your resiliency?
        * Best Practice: don't upgrade all nodes at once!  Upgrade in a rolling fashion taking no more than 1/3rd of your capacity away at any moment in time.
* Maintainability & Supportability
    * How much effort goes into standing up more instances?
    * How much effort will go into keeping this service running smoothly?
    * What type of hooks do you need in order to start, stop, restart your service?
    * What recovery mechanisms might you need to get out of a bind?
        * Examples: Suspend incoming traffic to resolve DB Locks, Dead Letter Queue on failed messages to debug/retry later, Replay message capability for when dependencies fail.
    * How hard will it be to fix a bug in this service?
    * Have we built tools for L1/L2 support to be able to help our customers in the event of a problem?
    * What self-service tools can we provide to the users along with this project?
    * What self-diagnostics and automated recoveries can be built?
    * What scenarios will we write runbooks to help L3/L4/L5 diagnose and remediate issues quickly?
    * What can we automate to reduce the costs of operating this service?
    * What is the impact of upgrading any of the components we operate?
    * Have we automated a deployment strategy?
    * Have we defined and automated a disaster recover strategy?
    * Has this service been designed to balance customer load (like a pod move)?
* Security 
    * What kind of data are we storing and how are we keeping it secure?
    * What bad can happen if our service container is violated?
    * Do we need any network micro-segmentation or ingress/egress traffic rules?
    * Are we GDPR compliant?
    * What aspects of this new service need to be considered for our SOC report?
    * What are we doing to protect our PII?
    * How will secret material be distributed and secured?
* Compliance
    * Have we considered GDPR in our design?  Do we understand what is required of us?
    * Does our service fall under SOX/PCI/HIPAA compliance?
* Configurability & Deployment
    * How will we change configuration of this service?
    * What level of configuration will be available? Per Pod? Per Realm? Per Instance?
    * How soon will configuration changes be applied to this service? Do instances need to be restarted for configuration changes to get applied?
    * How will we deploy this service - canary? blue/green? In-place with rollback? 
    * How will we maximize the automation for the deployment?
    * Are there recovery points and checkpoints during the upgrade/deployment that can be monitored?
    * Can this feature be upgraded/patched/enabled/disabled in a non-disruptive fashion?
* Monitoring & Logging
    * What will be the key metrics to monitor for the success of this service?
    * Will we be placing any alerting based on metrics or logs?
    * Which log messages do we need to document?
    * When will log messages be outputted?
* Testability
    * How will this service be tested? 
    * How will integration testing be performed?
    * Will there be any service contracts available?
    * Will the service accept client-contributed tests?


* * *

# Silent Expectations

2.5 years after I started this document, I read the following blog post which I think a reader of this document should also think about as it is in the same vein https://theprogrammersparadox.blogspot.com/2020/05/basic-expectations.html (reproduced below in case the original post gets moved)

*When interacting with any software, there is a fundamental set of overall ‘properties’ that the users expect. If these are not met by the system or product, they should be considered as software bugs, even if it isn’t explicit misbehavior in the sequence of instructions. It may be very hard for the programmers to fix some of these issues, depending on the state and organization of their code.*

### Availability

* The system is available when the system is needed.
* If part of the system is currently unavailable then the user will be notified before they start doing any work in that part of the system.
* If part of the system was unavailable, there is somewhere the user can go to see that that had occurred.

### Correctness

* If the system provides a calculation or computation, then the results of that work are either correct or it produces a specific error.
* If the system provides a calculation or computation, then if the user redoes the work with the same context, it will produce the same results (repeatability).
* If data is displayed on the screen with a label or attributes, then that labeling is correct (trustworthy).

### Completeness

* If someone can add some data, they should be able to modify and delete that data.
* If someone can perform an action in a given context, then they can perform the same action in any similar context.
* If a system has data, at least one interface exists to display that data.

### Context

* If there are a series of context-based operations that are reversible, then when reversing, all of the in-between context states are reachable.
* For example, if you scroll through a list of links, then jump to one, hitting back will return you to the last position of the scroll, not the top of the list (very common bug).

### Composable

* If you can do an operation in bulk by building up the context, it should work correctly to apply that bulk operation to everything (stability and performance).
* If the composition gets too large, then the system will warn about a limitation, but not undo the current composition.

### Visibility

* If a user enters data, the default scope (visibility) is to just to that user.
* If the scope is widened, either the user-initiated this or is aware of this (transparency).
* For any data, there is a way to see it’s current scope (transparency).

### Searchability

* If the system allows for searching, there is some composable way to narrow down the search to any specific item.
* If the system allows for searching by a category of items, then the results only contain that category.
* If an item exists in the data, then it can be found in the search.

### Performance

* Any computations done will be bounded (finish).
* Any resources used will be bounded (estimable).
* The worst-case time for the largest amount of work is still reasonable (usable).
* If the computation will take longer than expected, the user will be notified (progress bar).
* If the work takes a sufficient enough time, it can be stopped (cancelable).


* * *

## Planguage

Another interesting dig that I found recently was this overview of a formal process for specifying NFRs that uses a system invented in the 1980s called [**Planguage**](https://en.everybodywiki.com/Planguage) **** while the Agilista in me thinks it can be a little bloated and overboard, remembering there is a lot of good things here and as anyone who knows me can tell you, I love to take concepts that are well vetted in other places and apply them to the current state of engineering - there are no new ideas in computer science, just new implementations! 

Presentation for reference: http://www.iaria.org/conferences2012/filesICCGI12/Tutorial%20Specifying%20Effective%20Non-func.pdf

Some key things not covered in other sections above that are interesting to think about are covered below:

### **Words Matter**

Watch our for wording that is ambiguous or leaves it up to the reader’s interpretation of the requirements. Some categories of weak words to be aware of: 

* weak words (ie easy, quick, normal, reliable, effortless, immediate, secure, intuitive, frequent, timely) 
* unbounded lists (ie at least, such as, or later, ‘including but not limited to’) 
* implicit lists (ie modern browsers, all users)
* ambiguous terms - vague statements, subjective statements, optional statements, under specification and under reference (ie previously defined)
* verb clarity (ie what action specifically is required)
* specificity (each, every, only) - be clear

### Verifiability

In order for engineering to accept a non functional requirement, they must have a clear idea of how we will test in order to verify that requirement. Just like DoD forces us to know ‘when we are done for a Feature, we need clarity in our non-functional requirements just the same way. If we don’t know how to test and verify it, we don’t know we are done.

### Prioritization

Clearly indicating how important this requirement is relative to other requirements (ie prioritizing your NFRs) is a great practice that we tend to do subconsciously - but our NFRs should be prioritized against each other just like we do for functional requirements as we all know that it is seldom possible to design for all requirements equally.

### Intervals & Meters

Instead of slapping down a single number, think about a scale of acceptable values up front. If you say you want 200tps for your Order API... where are you willing to settle? If you hit 180tps and there is other work to be done... do you accept that and move on? By deciding up front your range of acceptability using a Target, a Minimum bar and a Outstanding or Stretch measure, you give the team more room to make their own decisions about prioritizing other work. Also it is important to indicate the meter you are using. Often we forget how measures can influence each other in a mulit-tenant system so think carefully about things like how latency might be impacted by throughput and vice versa. Think about how this will be measured up front to help you decide if it is a good measure to be requiring.
