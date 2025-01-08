###### Here I'll try to understand some common([level 3](./understanding-of-project.md#structure-of-common-knowledge)) technical aspects of LibP2P.</br> It's not a pure aggregation of what's already documented but a try develop the domain grounding on my sense of common ideas, documented knowledge and wisdom of ChatGPT.</br> All content is highly subjective and demanding to [critical attitude](./README.md#disclaimer)

# Considerations in development: 
- goal - abstractions system
- must serve domain of **modular P2P networking stack** and only this domain
- must not be bond to any lang API 
- must cover all processes and protocols within LibP2P 
- must be as simple as possible
- must consider extension sufficient to cover all demands with implementations

# Principles of negotiation: 
- initiator offer options and declare own preferences
- responder makes choice
- open offer. Initiator should announce all acceptable options at once

# Stream
###### Stream is well [specified from user side](https://docs.libp2p.io/concepts/fundamentals/protocols/#binary-streams) for now. But how about initialization side?
###### Stream must support both half-close by output and full close
## Upgrade
###### Let describe stream upgrading in terms of a pipeline
### Goals
###### Every goal could be addressed by different pipes(protocols)
- reliability
- ordering
- flow control
- encryption
- fast connection recovery
- DoS tolerance
- multiplexing
- peer authentication 
- backpressure
- compression
### Pipe
Pipe is a piece of stream with an instance of a [**protocol**](https://docs.libp2p.io/concepts/fundamentals/protocols/#what-is-a-libp2p-protocol) implementation mounted.
</br>Pipe could serve one or several [**goals**](#goals).
</br>Pipe might have one **descend** stream - where data is represented more like transport need.
</br>And several **ascend** streams - where data is more like application need.
</br>Each **descend** is attachable to any **ascend**.
</br>Pipe is stateful.
</br>All intermediary pipes work in pull-mode transferring and processing data on-demand.
</br>Pipes encapsulate all complexities of message-based processing accumulating required data volumes on entrance. Each pipe must know own buffer size requirements
</br>Processes asynchronously and in non-blocking way.
#### Handshake
Handshake is optional. Consists of serial of ping-pong-ping-... turns.
</br>Turns transfer the pipe related data via descend
#### Transmission
Transmit data as is by default. Starts immediately after handshake termination.
</br>Handles input and output sub-streams asynchronously to each-other.
</br>Could apply a complimentary transformations to input and output sub-streams.
### Pipeline
#### Topology
###### Free descends or/and ascends are forbidden.
- common root(one ascend) - transport
- some direct intermediary(one descend, one ascend) - upgrades except multiplexing
- some branch intermediary(one descend, any amount of ascends) - multiplexing
- some leafs(one descend) - applications
#### Building 
Pipelines builds incrementally from the root to leafs.
</br>Pipeline cannot be modified, only destroyed.
</br>Pipeline increment could be configured as a sequence of pipe types(protocols).
</br>Configuration could be predefined(via multiaddress or relayed-stream) or auto-negotiated via a growth-point-pipe(multistream-select).
</br>Every configured sequence of pipes not ending with a leafs(application pipe) gets automatically enhanced with a growth-point.

# Switch
###### To beat complexities of swithch I'll follow high-to-low level decomposition principle
## User API
### Initialization
- peer keys 
- bootstrap multiaddresses
- all kinds of modules - transport, upgrader, multiplexer, application(stream codec, client, server), modules for advanced mechanics(like peers scoring or NAT traversal)
- start/stop
### Use
#### Consumption support 
One responsibility - one use, dial.
</br>While use is single it must be flexible enough yet. 

Only essential parameter is protocol and only response is client for the protocol.
As for optional it could be a peer or black/white list of peers to serve the protocol.
#### Service control
In general user should be free to decide: 
- what connection to accept
- allow or forbid serving peer over a protocol
- how much resources could every peer consume

## Responsibilities
### Basic
- **routing** - analyzing multiaddresses
- **peers discovery** - by id or protocol service
- **tracking serving** - connections and protocols access. Needed for service control user API
- **hot transport switch** - feature essential for seamless switch from relayed transport to holepunched.
### Advanced(out of scope but must have API for external implementation)
##### PubSub
##### Coordination of multi-peer complex scenarios(alike NAT-traversal)
##### Monitoring: 
- strange behavior: protocol violation, connection disrupts, flooding
- traffic - timestamp, data amount, target peer, cutpoint(pipe type, ascend or descend), service or consumption
##### Maintaining consumption-serving balance
##### Scoring peers to set limits in collaboration

## TODO: Developer API 
- protocol modules - introduces pipe creators by protocol id 
- address resolver - suggests multiaddresses where a peer could likely be reached
- reactive environment - a listenable context to track and advice all-over mechanics [under the hood](#responsibilities). Seems to be only a way to keep peers both responsive and extensible.




