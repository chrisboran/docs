# Avoiding Dependencies in a Code Ownership World

### Problem

In the industry there are many models around code ownership. For some teams their code is like their baby - they love it and care for it and clean it up... and they would be freaked out if a stranger started playing with their baby or dressing the baby in new clothes. This is a totally rational viewpoint and it creates great accountability for the software that the team owns and leads to well curated products. However this also has a detrimental effect - it creates a nightmare ball of program dependencies in order to do anything beyond the scope of a single team. This is especially a problem for teams who are platform-centric in nature. 

For instance, say Team B arrives on the doorstep of Team A with a large list of features they need from the code owned by Team A in order to accomplish their important business goals. Team A already has a prioritized list and Team B's needs are below the line — they won't get to them until late. Now Team B is stuck - either:

1. they duplicate Team A's functionality so that they can move forward, or 
2. they take a dependency and potentially delay their project


Even if Team A wanted to sign up for the work - dependent projects are very hard to do well. So even if they accept the dependencies, Team B looses autonomy because they have to hope that Team A can deliver on their promises - which sometimes doesn't happen. This loss of autonomy can often manifest in the form of Team B blaming Team A as the reason they miss their deadlines - which fosters an unhealthy working environment for Team A, and causes both teams to feel less invested in the business outcomes that should be at the heart of their work.

None of these options produce consistently good business outcomes - in most cases it is a lot of extra work to deal with these dependencies, and represents large scale business risks to the schedule. 

### Inspiration: Open Source Models

For a moment consider, what would we do if Team A in the above scenario were actually a 3rd party open source project. If Team B were counting on functionality from, say an Apache project, how would the team interactions be different? What would be the acceptance criteria for us to build this functionality?

Likely Team B would start by consulting with the Apache project maintainers, starting with some functional questions: would the project want this functionality? Are there existing designs? Can we work on a design together? Can you share your plans for this project?

Next Team B would create a branch and start working - Team B would do the coding to the agreed specifications, and then submit this back as a pull request. The Apache project maintainers would review the pull request, ensure that the proper testing has been done, and that the new features meet the agreements and acceptance criteria, and then the Apache project maintainers would merge the code into their mainline and it would be part of their next release. 

As part of this interaction, future bugs would likely be fixed by the Apache project maintainers - they take responsibility for the maintenance in exchange for the contribution. 

### Applying the model here 

If we were to revisit this example with the lens of an open source project, could we approach it the same way? If Team A either can't commit or has other priorities that compete, would they instead be more inclined to behave like an Apache project?

To achieve this kind of model:

* Team B's PO should engage with Team A's PO to get a understand how the feature roadmaps may/may not align
* Team A's PO needs to be transparent about the team's other priorities
* Team A and Team B need to agree upon and document an agile working agreement on how the teams will interact with one another
* Team A's Tech Lead needs to either furnish or approve the design for the requested features
* Team A's PO & Tech Lead need to provide functional and non-functional (engineering) acceptance criteria up front for Team B
* Team A's Tech Lead needs to be prepared to answer questions and provide guidance to Team B as a priority
* Team B must adhere to Team A's standards and practices for submissions and testing
* Team A (Eng+PO) must review the PR for functional and non-functional acceptance
* Team A must be prepared to maintain the submission once accepted 
* Team B must be prepared to respect a 'warranty period' (agreed upon up front) where they are obligated to investigate and fix issues uncovered in their submissions
* Team A's engineering leaders must track how much code is being contributed and make sure they properly account for ongoing maintenance

### Commitment

To adopt a model like this, Team Tech Leads need to see it as their job to guide teams to build in their area of responsibility - not just their own team but any team. This also requires the PO and Tech Lead to have good vision and roadmaps both functional and technical. But if pulled off successfully it helps empower teams to control their own destiny, while still maintaining the high quality that comes from having code owned and cared for. 
