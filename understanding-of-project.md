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