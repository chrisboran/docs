# Classifying Work

There has been some confusion about what exactly certain categories of work “mean” — what bucket should a particular item fall under. Here we would like to detail the different categories of work, and how they should be classified so that the work can be consistently tracked across the teams so that leadership can make better quality analysis of decisions. I am writing this not on a theory but because I have seen consistent misunderstanding around these categories and I want us to seek to align on common definitions.

Something important to keep in mind when categorizing work: The **reason** work is being done plays a role in its categorization. The same piece of work might be categorized differently depending on **why** that piece of work is being done — context matters a great deal when it comes to tracking investment!

## Repetitive Costs

There are a number of themes that repeat release after release and do not relate to new feature initiatives. We want to define these themes consistently and make sure we tag them properly in in our ticket tracking so we can track our investments in them over time.

### Security 

Things labeled with security should not refer to new features that make our customers more secure (ie requests like adding MFA support or adding new customer facing encryption methods, etc) — those investments should be tagged as features that just happen to be security related. Instead the Security tag should be reserved for those items relating either to bugs under Security SLA or projects involving Security Trust Uplift of things that are not directly customer facing. This should also include the cost of things like 3PP library updates etc.

Security is a special case of RTB costs related to how engineering works that are driven by our security needs in our organization. Security is called out as a separate theme from RTB because we want to track it more granularly. It should not be the case that anything requested (even by our security team) that relates to how the product offers security — those items should be classified as product asks because technically those are security asking our product team to do feature work.

### Investigations

Investigations are anything triggered by SRE, support, our own alerting, or even other engineering teams are interrupt driven and represents time spent assessing if or how something is behaving in an unexpected way in production. This is the primary method that we use to track costs for supporting the customers in production. 

Investigations are also a special case of RTB costs that happen with enough frequency that we feel it is valuable to track them separately so that we can gain certain insights into our investments. 

### Defects

Often the result of an investigation is a defect that needs to be fixed. This work should be tracked separately from the investigation. We also want to likely track the difference in cause of the defects after the fact (ie was the root cause a coding error or a specification gap) for our future analysis, but for planning purposes we might look at our historic time spent fixing defects and plan for a similar defect repair budget in our release planning process.

Again, Defects are a special case of RTB where the costs happen with enough frequency that we feel it is valuable to track them separately so that we can gain certain insights into our investments.

### Run The Business (RTB)

This is a catch-all category of work that cannot be avoided because it is associated with running the SaaS that doesn’t relate to the previously listed categories. This will typically include manual actions that will be performed repetitively or on a one-off basis. Examples can include release overhead, manual testing overhead, etc. 

Run The Business should **never** include things that are requested by product management or the tech lead of the team — this category is to track unavoidable costs. Should we notice trends of types of work we may break some of this out into a new category to track in the future the way that we are tracking Security, Investigations and Defects at engineering leadership discretion. 


> **Toil**

> Toil is **not** a category we will track explicitly. Toil is a subset of all RTB work across the different themes we have talked about, and is the type of work that is avoidable if we try. Toil is the work that does not produce new customer value, and often is represented by things that cannot be ever ‘done’ because when you finish the work, after some time that work will reappear. 

> 

> Types of things that are often called toil include things like manual testing, manual truncation of tables, routine support operations, routine release operations, configuration operations, etc. If we try a lot of toil can be eliminated via smarter automation or via process changes. 

# Tech Enablement

Things are labeled as Tech Enablement is **solely** at the discretion of the Tech Lead of the team. Nothing can be labeled as Tech Enablement without the tech leads explicit agreement. If the tech lead notices something tagged as Tech Enablement that belongs in another category, they are expected to re-categorize it to prevent our tracking from being inaccurate.

Tech Enablement is **not** related to RTB in any way and we should not ever confuse the two. 

### **What is tech enablement?** 

It is any work that the tech lead deems necessary for the long term health of the team. Sometimes this involves work to reduce various RTB costs (ie toil reduction), sometimes it is paying down old Tech Debt, and sometimes it is building new things proactively to make future projects easier. 

### **What is not tech enablement?** 

* Defects fixing is not Tech Enablement - despite some rumors to the contrary. 
* Technical things that we build because of a feature requested by product is not Tech Enablement — those are just part of the cost of the new feature and should be associated with it.
* Run the Business costs are not Tech Enablement - they should be tracked separately
* Finishing work that was specified by the Product Owner but did not meet the Definition of Done (DoD)
* Finishing work that was committed in a prior release but not finished (like low code coverage numbers or incomplete technical docs)
* Production Monitoring and associated service ownership costs

## Investment Expectations

**Teamwork** is key in a healthy Agile process. Scrum Teams are supposed to be ‘three-in-a-box’ for decision making. Anyone who thinks that a single member of the leadership team can make decisions without the others is practicing a *dictatorship*. Scrum is a whole-team practice and is intended that the 3 key leaders on the team ***negotiate*** with one another. 

In a healthy scrum team, there is always a slight tension between the roles - this is on purpose to help the team ensure that they are equally considering technology (Tech Lead responsibility), customer value (Product Owner responsibility), and ability to execute (Scrum Master responsibility).

### Tech Leads 

Tech Leads are expected to bring a well-thought-out Tech Backlog to release and sprint planning and to meet with the Scrum Master and Product Owner proactively to help them understand the material value of the items in the backlog to the business/team. The Tech Lead must be able to clearly articulate why the items being prioritized are important and how the items support the objectives of the organization. Tech Enablement items must be able to map directly to real value either in terms of developer productivity, reducing RTB costs, reducing customer pain, or technical investment to accelerate known feature roadmap needs in the future. Tech Leads must expect that they are challenged by their fellow leads. 


> **Super Power:** Only the Tech Lead may label something as Tech Enablement and propose the tech backlog priorities

### Product Owners

POs should expect somewhere around N% (actual number can be an agreement via negotiation amongst the leaders of the team - but somewhere close to 40% tends to be a healthy number) of the release planning capacity for items prioritized at the top of the Tech Backlog. While this number does not have to be precise we do need to make sure that on the balance investment comes out for **every** scrum team. Failure to do so causes RTB costs to rise, killing overall team capacity over time and ensuring that the team is able to produce fewer and fewer new customer facing features as they will become mired in the RTB costs. 


> **Super Power:** Only the product owner can propose a prioritized release plan backlog and sprint backlog for the team 

### Scrum Masters

Scrum Masters have the hardest job of all: they hold the veto power - team commitment. Their job is to review the release plan proposal and speak for the team. The Scrum Master has to mediate between the Tech Lead and the Product Owner and represent the best interests of the team in doing so. If the Scrum Master believes that the plan being proposed by the Product Owner is not in the best interest of the long term health of the team (for instance because of under investment in tech enablement) they are required to reject it and ask for a new plan.


> **Super Power:** Only the scrum master can commit the team to a plan (release or sprint). The scrum master must exercise the veto power if the proposed plan is not in the best interests of the team

