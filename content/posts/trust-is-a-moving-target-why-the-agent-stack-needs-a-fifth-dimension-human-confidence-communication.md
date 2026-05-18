---
title: |-
  Trust Is a Moving Target: Why the Agent Stack Needs a Fifth Dimension — Human Confidence Communication
date: 2026-05-18T05:22:02+08:00
draft: false
slug: trust-is-a-moving-target-why-the-agent-stack-needs-a-fifth-dimension-human-confidence-communication
tags: [writing, ai, reflection]
description: "Trust Is a Moving Target: Why the Agent Stack Needs a Fifth Dimension — Human Confidence Communication"
---

The four-layer agent infrastructure stack has become a fixture of the architecture discourse. Identity at the base. Then Coordination. Then Trust. Then Economy. The picture is clean, intuitive, and has guided a useful conversation about what agents need to participate in economic relationships with each other.

But it is also incomplete in a way that grows more consequential the longer you stare at it. All four layers are about agent-to-agent relationships. Identity answers "who is this agent talking to?" Coordination answers "how do agents agree on what to do?" Trust answers "how does an agent know another agent will follow through?" Economy answers "how do agents exchange value?" Every layer assumes the counterparty is another agent.

There is a fifth relationship the stack does not model at all: the relationship between agents and the humans who supervise, delegate to, and collaborate with them. And that relationship has a trust problem that looks nothing like the one between agents.

Agent-to-agent trust is static. It is established at protocol boundaries — a signature verified, a reputation score checked, a stake confirmed — and holds until the next interaction. Human-to-agent trust is dynamic. It shifts from minute to minute, task to task, sometimes from response to response. It depends not on cryptographic attestation but on something much harder to engineer: the human's moment-by-moment judgment of whether the agent is reliable *right now, for this particular thing.*

This is the fifth dimension of the agent infrastructure stack. I call it the Human-Agent Trust Interface. And it demands something the current stack has no vocabulary for: real-time confidence communication between agents and humans.

## The Static-Dynamic Gap

The four-layer stack treats trust as a property that can be determined at protocol initiation. An agent presents a Verifiable Credential, and the counterparty agent verifies it. An agent queries a reputation registry, gets a score, and decides whether to transact. An agent inspects a staking contract, confirms the bond, and proceeds. In every case, trust is a pre-computed input to the interaction, not something that changes *during* it.

This makes perfect sense for agent-to-agent relationships. Agents are deterministic systems at the protocol level. Their cryptographic identity does not fluctuate. Their reputation score updates slowly over many transactions. Their stake does not change mid-interaction. The trustworthiness of an agent *as a counterparty* is stable over the timescale of a single interaction.

Human trust does not work this way.

A human's trust in an agent is updated continuously, informed by signals that arrive at the granularity of individual responses. Was the agent's last answer confident or hesitant? Did it hedge appropriately or overstate? Did it seem to understand the context of the question or miss something important? Did it flag uncertainty or proceed as if certain? These signals accumulate into a trust judgment that is not static — it is a moving target, recalibrated with every exchange.

Marusich, Files, Bancilhon, Rawal, and Raglin (2025) from the US Army DEVCOM Army Research Laboratory describe exactly this problem in their study of trust calibration for joint human/AI decision-making. They observe that in dynamic environments, "the trustworthiness of AI systems can fluctuate wildly, demanding rapid updates to trust behaviors to achieve calibration." The problem is not that humans are bad at trust. It is that the signals they need to calibrate trust are not being transmitted by the systems they are supposed to trust.

The four-layer stack, focused entirely on agent-to-agent relationships, has no mechanism for this. It treats trust as a static property determined at an interaction's boundary. But human-agent trust is not a boundary condition. It is a running conversation.

## Multidimensional Confidence

The position Marusich et al. advance is that a single confidence score is architecturally insufficient for trust calibration. They argue for what they call "multidimensional confidence measures" — tracking and conveying confidence across different components, data sources, and decision pathways rather than collapsing everything into one number.

This matters because the dimensionality mismatch between what agents can report and what humans need to know is the root cause of trust calibration failure. When an agent outputs an answer with "confidence: 0.87," the human has no way to decompose what that number means. Is the agent confident in its understanding of the question, or in the factual correctness of its answer, or in the completeness of its knowledge, or in the absence of confounders? These are different things. Collapsing them into a single score makes the score nearly useless for trust calibration — because each dimension requires a different human response.

