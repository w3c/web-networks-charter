# Why is there a need for more network/app collaboration?
Networking technologies are going through a series of transformations aiming at making them more performant, more programmable and adaptable:
* improved and configurable latency (QUIC, MEC, network slicing, LoLa),
* aggregated network paths (MPTCP, dual connectivity, multi-homing),
* adapative congestion control (mobile throughput guidance via MEC, machine learning).

Meanwhile, more and more network traffic is encrypted end-to-end to match the increased stakes on end users security and privacy of a networked society. This positve development also means that network operators have ever fewer ways to know on their own the kind of traffic they're transporting, making it hard or impossible to make use of these latest evolutions without explicit collaboration from flows endpoints.

# Why wasn't it done before?

Historically, it has proven hard to establish a cooperative approach between the application and network layers due to the following obstables:
* the abstract layering of the various components needed to build and deploy networks and applications discourages one layer integrating too deeply into another one; at the structural level, this layering is often reflected in split of standardization efforts across different organizations for the different levels (e.g. W3C for applications, IETF for transport, 3GPP and ETSI for cellular networks)
* network operators are reluctant to give control on the operations of the network to the application layer since this would expose the network to abuse (e.g. where every application provider would assume their own traffic requires the highest bandwidth and the lower latency)
* application providers are accountable to the privacy and security of the data their users entrust with them and need to control the boundaries of how that data is shared and transported
* trust mechanisms that would allow more collaboration between application and networks are hard to make relevant to the scale of the Web where so many different application and network providers may be involved; smaller scale coordination mechanisms may not be workable in many legal environments (e.g. due to their intersection with network neutrality directives).

# Why now?

We think a combination of factors make solving this cooperation conundrum more critcal today, creating an opportunity to make another attempt to establish novel processes to that end:
* new major network investments (e.g. for 5G) are hard to justify if these investments can't be clearly identified as perceivable improvements in usage of networked applications,
* a lot of network improvements have historically been severely reduced by accidental or intentional lack of collaboration between apps and network (e.g. lack of adoption of QoS capabilities),
* a number of the next wave of network technologies are reaching limits imposed by law of physics, making the hope that technology evolution on its own will suffice at hiding these lack of progress over time less realistic,
* network operators attempts at doing network managememnt in the blind in the face of increasing encryption are coming to a limit, pointing to an increased cost of operating current networks, independently of any deployment of new network technologies,
* many developments on the application side points toward needs of better control of network behavior, either as improvements to the overall user experience (where e.g. additional delay in responding to user interactions can be directly translated in terms of loss of business), or in a growing number of cases, as critical aspects of deployment of these new applications (streamed AR and VR, 8K / higher-color video streaming, immersive real-time communications, telepresence, real-time distributed machine learning, …).

# What has changed compared to previous attempts in this space?

