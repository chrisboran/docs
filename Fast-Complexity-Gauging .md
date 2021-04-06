# Soopah-SWAGs: Fast Complexity Gauging for Release Planning

Sometimes in release planning, a team feels a lot of churn because of shifting priorities. The business maybe suddenly facing some tough choices around prioritization because some of the swim lanes that had traditionally been available were suddenly un-funded, but the need for progress in those areas remains. In retrospect on the planning activities, it was mentioned that the teams felt that they were being asked to generate too many different permutations of 230 plans. In an Agile environment, the business needs engineering to provide options to choose from, and we believe that our degree of precision to give those alternatives to the business requires too much detailed work from the teams. Said simply: the business needs engineering to be able to quickly assess many different ideas rapidly in order to be able to evaluate the best path to pursue.

This proposal is to create a lighter-weight process around sizing *during the early phase of the planning process* that does not give the illusion of precision, but that gives an accuracy that is acceptable to the business to help make key decisions earlier without requiring a lot of effort from engineering to produce. This way the business might ask engineering to evaluate a number of different options and choose which one to pursue with better data while avoiding the churn the teams felt during 230 planning. 

### Precision vs Accuracy

When working at this phase, Accuracy is much more important than Precision. Having a wide range is perfectly acceptable - widening the range indicates to the business that there is uncertainty and risk in our estimation process. However it defines the bounds in which an outcome can be expected and enables the business to make prioritization decisions.

We should not be afraid to take information and make low-confidence estimates that clearly indicate the risk of being wrong (by widening the range) with short time horizons to think about the details. This exercise is at the heart of good Agile planning.  
[Image: PrecisionVsAccuracy2.png]
### Under Pressure

One of the possible reasons we seek precision in our current model is that we give ourselves too much time to think about it. We research and plan and things start to solidify. Then the business changes its mind and we start all over - lots of work wasted planning things we don’t work on. Instead of hoping that the business will stop trying to be Agile, we should lean in and embrace a simple fact: no matter what we do in estimation, it is inherently wrong. Just by accepting the fact that we cannot possibly be right, we free ourselves of some burdens. 

But you might say “we already knew this”. This proposal would say that we lean into the fact we are wrong, and use time boxing to give ourselves the amount of time we think is right to get to the level of accuracy we care about: very rough buckets and not worry too much about being more precise than ‘in the range’.

### SWAG?

Apparently by calling it a SWAG, not everyone knows that it stands for Silly Wild-Assed Guess and think it is synonymous with ‘accurate estimate’. The point here is to convey with the Boston-prounounciation of ‘super’ (soo-pah!) that these guesses are extra silly and extra wild. 

## Soopah-SWAG

A release plan is the result of T-Shirt Size which typically involves some whole-team estimation by the scrum teams. In order to avoid confusion, Soopah-SWAGs will not use the same language and will be a range as opposed to a singular value. By using different language we can avoid confusion about which phase of estimation the project/initiative is currently in. By using a range of values we can widen the range to indicate uncertainty. 

Here is the proposed chart for Soopah-SWAGing at the early planning phase (see [here](https://salesforce.quip.com/oVtxAKKWDiFh#HORACAew2Tn) for the t-shirt sizing table we use for release planning during the bottom up / team planning phase)

|Complexity To Build	|Person Sprint Range	|Emoji	|SWAG	|
|---	|---	|---	|---	|
|Skateboard	|0 - 5	|🛹	|Skateboard	|
|---	|---	|---	|---	|
|Bicycle	|3 - 15	|🚲	|Bicycle	|
|Car	|12 - 30	|🚗	|Car	|
|Bus	|25 - 50	|🚌	|Bus	|
|Truck	|35 - 80	|🚚	|Truck	|
|Train	|50 - 125	|🚃	|Train	|
|Airplane	|100 - 250	|✈️	|Airplane	|
|UFO	|???????????????	|👽	|UFO	|

### Process

The proposal would involve convening a **time limited** meeting between **the Director of Engineering, the PM, and the Architects & PMTSs** who would be working on the proposed initiative.  The PM would prepare a 1-Pager about the initiative or key deliverables within a initiative. 

This “Soopah-SWAG” team would read the 1-Pagers before the meeting, and then would come prepared with clarifying questions. At the bottom of the 1-Pager the team should add a notes section. In this section should be recorded all questions, their answers, and also an explicit list of the relevant assumptions that the engineering team are making while they Soopah-SWAG this initiative. We write these down for two purposes - first to establish a shared understanding among the team working to do the Soopah-SWAGing in clear black and white with no ambiguity about what is being agreed two, and secondly so that others who were not present can read and understand the context in which the assumptions were made. 

Lastly the team should agree to a bucket that this initiative fits into. We don’t need to have a precision, just to get into the right bucket. The focus of this exercise is to stay time boxed. If we go too deep we start to believe that we know the right answer. We don’t. This means that we should time limit this exercise to 30-60 minutes per initiative we want to define. This way we can try out different alternatives without spending a great deal of time. 

### Expectations

We do not expect that this process will yield identical results when we get to team-estimation (t-shirt sizing) for release planning. **No commitments** will be made from these estimates. This exercise is to quickly iterate on potential combinations of plans ahead of release planning to minimize throw-away work during the planning phase. While we might examine our Soopah-SWAGs versus our t-shirt sizes in order to improve our process, we do not want anyone to believe that the Soopah-SWAG is precise and the t-shirt size will still be what is used for the release commitment — this really is just to help the business decide which themes to pursue in a release.






