# Context Mapping Process

Conway’s Law (https://en.wikipedia.org/wiki/Conway%27s_law) was first cited in 1967 and has endured as a truism of computer engineering — how we are organized to communicate will dictate how we work and what our end product is to customers. It is because of this that every few years we need to check our navigation against the north star - are we organizing the way we want our architecture to evolve? Are responsibilities properly balanced and resourced relative to their importance to the business? Almost inevitably the answer will be a resounding ‘no’ and we will seek to make adjustments. The Context Map provides us with a framework for decision making.

Historically most engineering organizations used a Functional Decomposition (https://sourcemaking.com/antipatterns/functional-decomposition) to their organizations — that is to say that they organized around distinct layered job roles that optimized for specialization at their independent layers. This stratification led to layouts that were very focused on taking a piece of work and moving it through the different roles. 

In our organization we seek to create teams that have greater cross functional natures and that are able to independently own the Domains (https://en.wikipedia.org/wiki/Domain-driven_design) of what they build from ideation through to production. While others might have a role in helping or mediating, we view the “Domain Teams” as owning the solutions while the other teams are centers of excellence providing tools, best practices, and checks & balances. This has been shown to lead to better overall customer outcomes in numerous companies and is generally viewed as a well accepted technique. 

Some critical concepts (https://codeburst.io/ddd-strategic-patterns-how-to-define-bounded-contexts-2dc70927976e) everyone should know:

* *Domain*: a set of tightly related business problems to be solved 
* *Bounded Context*: a logical grouping of related Domains
* *Category*: a set of related Bounded Contexts that have affinity 

Our goal is to unearth and group together Domains, into Bounded Contexts and then assign ownership of Bounded Contexts to a scrum team. This effectively says “This team is empowered to solve these business problems”. By grouping the alignment of the teams around business problems instead of around technology layers, we empower the teams to work more independently. 

Principles of Organization

1. One Team owns N Bounded Contexts FULLY - no shared ownership
    1. Promotes Autonomous Teams
    2. Minimizes Cross-team Dependencies
    3. Shared ownership of a Context can lead to divergence of solutions that will later cause us to struggle to converge and create greater long term costs for the business
2. No Unowned Things, No Nominally Owned Things
    1. A team is autonomous to choose their own level of what to invest, but leadership must not be enabling bad behavior by referring to things as ‘nominally’ owned. What would we tell our customers if those areas failed? That we gave teams permission not to own what we have already built? 
    2. All unowned/nominally owned things should simply be deleted - if we don’t care enough to support them we are just asking for trouble. 
3. Target Teams Size 6-8
    1. Smaller teams are poor service owners by definition
    2. Prefer larger teams with multiple responsibilities over smaller teams with single responsibility to avoid peanut buttering across many projects because we ‘seem’ to have more teams than we really do
4. Establish Clarity of Purpose
    1. Teams can show greater ability to counter propose plans when they understand their scope
    2. Teams can plan new adjacent ideas when they understand their boundaries
5. Equitable Balance of Leadership
    1. Our key leaders should have an equitable workload. While some might manage more teams and some might manage more processes, the workload needs to be fairly distributed across the leadership team as well as the scrum teams