Lessons learned from previous attempts at improving the cooperation between network and applications point toward a possible framework to remove or reduce the barriers identified for such a cooperation:
* while layering remains an important overall approach to architect the internet, that layering has never been intended to be strictly enforced (as illustrated by [“layering considered harmful in RFC3439”](https://tools.ietf.org/html/rfc3439#section-3)), and recent developments have shown the value of allowing cross-layer interventions (e.g. WebRTC control of network topology and firewall piercing); we believe a more coordinated approach at managing these cross-layer interventions would prove beneficial to their pace and their suitability to the overall ecosystem, and that in particular, more coordination across the various involved standards organizations would help defining shared priorities and clarifying which use cases and requirements are most likely to effect an impact
* rather than expecting either network and application providers to relinquish control, or waiting for a Web-scale trust mechanism to emerge for such a collaboration, we believe identifying opportunities where applications benefit from communicating their intent to the network (e.g. through hints) and vice versa where both sides would benefit from the exchange, and no side would be likely to gain from misbehaving offer a good way to anchor work on such a collaborative framework in the short term.
* we believe taking a privacy-by-design approach in defining and scoping any opportunity for this cross-layer collaboation will help reduce the legitimate concerns that have been raised both by network and application providers in sharing information; in particular, we believe data minimization and aggregation techniques can help reduce or alleviate these concerns.
* making the results of any such collaboration more transparent and auditable would help both paving the way for more collaboration opportunities, and ensuring these collaborations remain in-line with an overall positve impact on the internet ecosystem

# Specific network/app collaboration opportunities

A few specific opportunities fitting the above criteria have been identified looking at recent examples of proprietary or small-scale network/application coordination.

## MPTCP, dual connectivity

## Latency Loss Tradeoff (LLT) - This particular proposal (https://www.ietf.org/archive/id/draft-you-tsvwg-latency-loss-tradeoff-00.txt) allows the application to request treament for either low-loss or low latency flows at a congested link. It attempts to address common challenges with resource allocation (buffers and bandwidth) for application flows with different requirements and traffic characteristics. The technique used in this proposal is by creating two different classes of service: a low-loss service (Lo) and a low-latency service (La). The packets marked as low-latency service receive lower queuing delay where the packets marked as low-loss service receive at least as much throughput as they would in a legacy best effort network. La-marked packets are more likely to be dropped during periods of congestion than the Lo-marked packets. While this technique uses existing QoS mechanisms it does not prioritize one over the other and as a result it provides no incentive for the application to miss-categorize flows.
The Latency Loss Tradeoff proposal covers the IP level mechanism to mark the packets but it does not go into the specific details about how the application would convey the Lo/La to the lower network stack.
The opportunity is to identify the API requirements for web based applications and content creators to provide the hints for content classification.

# Web & Network Interest Group

We believe a W3C Interest Group (with a working name of "Web & Networks") could provide a useful forum to push this collaboration agenda further; such a group, modeled after the Media & Entertainment Interest Group would:
* develop and maintain a list of relevant activities in the network/application collaboration space, in both proprietary and standard ecosystems,
* identify opportunities for network and app collaborations that seem likely good candidates for adoption, analyse them in relation to existing standardization efforts, and when relevant, build the case for additional or prioritized standardization,
* actively liaise and coordinate with relevant standards organizations (esp. 3GPP, IETF) to keep track of their relevant activities, to identify and when possible, help lift obstacles they may be facing, and to ensure they're provided with a cohesive understanding of use cases and requirements coming from Web applications.

## Interest Group deliverables

Practically speaking, we would expect the Interest Group:
* to organize monthly calls, each on a specific in-scope topic, often with external presenters (from other W3C groups, from other SDOs, from relevant proprietary or open-source efforts),
* to maintain a roadmap of specific technical opportunities for greater network/app cooperation, reviewing them for their chances of success given lessons learnt from past successful and failed attempts, mapping them to ongoing standardization efforts (if any), keeping track of their chain of dependencies and identifying obstacles to their progress and plans for lifting them,
* to develop use cases and requirements emerging from Web applications needs in terms of network that cannot be addressed with the current set of standardized network interactions,
* to maintain a list of relevant groups and contacts in other standard organizations (esp. 3GPP, IETF), consortia and software projects, and a plan of communication and liason with them.

## Expected participants

**Network operators** have clear needs in improving their ability to manage networks, reducing the cost and improving the performance for their subscribers. They have the means to push for the operational adoption of changes, and the understanding of the technical and economic constraints in defining them.

**Network equipment providers** can translate the changes that need to percolate through the network chain in terms of standards and products roadmaps, and shed light on the technical and economic constraints in getting them deployed.

**Network measurements providers** can help identify which metrics are readily available to applications and network providers, identify opportunities on when and how these metrics might benefit from being shared across layers, and define frameworks that enable operational accountability in network/app collaboration.

**OS vendors** and **browser vendors** determine what features (incl. networking APIs) get exposed to application developers on end-user devices and how they are gated for access. Similarly, **cloud and edge providers** provide these capabilities on the server-side.

**Application providers** (esp. those with a high degree of sensitivity to network conditions, e.g. media content providers) have domain-specific and business-specific requirements in how they wish they could get the best performances out of the underlying networks to satisfy the need from their users.