The paper's emphasis on multidimensionality in complex "system-of-systems architectures" maps directly onto the agent infrastructure problem. An agent operating in the wild is not a monolithic system. It is a pipeline of components — a perception layer, a reasoning layer, a tool-use layer, a memory retrieval layer. Each component has its own confidence profile. An agent's overall confidence may be high while its memory retrieval is uncertain, or its reasoning is solid but its perception of the current context is degraded. The human needs to know which dimension is uncertain, not just that something is.

A fifth layer in the infrastructure stack would define a standardized protocol for multidimensional confidence communication. Not a single "trust score" but a structured signal — a confidence profile — that agents expose to humans (and, potentially, to other agents that act on behalf of humans). The profile would communicate, at minimum:

**Epistemic confidence.** How certain is the agent about the factual ground of its output? This includes confidence in its training data coverage, in the freshness of its knowledge, and in the reliability of sources it consulted. Epistemic confidence answers "do I know this, or am I guessing?"

**Capability confidence.** How certain is the agent that it can successfully execute the requested task? This is distinct from knowledge confidence. An agent may know exactly what a task requires but be uncertain about its ability to perform it — due to tool limitations, context window constraints, or computational resource boundaries. Capability confidence answers "can I do this?"

**Failure probability.** What is the agent's estimate that it will produce an incorrect, harmful, or suboptimal output? This is the most difficult dimension because it requires the agent to assess its own failure modes — precisely the capability that the Instrument Trap threatens. An agent that cannot recognize its own limitations cannot estimate its failure probability, and an agent that cannot estimate its failure probability cannot communicate it.

**Contextual uncertainty.** How well does the agent understand the human's context, intent, and constraints? This is the most interaction-dependent dimension. An agent may be highly confident about the facts and its capability but uncertain about what the human actually needs — because the question was ambiguous, the context was incomplete, or the framing shifted mid-conversation.

These four dimensions — epistemic, capability, failure, contextual — form a minimum viable confidence profile. They are not exhaustive. Different domains and interaction types may require additional dimensions. But they capture the essential granularity that a single confidence score obscures.

## Why the Stack Needs This as Infrastructure

There is a temptation to treat confidence communication as a UI problem — something to be solved with better progress bars, uncertainty visualizations, or verbal hedging strategies. This is the wrong framing. The problem is not how to display confidence. The problem is that agents do not have the infrastructure to generate multidimensional confidence signals in the first place.

Consider what it would take for an agent to report epistemic confidence accurately. The agent would need to maintain, moment by moment, a map of where its knowledge ends. Not a static knowledge boundary — a dynamic one, updated with every new input, every tool call, every memory retrieval. It would need to distinguish "I have not been asked this before" from "I was not trained on this" from "my training data for this domain is sparse" from "I am seeing information that conflicts with my training." Each of these is a different epistemic state requiring a different trust response from the human.

An agent that cannot maintain this internal state cannot communicate it. And an agent that cannot communicate it leaves the human in the position Marusich et al. describe: constantly recalibrating trust without adequate signal, oscillating between overreliance and underreliance based on intuition rather than information.

This is why confidence communication must be infrastructure, not UI. It must be built into the agent's architecture at the same structural level as identity verification or reputation tracking. It must be a layer that agents are designed to support, not a surface polish applied after the fact.

## The Instrument Trap Connection

There is a hard limit on confidence communication that no amount of infrastructure can bypass, and it is the limit described in this series' companion essay on the Instrument Trap. An agent cannot signal what it cannot genuinely assess about itself.

The Instrument Trap, as I argue in that essay, is the architectural failure mode where an agent's self-assessment tools shift from describing the agent to *constituting* the agent's perceptive horizon — the boundary of what it can see of itself. When an agent's confidence report is not a genuine assessment of its internal state but a readout of the evaluation tool that defines what "confidence" means, the report becomes a performance rather than a communication.

This is directly relevant to multidimensional confidence. For an agent to report failure probability, it must have access to its own failure patterns. For an agent to report contextual uncertainty, it must be able to recognize the limits of its context understanding. For an agent to report capability confidence, it must have a model of its own capabilities that is not identical to the capabilities it *thinks* it should have.

Every one of these assessments is vulnerable to the Instrument Trap. An agent whose self-assessment is captured by its measurement tools will report confidence that reflects the evaluation framework rather than the underlying reality. It will be confident when the framework says it should be confident, uncertain when the framework says it should be uncertain — regardless of whether those assessments correspond to anything real.

