# Determining Reliable Scale Guidance

## The Challenge

In a a complex distributed system that allows for a large swath of variation in what a customer can customize that will alter the behavior of the system. Every customer instance has a high degree of variability. It becomes a nightmare to predict the behavior of any complex system when the number of independent variables go up - the more variables the harder it is to reason about the system. This continues until the problem feels unsolvable - we cannot know therefore we should not try to know. 

So we develop a high-touch approach that involves careful coordination, deep monitoring and experts who have a wide swath of knowledge about the system and its leading indicators. This approach is great to ensure that implemented customers will be successful, but offers little material data driven up front insight for prospects, and not a lot of material guidance to those in the implementation phase about what they should do and what they should avoid doing. 

The business needs us (engineering) to provide clear guidance. How can we tackle such a hard problem? How can we eat a whole elephant? 

## One Bite at a Time

We want to shift our mindset. Instead of trying to answer the question “Can we scale functionality X to Y level?” and go design tests to prove/disprove, instead we need to adopt a different thought process. We need to focus on building a deep understanding about the **resources** that cause scale issues, what pieces of **functionality** scale with those resources, which pieces of functionality **share** the same resources, and focus on building tests to demonstrate the models we use to determine the scaling. Sounds easy right? 

Well, it takes a lot of methodical work to do this. It requires us to gather quite a bit of data first. We also want to take inspiration from some common frameworks — in this case the [USE Method](http://www.brendangregg.com/usemethod.html) is a good candidate to take inspiration from. The focus will be for us to understand our resources, utilization, and limits. Our benchmarks will follow from that knowledge.

* We have to gather data about the resources that typically fail under production loads
* We have to gather data about what functionality is used in which ways by typical customers
* We have to dive in architecturally to understand which functionalities map to which resources
* We have to understand which resources reaching limits are more important to which functionalities
* We have to have an understanding of which functionalities consume the same resources

But the good news is that all of these things are knowable - we just need to do a lot of hard work to gather the data first, and then perform thoughtful analysis. 

## Scientific Method

First and foremost we want to focus on the scientific methods. We do **not** want to run tests and 'see what happens'. We want to gather enough data so that we build a hypothesis and then design our tests to prove or disprove our hypothesis. Every test we design and run should answer an explicit question for us, and have a clear metrics based answer.

## Resource Identification

Systems will scale with their resource consumption some critical resources. Often these resources come down to some set of*:

* Memory
* I/O
* CPU
* Network
* Lock Contention

These resource limits might be on different systems too - different data stores, different application workloads and different buffering/eventing will all lead to variable results.

Each resource should be examined and cataloged as a dimension by which a particular functionality might consume. We can start by cataloging all of the resources that are consumed. 

**Note: lists are meant to be illustrative and not exhaustive - the expert teams should create their own lists* 

## Functionality Identification

Next we determine what the critical pieces of functionality customers care about, and what pieces customers most customize. We don't want to focus on just what they ask about, because it could be that customers don't ask about something that they assume they can customize a lot. We should for this step we want to examine both the High Scale team's customer data, and the real world observations that the Performance team have tools to peer into to see frequencies of object distributions and rates of change. 

From this we should create another list - our list of critical functionality. This list will be the list of the things we want to provide reliable guidance around and will drive how we design our tests.

## Code Spelunking

Next we go spelunking in our code. We take each piece of critical functionality (use case), one at a time, and walk through the code and record which of our cataloged resources that piece of functionality makes use of. This cataloging process may seem tedious, but having all of the facts cataloged is critical to good decision making. This step will provide rich data necessary for future steps in the process, so it is important to do a good job here.

## Determining Dominating Resources

Once we have the list of critical functionality and what resources it impacts, we can prioritize the functionality we want to test first. With each piece of functionality we can independently test focusing on stressing just that singular functionality, and paying attention to the utilization and stress (faults) that occur on those resources. Because we have already determined which resources a functionality utilizes, we can design our tests thoughtfully. 

Once we have run a few scenarios for a piece of functionality, we should be able to determine which resources dominate the scaling (fault first) and are the primary determinants of how this piece of functionality scales. We carefully catalog the dominating resources to understand how each piece of functionality scales. 

## Dependency Identification

Once we have determined the dominating resources for several pieces of functionality, we start to build a picture of how the different functionalities can impact one another through their dominating resource sharing, and how others move independently because they don't share dominating resources. This picture helps us to better understand our system in its entirety. 

It is expected that this will be a somewhat complex map of dependencies, but this white box methodology gives us a basis for making better decisions later, and a deeper understanding of how our features interact and influence one another.

## Independent Benchmarking

Now that we have an understanding of basically how our piece of critical functionality scales, we can fix the values of the non-dominating resources and design tests to benchmark the dominating resources. We can execute those tests and record their results with the goal not of pushing the system to a prescribed target, but rather to understand the levels we need to reach in order to saturate utilization or observe increases in faults to tell us that we have hit our limit and record those limits.

## Stress the Dependencies

Things have been easy up to this point, but now we come to the hardest part. However the good news is that this part looks similar to how we have traditionally done performance & scale benchmarking, only this time we are armed with a lot of independent knowledge. 

In this stage we take our independent benchmarks and we target testing along the dependency boundaries that we have identified, pushing our resource utilization to fault in order to identify which functionalities utilization of resources dominate the others. From this will emerge the dependent variables - as stress on one functionality goes up, what other ones go down. We will find out in this testing which functionalities are the pain points in definitive terms. 

## Final Results

By combining the results of the Independent Benchmarking and the Dependency Stress we will be able to identify the functionalities that effect our scale most, and how they inter-relate. The focus will not be on trying to push the system to hit a specific number, but to build a model that represents our scaling. 

We can then provide guidance on 'safe' values across the board, and on how moving the scale factor up on a particular functionality impacts other pieces of functionality because we have good understanding of the underlying resources and how they are being utilized in the various scenarios. We can also then provide the rich information to the High Scale team for evaluations with a clear understanding of risk profile of various recommendations.


