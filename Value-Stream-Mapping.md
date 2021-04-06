# Value Stream Mapping Ecom Dev Workflows

### Why

Everyone wants to deliver customer value faster. Over time, a system unchecked tends towards entropy - development slows down progressively as complications and unnecessary or uncared for things build up and get in the way of creating new customer value. Every once in a while we need to do some ‘spring cleaning’ in addition to our regular ‘house cleaning’.

The catch is that we don’t always know where to look to make the best improvements. Amazingly humans are actually terrible at intuiting where in a process is the most valuable place to spend time optimizing - we are shockingly bad at it. Donald Knuth said that “[Premature Optimization is the Root of All Evil](http://web.archive.org/web/20130731202547/http://pplab.snu.ac.kr/courses/adv_pl05/papers/p261-knuth.pdf)” - and good performance engineers know that you measure a system in order to determine the best place to focus our optimization efforts. The same should apply to productivity.
 
[Value Stream Mapping](https://www.lean.org/LeanPost/Posting.cfm?LeanPostId=557) comes from Lean Manufacturing as a practice, and can be used to help us analyze the work that we do in order to understand where to best invest our cycles in making improvements. While the process of creating software is necessarily different from manufacturing, that doesn’t mean that many of the same concepts can’t be adapted to apply. In fact most of the world of Agile philosophies were taken by watching manufacturing process optimizations and reimagining them for software development. We want to explore using this tool to help us prioritize where to target our productivity optimizations in order to ensure that we are investing our innovation dollars on things that will have the biggest impact on our bottom line ability to deliver value to our customers faster.

### Scope

For the purposes of this pilot project we will be focusing on developers who work just a few services. If we can see common elements that those other teams might use, we will of course share them, but the focus of this exercise will be the pilot group.

### Process

We have defined a set of Personas (below) and we will interview developers that we feel are representative of those personas, pull data from their GUS tickets and checkins etc in order to build a map of the steps and associated costs with doing their regular development activities. We intend to make this artifact freely available to everyone, and we intend for this to be a living document that we periodically update so that we can continue to measure productivity in an ongoing basis.

We will then look across these different personas and attempt to identify potential improvements that will have the biggest impact across the most different personas in order to attempt to maximize return on investment. This analysis will also attempt to be mindful of known future directions so that we aren’t over investing in things that are transient. Repeating this process occasionally should ensure that we are always prioritizing the most impactful things we can.

### Personas

|Name	|Primary Use Case	|Sample Team	|
|---	|---	|---	|
|Framework Frejya	|Java Developer building cross cutting frameworks for other internal teams to use	|	|
|---	|---	|---	|
|Admin Console Bronson	|Java + Javascript developer building UI functionality for Admins 	|	|
|Javascript Stephen	|Javascript Developer building rich UI components for customers	|	|
|Backend Connie	|Java Developer building commerce functionality & APIs	|domain team	|
|???	|	|	|
|	|	|	|

### Steps

1. Start with a high level workflow simply listing the stages that a piece of work goes through
2. Walk the flow and try to capture the time taken in each stage for a few different ‘representative’ work items
3. Consider doing this not as a table but as a diagram as not all work is sequential - think about where items might bounce between stages and record what cycles exist in the process — consider creating a sequence diagram of the stages
4. Focus on loops - understand why they exist and where inefficiencies might exist - optimizing out loops has real value for the organization



