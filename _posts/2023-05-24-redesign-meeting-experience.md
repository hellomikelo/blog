---
layout: post
title: Redesign the Video Meeting Experience
description: 
published: false
categories: [Design] # choose from [AIML, Career, Data Science, Design, Diagrams, Guides, Product, Research, Web3]
tags: [trends] # choose from [web3, ds, problem-solving, ?, career, ML, data science, thoughts, trends, products, Misc]
excerpt_separator: <!--end-->
---

When the pandemic first hit, virtual meeting was one of the few tools that truly connected us to family and colleagues. At that time people were happy to have just any reliable communication tool that worked -- they had low expectations and were easy to satisfy. <!--end-->

## 😩 The Woes of Virtual Meetings

But fast forward 3 years to now, expectations have changed. After countless virtual meetings, companies and workers are no longer satisfied with the bare minimum in video communication. They are tired of having inefficient meetings that suck disproportionate of their time but produce a fraction of the value. [Workers Now Spend Two Full Days a Week on Email and in Meetings](https://www.wsj.com/articles/workers-say-its-harder-to-get-things-done-now-heres-why-2a5f1389).

This frustration is a _good_ thing. 

Truth be told, even after 3 years of practice, most people still suck at having productive virtual meetings. This is due to a combination of technological and human factors. 

|···|

Let's consider a typical virtual meeting journey,

_\<placeholder\>_

Here are some possible pain points that can sting the overall experience.

| Journey | Pain |
|--|--|
| Get meeting invite | No meeting agenda or any context |
| Join meeting | Meeting drags on aimlessly and runs over time|
| End meeting | No concrete summary and action items |

What's worse, the following week you may get _another_ meeting invite on the same topic, like a meetings deja vu! 

## Reimagining the Meeting Experience 

So how might we redesign virtual meetings for a productive experience? Let's zoom out and think about how progress is generally made. I like the [Double Diamond]() process for framing this innovation process. 

The Double Diamond entails __discover, define, develop, and deliver__. The “discover” and “define” phases are where virtual meetings can have the most impact on (if done correctly). They're where open-ended and heads-up collaboration and discussion take place. 

[double diamond]()

* Discover. The first diamond helps people understand, rather than simply assume, what the problem is. It involves speaking to and spending time with people who are affected by the issues.
* Define. The insight gathered from the discovery phase can help you to define the challenge in a different way.

This process involves idea generation, goal review and alignment, and establishing to-do tasks and milestones that each team member can go off and work on their own. I'd bet that >80% of virtual meetings would be considered fruitful if they can just accomplish those 3 feats. But of course, that's easier said than done. 

The realization of those improvements will require a systems-level approach that needs a combination of technological (e.g. AI) and user experience innovations (e.g. [nudges](https://en.wikipedia.org/wiki/Nudge_theory)). Let's reimagine how each pain point can be alleviated. 

## Redesigning for a Productive Meeting

__No meeting agenda or context in meeting invite__: Solution can be as simple as requiring the host to set an agenda when sending a meeting invite. To , an AI-enabled virtual assistant can parse through any periphery documents related to the discussion to suggest and pre-populate an agenda. The documents can be pre-embedded and stored in a vector to enable quick parsing and summarization. 

__Meeting drags on and meanders__: To adhere the meeting to the agenda, an AI moderator can join the meeting and moderate the discussion based on the pre-set agenda. 

To implement this, meeting conversations can be converted to text using automatic speech recognition (ASR), then the transcript can feed into a custom large language model (LLM) to gain a semantic understanding of the discussion, and also measure how far the conversation is diverging from the predetermined agenda, maybe by calculating the cosine similarity between the agenda item and live transcript. If the similarity diverges below a certain threshold, then the AI moderator can initiate a gentle reminder to get back on track. 

To combat overrunning meetings, meeting UI can introduce a subtle visual cue to convey the sense of time running out, like a digital hourglass that unobtrusively trickles sand down to the end of the meeting. The benefit of this simple UI update is two-fold: (1) it instills comfort in the attendees in knowing that the meeting is progressing, so they don't feel like they're trapped in an endless meeting (like they're in a casino with no clocks), (2) it instills a sense of urgency in the host to move things along and not waste time. 

__No concrete summary and action items__: AI-based solutions are readily available for doing this. This is a straightforward task of ASR followed by text summarization to output meeting summary and action items when the meeting ends. In addition to generating those takeaways, the AI moderator can also block out the last 5 minutes of the meeting to review those notes with the attendees so everyone can level set before they end the call with the takeaways. 

Lastly, to avoid “meeting deja vu” and ensure that the meeting actually leads to meaningful progresses, the AI moderator can nudge the participants to remind them of the action items. What's more, it can also explicitly lay out the steps the team can take to push forward. 

While this sounds like something out of a Sci-fi movie, this is quickly becoming feasible as autonomous AI agents (e.g. Baby AGI and Auto GPT) matures. In short, when presented with a general task (i.e. a post-meeting action item), the AI agent can create and prioritize an execution plan that lays out the steps needed to complete the task. Then the agent can either guide the humans through task execution, or actually attempt to execute the tasks itself if given sufficient access to backend data and documentations. 

## Achieving Flow in Meetings

I believe virtual meetings _can_ be beloved rather than something to be endured if they can just help teams achieve “flow.” Flow as in the team aligning on a shared purpose and making meaningful progress. I think most people don't mind working hard and attending meetings, but what they (myself included) despise is the sense of stagnation caused by ineffective communication and lack of directions. They want to feel that the effort they put in is reciprocated with equal result. But as we all know, that's rarely the case.

And this is where I believe the marriage of UX design and AI--if done thoughtfully--can be of service. The more I think about this, the more I see new opportunities arise in this rapidly developing space, and I am excited to continue to write about it more. 
