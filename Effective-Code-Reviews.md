# More Effective Code Reviews

## Why do we do code reviews?

Code Reviews can serve multiple purposes for a team. Primarily they are to help us find defects early in the software lifecycle and fix them fast - before they have a chance to get out into the wild and impact our customers. Code reviews should be focused on finding defects, but they have other side effects that are beneficial to teams and should not be overlooked.

By formalizing the code review process, a team can ensure that multiple members in the team are familiar with the code being built, helping to reduce single points of failure. Good code reviews often will trigger discussions and reevaluations of design choices and structuring. They also provide a great opportunity for senior engineers to provide mentorship to more junior engineers, and for new ideas to spread in the team. 

In short, an effective code review process can give teams a great intellectual boost in addition to the usual defect reduction aspect that pays dividends on the overall team performance.

## Expectations

The code review process is a team based process. We should treat our teammates with respect - no matter who is right and who is wrong about a given piece of code or problem. We should engage open to learning - from both sides - and we should communicate in ways that avoid making criticism personal. Our shared purpose is better software - stay focused on that. Assume best intent in comments and responses. 

## Responsibilities of a submitter

Submitters should respect the time of their peers. Before submitting code for review, they should first ensure that they have done their own due diligence:

* all required lint-checking has already run and heeded
* completed a self-review of the code 
* commit and code comments are sensible and useful and relevant for setting context of the code
* code is coherent & self-contained - it should contain exactly a single unit in a single PR
* include links to relevant design documents to help set context
* mentally prepare to listen to and learn from the reviewers
* acknowledge all comments in writing so the reviewer understands their feedback was heard, and be clear about intended actions as a result of this feedback

## Responsibilities of a reviewer

Reviewers should recognize that they are inherently in a position of responsibility. While we believe that engineers at all levels should be reviewers - even entry level - they should take this responsibility seriously. While reviewing, the reviewer should keep the following in mind:

* take the time to review it right
* devote undivided attention or the benefit is lost
* recognize that there are many ways to do something right - different than the reviewer would have done is not wrong
* favor asking questions when uncertain of intention
* treat the author with respect
* make feedback polite, specific, and actionable
* provide feedback promptly - even if just do say “I cannot get to that today”

## Tips for more effective reviews

### Understand the context

Reviewers should understand the context in which the code is being written. This means reading the comments and design documents that the author provides. It means asking questions of the author to ensure understanding. It means asking around the edges of the problem to ensure there is shared understanding about exactly the problem being solved and the solution both. It is not just about code - it is about the software construction process.

### Enforce Coherence

When the same PR contains many different mini-features it can become very confusing. Each PR should stand on its own, and reviewers should reject PRs who try to combine multiple concerns. 

### Start and finish with tests

Many people overlook reviewing the tests, but by starting with the tests, a reviewer can gain greater understanding of the intention of the code they are about to review. Once the code has been reviewed, by re-reviewing the tests, the reviewer can give feedback on missed edge cases and other ideas to improve the coverage and effectiveness of the tests.

### Focus on substance not style

Finding defects in the code is our goal, not arguing holy wars about minor pieces of personal preference that do nothing to affect the quality of the code. Anything that is stylistic, try to put into the checkstyle/lint configurations and treat checkstyle violations as a broken build. 

The advantage here is that this frees the reviewers of the distractions around style which can hide the more thoughtful and important discussions around defects. By taking this class of comments off the table early, it ensures that the comments being made by the reviewers are of a greater level of criticality.

### Keep a living team review checklist

Each team should keep a checklist of common problems they have experienced. All reviewers should use the same checklist, though they should not limit themselves to the checklist - it is a tool to help reviewers think and remember not shackles to limit their thinking. Periodically this team should review the checklist and add new common mistakes, and remove ones that the team are no longer seeing. 

### Automate common mistakes

To keep the checklist from getting too long try to automate checks for common mistakes. By moving these to static analysis phase the team can drive the defects out right from coding time rather than waiting for review time. Embrace the power of automation, even in your code review process.

### Communicate clearly

Reviewers must be clear and explicit in their comments. They should provide usable feedback, not general statements. Actionable comments lead to actions by the authors. It should also be polite and factual - keep it professional. Authors should read the reviewers comments and assume best intent - reviewers are often operating under time constraints and may be short in their comments.

Likewise authors must be clear in their responses to comments - they must clearly indicate their plan of action for each comment. One common method for ensuring clarity in intent is to adopt a formal tagging language on comments - prefix the comments using language adopted from the [MoSCoW Method](https://en.wikipedia.org/wiki/MoSCoW_method) for requirements - Must Do, Should Do, FYI and of course the negations - Must Not Do, Should Not Do.

Everyone should ask each other questions throughout the process - this is a team process, not an individual one.

### Go face to face fast

When there is any doubt or lack of clarity - go to live chat, video conference, or in person. This is a human process and it is easy to fall into the trap of “talking through tools” - instead when questions arise that cannot be answered in a single exchange, favor direct communications immediately to clear up confusion. 

### Avoid code overload

Code reviewing is a mentally intensive activity. Do not try to do more than a couple of hundred lines of code in a single sitting as studies have shown that effectiveness of review drops after an about an hour and about 200 lines of code in the same review. Ideally authors submit small PRs hidden behind feature switches so that code can be merged early and often and avoid mega-merges of a thousand lines. 

### Embrace rejection

Sometimes PRs can sit in an open state because no reviewer wants to approve it, but no one is willing to tell the author that. Rejecting a PR should not be taken personally - it should be our default operation for safety. A rejection sends a clear message to the author that the code is unacceptable as is and needs work. Open PRs with tons of comments can be ambiguous. 

## Spirit

Just remember - the spirit of the code review should be one of learning, sharing, growing, and helping each other build better software. Keep these goals in mind as you go through the process.


