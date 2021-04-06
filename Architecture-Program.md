# Architecture Program 

## Program Overview 

### Context Map Driven
// insert context map diagram here

// table of contents here

## Program Goals

We want to bring a bit more transparency and deliberate planned technological investment to the work that we do in a way that moves the needle. By creating greater visibility across our teams into vision, goals, and plans, we can look for opportunities to share learnings and investments to create more leverage and leverage and technical uplift our organization. 

**Benefits:** This program should help us proactively lobby together for common investments, provide awareness of areas of risk, and generally improve the overall quality of the outcomes for our customers through strategic planning and coordination. This level of sharing also helps to spread knowledge in the organization and up levels all of our teams by promoting a learning mindset and an environment of collaboration.  

We strive to make our decisions on the right hand side of the following graph, as opposed to letting them fall to the left. 

[Image: Tech Debt Categorization.jpeg]

While we have a focus on our ability to ship code reliably with high quality, we also want to encourage the following behaviors:

* **Collaboration, Sharing, & Integration**: through re-use of components built throughout our Eco-system.  Ensure that all architects and tech leads can talk to the vision and that at least *N* key initiatives have been reviewed and can be described as in-line with that vision
* **Subject Matter Expert (SME) Feedback**: take time to solicit feedback from Domain SME to ensure our designs accommodate future needs from the business even if they are not obvious
* **Technical Expert Feedback:** ensure technology choices and implementation decisions validated with experts
* **Velocity from Re-use**: achieve high velocity via re-use of components 
* **Alignment & Transparency:** no hidden factories and clarity of purpose across groups
* **Towards a North Star:** ensure that all projects are provably on path to a North Star
* **Leverage Established Patterns**: establish and advocate common patterns and approaches to problems 

### Tech Review Boards (TRBs) aligned to Context Areas

Each Context will have a TRB, which is a standing working group tasked with:

* Discuss all planned engineering work, at any phase of Software Development, and offer feedback on how (and why) the work should best be executed to maximize operability, service ownership, and generally line up with organizational best practices and long range visions 
* Execute Project Launch Readiness reviews in conjunction with appropriate stakeholders for all new product launches as well as rollouts of significant changes to existing systems
* Lead by assigned Architect and staffed by the key Tech Leads in that context
* Assigned Architect MUST ensure that POs are informed of the discussions and POs may join as they see fit

> TRBs attempt to provide a framework to support our Tech Leads and provide visibility for the leadership team around the technical decision making of the organization. 


[Image: 3-in-a-box.png]
### **Virtual Architecture Teams (VAT)**

VATs are standing working groups of multiple TRBs tasked with:

* Discussing all significant planned engineering work, at any phase of Software Development, and offering guidance on how (and why) the work should best be executed to maximize operability and service ownership and generally line up with organizational best practices and long range visions
* Collaborate on and present proposals to Architecture Guilds for alignment
* Execute at least Monthly reviews for all significant, long term work streams (LRP owned work streams)
* Hold Quarterly Retrospective to determine how guidance was incorporated back into our delivered products
* Staffed by the TRB Leads within the associated teams
* Attendance by PMs associated with the area is welcomed to promote product and technical alignment

## Program Specifics

### <TRB Name>

**Architecture Leader:** {Name} {email link}

**Weekly Meeting Schedule Link:** {Recurring Date} ([Add to Calendar])

**Slack Channel:** {slack link}

**Current Stage:** {stage} 

**Key Invitees:** 

* {primary audience members}
* {critical invitees}
* {optional invitees}

|Domains	|Eng Leader	|Tech Lead	|PO	|
|---	|---	|---	|---	|
|	|	|	|	|
|	|	|	|	|
|	|	|	|	|


* * *

## TRB Stages

Building an architecture program takes time. To help us understand the progress the TRBs are making towards the end goal we want to use a leveling system to indicate the expectations for that TRB. To make this easy we can talk about it in terms that we often think of as the stages of team development, and then set expectations for what to expect of a TRB when it is in that phase of its life. 

We should understand that like any team, sometimes we will float at the border of a stage — not quite achieving the next level, and sometimes taking a step back because of inconsistency. That’s ok. This is all a journey to where we want to be.

### Stage 0 - Forming

During the formational stage of a TRB everyone is still getting used to new concepts. At this level our goal is simple: get people comfortable sharing with each other what is going on technically in their teams on a regular cadence. The focus is conversation and sharing. 

Key Expectations at this stage:

* TRB slack channel exists
* there is a recurring meeting on the Public Calendar that anyone can attend
* key Tech Leads are identified in the above charter for the TRB and attend regularly
* meetings are recorded and posted to the channel for anyone to view
* powerpoint presentations or open discussions more common 

