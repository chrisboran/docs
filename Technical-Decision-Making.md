# How do I go about selecting a particular technology to solve my problem?

This document attempts to setup some basic process guidelines to help teams make an assessment about which technology a team should use to solve a particular problem in their project. It is intended to be used by the Tech Leads to help manage their team through technology selection processes.

## The Process

### **Understand** 

Always try to start by being very clear: **What problem am I solving?** It is really easy to geek out and get excited about a particular technology, but the hard part is making sure you are using the right tool for the job. Start by writing down what your problem really is - what are the edges of your problem. By understanding the problem better up front, you will end up with a better solution. At this point you should be starting a wiki or quip document that can be shared with others. You will make better and more objective decisions by writing things down.

### Discover

**What does a good solution to this problem need to be able to do?** By defining your requirements in terms of solving a particular problem you generate criteria that will help you evaluate your solutions later. By writing down these required capabilities you are freed from the slant any particular tech choice constrains your thinking — **don't think about technical solutions yet** - just stay on target figuring out what the blobs on your architecture diagram need to be able to do.

### Resarch

Start researching which services, products, and open source projects might be usable to solve your problem - do your research before considering building anything yourself. Remember that we should be **focused on building IP in our business space** for the company, and we should make use of tools developed by others before going out on our own.

### Prioritize

Prioritize the **must have, nice to have and interesting** requirements for a solution based on your research. Avoid generating your requirements in such a way that it is heavily titled towards a particular solution. The requirements should be clustered around your needs and what can be satisfied. 

### Analyze

Create a **matrix table in your HLD** (High Level Design Document) evaluating how well each solution is at satisfying each of your requirements (1-5 tends to be a useful scale) - make sure to include security concerns, performance and scale concerns, prevalence in the marketplace and long term maintainability of your options. Non functional requirements should be given equal weight to functional requirements in this analysis. Involve your team in this analysis — the team will feel more ownership of it if they have all had a voice in evaluating the different dimensions.

### Reflect

Review your matrix. Did you **avoid 'stacking the deck'** in favor of a particular technology? Other engineers need to be able to review this artifact and not feel like the assessment was intellectually dishonest. We've all see website product comparisons done by marketing. We want to remember that as engineers we know that every tool will have strengths and weaknesses - make sure you are being fair in your assessment.

### Consult

Make a list of opinions you should seek. You should at a minimum seek input from another member of the TRB and one from the VAT. Additionally you should think about who else in the organization might have interest, expertise, or a stake in the decision. Invite these people to review the matrix and contribute to it **before it is finalized**.

### Communicate

When the decision is made, capture it along with the rationale in the HLD. We want to ensure that anyone who reads the HLD will understand why the decision was made the way that it was. The decision should not be considered finalized until it has been reviewed as part of a formal HLD review. Once made we want to announce the decision so that others **understand what was decided, what the scope of the decision is, and how it might affect them**. 

### Commit

If the driver has done a good job to this point, it should be easy to get folks to **commit to this decision and move forward**. Decisions can be revisited in the future if new information comes to light, but without material change to the information involved, we want everyone to trust that their peers have made a good decision and move forward. By being transparent about the reasons for the decision and how it was made, folks should be able to commit more readily. 

### Whoops

Everyone always makes the best decision they can with the information at hand. No one should feel bad about doing their best and being wrong. Sometimes the requirements were not quite right, sometimes the assessment of fit in the matrix was off. Sometimes the research was shoddy. While we should not be afraid to admit mistakes and reexamine, we also want to involve the original driver in the process of reexamination. 


### 


