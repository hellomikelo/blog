---
layout: post
title: Designing a desirable AI product
description: We're in the Wild Wild West of AI application development, in which companies race to figure out how to generate values using large models. How will they create desirable AI products? 
published: true
categories: [AIML] # choose from [AIML, Career, Data Science, Design, Diagrams, Guides, Product, Research, Web3]
tags: [products] # choose from [web3, ds, problem-solving, ?, career, ML, data science, thoughts, trends, products, Misc]
excerpt_separator: <!--end-->
---

## We've reached the AI critical mass

AI is having an "oh shit" moment. It's that moment before a roller coaster before its descent from the top, when you only see the sky and feel that butterfly in the stomach as you brace for the drop. Similarly, Large Language Models (LLMs) that have endured years of research and development have reached a turning point: The technology is finally about to spill over from academic research labs and tech companies out to the rest of the society.<!--end-->

In this current AI landscape, I see two major cohorts of players:

1. **Model producers:** Large research institutions and tech companies with access to advanced compute resources and ML expertise that will explore the frontiers of LLMs and train more advanced large models that exhibit increasingly sophisticated [emergent behaviors](https://www.pbs.org/wgbh/nova/sciencenow/3410/03-ever-nf.html). These players include OpenAI's [ChatGPT](https://openai.com/blog/chatgpt/), [DALL-E](https://openai.com/dall-e-2/), [Codex](https://openai.com/blog/openai-codex/), Stability AI's [Stable Diffusion](https://huggingface.co/spaces/stabilityai/stable-diffusion), Google's [Bard](https://blog.google/technology/ai/bard-google-ai-search-updates/), Meta's [BlenderBot](https://blenderbot.ai/), Baidu's [ERNIE Titan](http://research.baidu.com/Blog/index-view?id=165) and startups like [Cohere](https://cohere.ai/), [AI21 Labs](https://www.ai21.com/), [Midjourney](https://midjourney.com/), Anthropic's [Claude](https://scale.com/blog/chatgpt-vs-claude), [Jasper.ai](https://jasper.ai/), [Notion AI](https://www.notion.ai/), etc.
2. **Model consumers:** Individual developers and smaller companies lacking AI expertise that will start to apply LLMs to create intelligent applications and revamp different industries. At most, they may perform [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning) on their own proprietary datasets to finetune the large models to their specific use cases, but they will not commit resources to build large models from scratch.

Cohort #1 has been doing their thing for 10+ years, and that rising tide is well-documented in media coverage. What is less visible are the smaller boats in cohort #2 that are lifted as a result of those efforts. It now feels like a Wild Wild West of AI application development, in which companies race to figure out how to generate values using large models. As LLMs continue to be commoditized as API services and open sourced models, I can see attention in the AI landscape begin to shift toward the model consumers.

As AI matures as a technology, time is now ripe to seriously think through ways those large models can weave into our everyday lives. To begin to explore that thought, one starting point is to ask: _how can we make AI products desirable?_ Seeing as how AI will uproot the status quo and fundamentally redefine the way we interact with technology, how should AI products be designed and implemented so that they create more joy than woe? In this post, we'll dive into this topic of AI product desirability.


## Can AI products be desirable?

In 1990, General Magic co-founder Marc Porat described the concept of a smartphone that predated the iPhone to then-Apple CEO John Sculley, 

"A tiny computer, a phone, a very personal object… It must be beautiful. It must offer the kind of personal satisfaction that a fine piece of jewelry brings. It will have a perceived value even when it's not being used. It will offer the comfort of a touchstone, the tactile satisfaction of a seashell, the enchantment of a crystal. Once you use it you won't be able to live without it."

The notion of a desirable hardware is easy to grasp: you can see it, you can touch it, and you know you feel good when using it. But the same cannot be easily said for software (AI). The field of user experience (UX) research emerged to make software more user-friendly, and yet, even in the best designed software program, we don't perceive the same kind of strong visceral response that we'd get when using a well-designed physical product.

So does it even make sense to describe AI products as desirable? Maybe a good AI product isn't meant to be sexy or the centerpiece of an interaction. Maybe AI is meant to disappear into the background and do its job in silence. We talk about turning on lights, not electric lights, because electricity works so well that we take it for granted. If AI is the new electricity, then maybe it should be taken for granted, too. But does this suggest that desirable AI products aren't possible, or just that it doesn't exist yet? 

While I agree that AI products don't need to be eye-catching, I also believe that they can be desirable. More specifically, I believe their desirability can manifest in the form of fully immersive experiences, wherein the user can enter a state of flow and become highly involved and focused on what they are doing, like a writer becoming so absorbed in his craft that words flow easily and quickly and time passes without him noticing. By that definition, then yes, AI products can be desirable. In fact, they are close to becoming reality.


## Imagining the desirable AI product

One existing AI product that many people may perceive as desirable is probably ChatGPT: It offers an intuitive user interface, and the workflow is simple enough that people of all ages and technical savviness can use it effortlessly. While ChatGPT in its current form already feels more natural than its peers, OpenAI will no doubt continue to enhance its usability both in model sophistication and user interface.

However, to create a truly desirable AI product that doesn't yet exist, we must first imagine what it could be like, and think what is plausible based on current technological trajectory. To do this, we can turn to science fiction and pop culture to find inspirations. In the 2013 movie Her, one of the most memorable scenes is when the protagonist Theodore first activates and greets Samantha, the OS1AI system. Here's the scene,

{% include youtube.html id='GV01B5kVsC0' %}

That whole first encounter feels so playful, natural, and wonderful, despite the fact that Samantha is a computer program with no physical embodiment. Nonetheless, Theodore is fully engaged in their conversation, and is actually able to be productive by seamlessly transitioning into grooming email inbox and contact lists. To me, Samantha's interaction in that short sequence is the epitome of a desirable AI product. If we extrapolate the most salient characteristics from Samantha, we can begin to conceptualize what an ideal desirable AI product can be like:


* **It should feel intuitive**
    * **Simple interface.** OS1 offers a minimalistic interface (think Apple's Spotlight search) with system-wide reach that enables search for contacts, chat history, documents, and general knowledge. 
    * **Natural language.** Thoughts should be conveyed through basic forms of communication such as text or speech, not multiple choices or a series of button clicks.
    * **Multimodal interactions.** Ideas and questions should be expressed in a continuous thread in one or more mediums, such as sketches, images, text, or speech, whichever is most suitable at the moment.
* **It should be truthful.**
    * **Transparency.** It should be honest when it is uncertain about topics, set the right expectations, and disclose confidence scores when appropriate. 
* **It should solve nuanced problems**
    * **Contextual understanding.** It should comprehend your requests at face value, but also detect their undertone and varying sentiments through the tone of your voice. 
    * **Steer toward desired outcomes.** It should know when to nudge, not nag, you toward desired choices, but without removing options or changing incentives.
* **It should be fun**
    * **Unique identity.** It should have its own personality, with distinctive humor and quirks, but with guardrails to prevent inappropriate behaviors. This identity should grow over time through interactions with you, like aged leather that adds to its character without weakening its overall integrity.


## Turning plausible imaginations into reality

Years after the pandemic forced the world to work remotely, companies are facing challenges in adopting hybrid work. One main challenge being that while current enterprise SaaS tools focus on replicating the traditional paradigm of human-human collaboration in the virtual space, they lack the ability to promote a new kind of _human-machine collaboration_ that arises in remote settings and is crucial for [deep work](https://asana.com/resources/what-is-deep-work). Generative AI, with its conversational [affordances](https://www.merriam-webster.com/dictionary/affordance) and intuitive workflows, can enhance that human-machine collaboration.

Generative AI offers workers a new way to boost efficiency, creativity, and productivity, even when working alone. It can benefit all business units, and help with tasks such as drafting blog posts, job descriptions, meeting agenda, press releases, sales emails, social media posts, meeting summaries, action items, prioritizations, product strategy, code completion, etc. 

When generative AI evolves to a point where it can take on Samantha's charm and natural problem-solving capabilities, it will bring tremendous value to companies and employees. To create such a desirable AI product, some important milestones need to be reached,



* Redesign the user interface to promote more fluid and immersive interactions.
* Experiment with custom model architectures to create new [emergent behaviors in AI](https://en.wikipedia.org/wiki/Emergent_algorithm).
* Transfer learning with proprietary data to perform specialized tasks.

Recently Microsoft took a leap in that direction with a new Bing that's powered by ChatGPT (see overview [article](https://www.theverge.com/2023/2/7/23587454/microsoft-bing-edge-chatgpt-ai) and [video](https://youtu.be/q03pHll0VW4)). The new search engine offers Search, Answer, Chat, Create through a redesigned chat interface. At a high level, it works by using ChatGPT to transform user prompts into search queries that can map to a live internet index. Relevant contents are then fetched from the index and fed back into ChatGPT to summarize to the user. Microsoft also plans to incorporate ChatGPT into its [Office](https://www.theverge.com/2023/1/9/23546144/microsoft-openai-word-powerpoint-outlook-gpt-integration-rumor) and [Teams](https://www.theverge.com/2023/2/2/23582610/microsoft-teams-premium-openai-gpt-features) products. 

Other companies are also making similar strides. Zoom recently introduced its [Virtual Agent](https://explore.zoom.us/en/products/contactcenter/features/virtual-agent/) product, Notion introduced [Notion AI](https://www.notion.so/product/ai) digital writing assistant, and Jasper has the [AI Content Platform](https://www.jasper.ai/) to streamline creative workflows. The competition is heating up. All these companies are striving for the same goal, and that is to create the most desirable generative AI product on the market. 


## Buckle up for the ride!

Thirty years after the rise of the internet, we are now at the cusp of another tech revolution that's driven by AI. Generative AI can be a powerful force for good in many areas of our lives, but if designed and implemented carelessly, the technology can go by the wayside like what happened to [Microsoft's Tay](https://en.wikipedia.org/wiki/Tay_(bot)) back in 2016. And when taken to the extreme, it can lead to unintended harm like the cautionary tale in the movie [M3GAN](https://www.youtube.com/watch?v=BRb4U99OU80).

In order to realize AI's full potential, designers and developers need to make it desirable for the users to use. On the design front, this means leveraging good design patterns to make the system intuitive, trustworthy, and fun to use. On the engineering front, this means crafting custom model architectures with domain-specific data to create specialized systems that not only solve straightforward problems, but can also enhance human creativity. 

Honestly, it can be unnerving to be at the "anticipation moment" of this generative AI roller coaster ride. There's a mix of excitement, fear, and thrill because we aren't sure where this technology will take us, or whether it will live up to its promise. The responses stirred up by this technology can be intense, but it's often moments like this that are remembered long after the ride is over. So let's buckle up and enjoy the journey! 
