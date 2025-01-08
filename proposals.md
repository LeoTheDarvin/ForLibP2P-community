###### All proposals are based on my experience and [understanding of the project](./understanding-of-project.md)
###### The proposals are intended to make implementation process[(levels 3b and 4)](./understanding-of-project.md#structure-of-common-knowledge) more [enjoying for developers](./understanding-of-project.md#motivation-of-a-contributor-or-what-wedevelopers-could-want) improving communication. 
###### The most demanding to cohesion of community proposals are listed first
### Test suites in docker-images:
#### Profit - X-language tests reuse should save lots of human-hours
#### Price - extra efforts on test suites standardization, docker setup, LibP2P run setup
#### Implementation
- LibP2P partial run setup(no need to run potentially heavy switch)
- tests cases must hit implementations via network adapter(not via internal call)
- need a docker configuration to run a test suite
- we mustn't make docker understanding commonly demanded for [inclusivity](./understanding-of-project.md#inclusivity) considerations. There must be a way to run the same test suite as in lang-native way as bundling it into a docker-image.
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
- decreases implementation([level 4](./understanding-of-project.md#structure-of-common-knowledge)) contribution threshold
- predicts problem of modules([LibP2P is modular by the way](https://docs.libp2p.io/)) compatibility
#### Price:
- deep understanding of whole the stack principles
- negotiation on **_seed module_** 
#### Implementation
Early decoupling supposes starting development from extraction of [implementation level](./understanding-of-project.md#structure-of-common-knowledge) **_root abstractions_** to **_seed modules_**. 

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