### Stage 1 - Storming

During the next phase we want to start encouraging healthy debate in the teams. Meetings should be less show-and-tell presentations and more a discussion among the participants. Questioning to seek understanding and debate should be encouraged - we want all participants to understand why certain decisions were made. The TRB should start to become a bit more organized with several weeks of topics planned in advance and the TRB Leader should ensure that topics are coming from every team.

Key Expectations at this stage:

* All teams are participating
* Shift from open discussions to guided discussions starting from a document to review
* Active debate and questioning
* Several weeks of topics planned in advance

### Stage 2 - Norming

Once the TRB has been running for a while and the level of engagement is good, the next major stage introduces more coaching from the TRB Leader and starts using the TRB as a vehicle to ensure some architectural consistency by having teams regularly show to each other the things that they are prioritizing in terms of work.

Key Expectations at this stage:

* TRB Leader is regularly meeting with Tech Leads from the TRB
* Teams are presenting their Tech Backlogs and Roadmap ideas
* TRB Leader ensures that the most important projects that the teams are working on get reviewed at the VAT 

### 
Stage 3 - Performing

At the final stage, the TRB we introduce more formality to the consistency and start tracking our documentation to ensure that all teams are meeting the agreed upon documentation sets and keeping them up to date. The TRB Leader is accountable to inspect each of these documents, and to raise it to their director when teams are not completing the expected artifacts. 

Key Expectations at this stage:

* All teams are writing design documents using our standard templates
* All teams have documented visions for their domains that have been reviewed at the TRB
* All teams have a 8-12 month Rolling Roadmap plan for technical investment
* All teams are documenting their test strategies
* All teams have documented monitoring and service ownership assessments / plans

* All teams have a set of proposed spikes for upcoming RPs
* All teams maintain a list of PRBs 
* All teams maintain a library of Runbooks

### TRB Leader Expectations

**Open Meetings:** It is expected that the weekly TRB meetings be openly posted by the TRB Leader so that anyone might join in, that their sessions are recorded and posted so that someone missing a meeting may review and catch up on the content of the meetings. 

**Accountability:** It is additionally expected that the TRB Leader ensures that the reviews and documents are happening and up to date, but it is *not* the job of the TRB Leader to create all documentation. The entire TRB team are required to work on the documentation and the TRB Leader is accountable for the quality of those documents.

Once per month the TRB Leader should ensure they make time to meet with:

* ***Tech Leads 1:1s:*** with each Tech Lead to assist them in development of the technical backlogs for their teams, and to help mentor them on developing their technical leadership skills
* ***TRB Leadership Sync:*** with the Eng Dir and PM Dir of their assigned domains to stay aligned on priorities and review observations

* * *

## VAT

**Architect Leader:**  {Name} {email link}

**Weekly Meeting Schedule Link:** {recurring schedule} ([Add to Calendar]()
)
**Slack Channel:** {slack link}

**Key Invitees (Internal):** 

* {TRB critical attendees}

**Key Stakeholders (External):**

* {attendees impacted by decisions in this VAT}

## VAT Artifacts

The VAT Architect should work together with the TRB Architects to maintain the following set of up-to-date documentation posted in a location easily accessible to all other teams in the group:

* Maintain Documented Global Technical Vision for the product lines
* Prioritized Backlog of Cross Cutting Themes to be investigated for the next 18-24 months
* Maintain and update Library of Patterns & Standards 

The VAT should seek to harmonize the contributions of the various TRBs, to argue for investment in technical initiatives, and to identify and resolve issues that cut across the TRBs in a broader product and technology sense.  

### VAT Leader Expectations

**Open Meetings:** It is expected that the weekly VAT meetings be openly posted by the VAT Architect Lead so that anyone might join in, that their sessions are recorded and posted so that someone missing a meeting may review and catch up on the content of the meetings. 

**Accountability:** It is additionally expected that the VAT Architect ensures that the reviews and documents are happening and up to date, but it is *not* the job of the VAT Architect to create all documentation. The entire VAT team are required to work on the documentation and the VAT Architect is accountable for the quality of those documents.

Once per month the VAT Architect should ensure they make time to meet with:

* ***TRB Architects 1:1s:*** with each TRB Architect to assist them in development of the technical backlogs for their teams, and to help mentor them on developing their technical leadership skills
* ***Group Leadership Sync:*** with the Eng VP and PM Dir of the prodcut lines to stay aligned on priorities and review observations

Once per month the VAT Architect should ensure they make time to meet with:

* ***TRB Meetings:*** For each TRB, sit in on the regular meeting to keep a feel for what is going on with the TRB team