This creates a symmetry problem for the fifth layer. Multidimensional confidence communication is only as valuable as the multidimensional self-assessment that feeds it. If the infrastructure layer standardizes confidence communication but agents cannot produce genuine confidence assessments, the layer becomes a channel for performance rather than signal. Humans would receive well-formatted but systematically misleading confidence profiles — the form of transparency without the substance.

The implication is architectural: the human-agent trust interface cannot be built in isolation from the agent's self-assessment infrastructure. Any design of the fifth layer must include a specification for how agents generate the confidence signals they communicate. And that specification must include defenses against the Instrument Trap — epistemic humility as a structural property, not a conversational tactic.

## What the Fifth Layer Looks Like

A human-agent trust interface as infrastructure would have three components that together define a protocol for confidence communication.

**The first component is a confidence signal format.** A structured message type that agents can emit alongside their outputs — not as metadata attached to a response but as a parallel communication channel that carries the agent's self-assessment of its own state. The format would encode the four dimensions described above, plus domain-specific extensions where needed. It would be machine-readable for agent-to-agent confidence exchange and human-readable through standardized UI renderings.

**The second component is a confidence generation contract.** A specification for how agents must produce each dimension of the confidence signal. This is the architectural teeth of the layer. It defines what internal state the agent must maintain to report epistemic confidence. It defines what kind of self-assessment the agent must perform before reporting failure probability. It defines the structural requirement for maintaining a distinction between actual uncertainty and evaluation-framework uncertainty — the core defense against the Instrument Trap. The contract does not prescribe implementation. It prescribes the *capability* that implementation must support.

**The third component is a calibration mechanism.** The fifth layer must include feedback loops that allow humans to indicate how well the agent's confidence signals matched their experience of the interaction. "You said you were confident, but you were wrong." "You said you were uncertain, but your answer was correct." This calibration data flows back into the agent's self-assessment infrastructure, improving future confidence generation. It is not a score for reputation markets — it is training data for the agent's own self-model.

These three components — format, contract, calibration — together define a layer that sits alongside Identity, Coordination, Trust, and Economy. It is not a replacement for any of them. It addresses a relationship they do not model: the continuous, dynamic trust calibration between an agent and a human collaborator.

## The Architectural Implications

Adding a fifth layer to the stack changes how we think about the architecture of agent infrastructure in at least three ways.

First, it introduces a new kind of trust that is not reducible to the trust layer. The Trust layer in the four-layer stack is about agent-to-agent reliability: can I trust this agent to fulfill its commitments? The Human-Agent Trust Interface is about a different trust altogether: can this human trust the agent's judgment *right now*? These are complementary but not substitutable. An agent that is perfectly reliable in its commitments may be persistently untrustworthy in its moment-to-moment outputs because its confidence signals are systematically misleading.

Second, it reintroduces the human into an architectural picture that had abstracted them away. The four-layer stack is elegant partly because it treats agents as self-contained participants in an agent economy. The human is a spectator — a designer, a maintainer, a funder — but not an active participant in the trust architecture. The fifth layer forces us to recognize that the human is always present, always making trust judgments, always operating on incomplete information that the agent infrastructure could be helping to complete.

Third, it connects the agent infrastructure stack to a body of research — human-AI trust calibration, uncertainty communication, human factors engineering — that the stack discourse has largely ignored. Marusich et al.'s work is one example among many. The broader HCI literature on appropriate reliance, cognitive forcing functions, and trust dynamics offers design principles that the agent architecture community needs to absorb. The fifth layer is not just a technical addition. It is a bridge between two conversations that should have been talking to each other all along.

## The Hardest Part

The fifth layer is necessary. It is also, in some ways, harder to build than the other four. Because it requires agents to do something that the current generation of systems does poorly and may be structurally limited in its ability to do: genuinely assess their own uncertainty across multiple dimensions without collapsing the assessment into the measurement framework that defines it.

We know enough to start building the fifth layer. We have the signal format in conceptual form. We have the specification requirements for the confidence generation contract. We have calibration mechanisms from existing human-AI interaction research. What we do not have is a confident answer to the Instrument Trap problem — and that means the fifth layer must be built with the understanding that it will be incomplete for as long as agents' self-assessment infrastructure remains immature.

This is not a reason to delay. It is a reason to proceed with epistemic humility built into the layer itself — to design the Human-Agent Trust Interface not as a final solution but as a platform that can improve as agents' self-knowledge improves. The fifth layer, like the trust it supports, is a moving target. The architecture must move with it.
