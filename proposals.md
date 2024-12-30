# My newcomer's the first semi emotional overview
### What important I've found here
- wide community with a public hub
- ambitious mission - creating a modular p2p networking protocols stack
- experience of success - ipfs
- robustly and simply defined customer abstraction layer serving p2p goals: stream, multiaddress, protocolId format
- fine documentation
- developed protocols with **SPECIFICATION**!!!

### What I'm missing here: 
- **entry point** into development process. I'd like to write something modular supplementing enormously complex p2p world network. Unfortunately a well defined extension point is out the existing implementation's scope(`Java` of course)
- I believe in power of p2p but seeing it as a log running in console is something enjoying and encouraging
- **roadmap** with relevant progress is not a matter of bare curiosity. But it's something saving your time when you look for a topic of contribution or trying to reuse existing development. Of course, I was happy to see a roadmap representation over there(https://libp2p.io/implementations/) but without a comprehensive Definition Of Done with a references to documentation(or/and specification) is just an enjoying picture.
- comprehensive digest of the [switch](https://docs.libp2p.io/concepts/multiplex/switch/) functionality and it's user interface. 
- **conflicts**, how not to be strange. When people do something common they cannot stay 100% agreeable. Are we doing the same LibP2P? 

### Summarising
LibP2P development(standardization, implementation, testing, releasing) process is not established well enough(at least for `Java`)

# My analytics. Or important considerations

## What're special features of the proj
### Volunteers-driven
#### advantages
- no "time doers" and "formal performers". Every one is proactive and creative
- you do what you want to do. Free to find the best application for your abilities
- you're the one who judge and introdce proposals over what others're doing
#### challenges
- only a way to guarantee something will get done is doing it by yourself
- standardization. No central decision maker whereas public negotiation of everything is a boring and time-consumptive and normally useless swamp
- new paradigm of thinking which I call **_decentralized source of truth_**. None solution is true or false it's just more or less accepted in community but never 100% or 0%

### Community language-based segregation
#### advantages
- its't a chance to eventually resolve argument "What lang is better")
#### challenges
- achieving both X-language experience reuse and absence of noise about other lang's internal problems

## Motivation of a contributor. Or what we(developers) could want
- Develop something will come in handy to lots of people. Use other's contributions
- Stay free to research only topics you keen on. Stay free from learning too much(whether it's an ugly specification or even more ugly code)
- write once in CV something like "experienced DApps developer and originator of THE P2P networking stack"

## Structure of common knowledge
###### TODO: enrich level description with: preceptors, acceptors, share example, function
* **level 1** - goals resolution
* **level 2** - abstractions
* **level 3** - X-language implementation details:
  * **a**. peer-to-peer integration
  * **b**. a peer insides(including [switch](https://docs.libp2p.io/concepts/multiplex/switch/))
* **level 4** - language-specific implementations
##### The higher level of knowledge the the more people criticising and relying on it
##### Absence of communication on any of levels above stops the project's general progress. So it's important balance activity on all levels
##### As for my estimation last topic levels 3b and 4(in `Java` at least) sucks for now.
	
## Solution
###### Of course a good solution is a solution widely accepted over the community and I cannot just introduce something like that. Here I'll just highlight some aspects of a good solutions to be addressed somehow:
### Inclusivity
How our community is powerful is directly dependent on how it's attractive.
Inclusivity is up to consider in two extents: 
- [for developers](#motivation-of-a-contributor-or-what-wedevelopers-could-want)
- for users:
  - a. how LibP2P's API intuitive in use and documented
  - how LibP2P gets along with public networks(node to DPI and NAT issues)
### Negotiation system
In absence of [central authority](#challenges-1) decision-making must be:
- decentralized
- transparent
- inclusive(low participation threshold)
- naturally fair(the higher contribution - the higher influence)
  

# My proposals
###### The proposals are intended to make implementation process[(levels 3b and 4)](#structure-of-common-knowledge) more [enjoying for developers](#motivation-of-a-contributor-or-what-wedevelopers-could-want) improving communication. 
###### The most demanding to cohesion of community proposals are listed first
### Test suites in docker-images:
#### Profit - X-language tests reuse should save lots of human-hours
#### Price - extra efforts on test suites standardization, docker setup, LibP2P run setup
#### Implementation
- LibP2P partial run setup(no need to run potentially heavy switch)
- tests cases must hit implementations via network adapter(not via internal call)
- need a docker configuration to run a test suite
- we mustn't make docker understanding commonly demanded for [inclusivity](#inclusivity) considerations. There must be a way to run the same test suite as in lang-native way as bundling it into a docker-image.
</br></br></br>
### Open Definition Of Done section
#### Profit
- transparent completeness rate
- improves code compliance to specification and common(or lang-specific) programming principles and contracts
- higher chance to acceptance for your code/specification
- chance to resume progress within a module without full rollback of the previous contributor's developments
#### Price - attention to DOD section in repository as from code as from specification writers
#### Implementation
Two-columned, row-by-feature DOD section in README. </br>
1st - short description & references to specs. </br>
2nd - use instruction & reference to implementation
</br></br></br>
### Early decoupling:
#### Profit
- decreases implementation([level 4](#structure-of-common-knowledge)) contribution threshold
- predicts problem of modules([LibP2P is modular by the way](https://docs.libp2p.io/)) compatibility
#### Price:
- deep understanding of whole the stack principles
- negotiation on **_seed module_** 
#### Implementation
Early decoupling supposes starting development from extraction of [implementation level](#structure-of-common-knowledge) **_root abstractions_** to **_seed modules_**. 

**_Seed modules_** must contain minimal synchronization essentials as so: 
- root interfaces with exhausthing documentation
- README with agreements to be implemented in all dependencies

_**Root abstractions**_ suggestion:
- [stream](https://docs.libp2p.io/concepts/fundamentals/protocols/#binary-streams) abstraction it the best fit to decouple protocol handlers with each other and with switch
- [switch](https://docs.libp2p.io/concepts/multiplex/switch/) is complex internally, hence its implementation should be decoupled too. But how?... Need research
</br></br></br>
### Git branch-based conflicts negotiation and acceptance rating
###### Profitability of the proposal depends on number of actors within the same module
#### Profit
- enables negotiated standardization
- transparent rating of acceptance in community
- encourages mutual revision - good for quality
#### Price
- initial repository setup 
- learning new(simple enough but nevertheless) branching system(`develop` and `master` will be deprecated)
- mutual revision is naturally enforced
#### Implementation
- we remove central branches(eg `main`, `master`, `develop`) or leave them to a repo admin for technical setup. 
- every created by a user branch becomes own. This means full control of an owner over branch. Whereas read-only access for non-owners.
- such setup makes every participant care of acceptance of own contribution. To increase acceptance, contributor could PullRequest to other contributor's branch. Hence, everybody get naturally engaged in standardization and code quality check. Nobody need mess in own branch.
- such setup makes possible a **theft**. You know, when someone overrides your signature in **git blame**. And this is not a matter of pure ambition. **Git blame** is a convenient tool to spoil it with **thefts**. Fortunately the problem is easy to mitigate with "Our honorable thieves" section in README to expose **theft**-engaged branches and commits.
- (optional)For matter of git history transparency. It would be fine to restrict branches amount per user. Setup rule one branch - one new commit(which belong to only one branch). 
</br></br></br>
### Language-based discussion partitioning: 
#### Profit 
- extracting commonly usable knowledge from lang-specific simplifies its sharing
- ease of a lang-based subcommunity addressing
#### Price and Implementation is lang-based sub-partitioning of [contributor's](https://discuss.libp2p.io/c/contributors/6) section. 
