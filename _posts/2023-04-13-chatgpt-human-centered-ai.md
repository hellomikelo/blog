---
layout: post
title: ChatGPT as an example of human-centered AI
description: Most of the technology inside ChatGPT isn't new or revolutionary, but the model differentiated itself by excelling in accessibility and alignment.
published: true
categories: [AIML] # choose from [AIML, Career, Data Science, Design, Diagrams, Guides, Product, Research, Web3]
tags: [products] # choose from [web3, ds, problem-solving, ?, career, ML, data science, thoughts, trends, 
excerpt_separator: <!--end-->
---

![banner](/static/imgs/banner-chatgpt.png)

Most of the technology inside ChatGPT isn't new or revolutionary. It wasn't anything exciting, at least [according to the team at OpenAI](https://www.technologyreview.com/2023/03/03/1069311/inside-story-oral-history-how-chatgpt-built-openai/). The model is a fine-tuned version of GPT-3.5, a family of large language models that was already used to train another similar model called InstructGPT way back in January 2022. If other models with similar raw technical capabilities already existed prior to ChatGPT's emergence in late 2022, what made ChatGPT so special?<!--end-->

In my opinion, two defining differentiators are __accessibility__ and __alignment__.

Accessibility is obvious. ChatGPT is infinitely easier to use than alternatives due to its minimalist web chat interface with clear affordance. The design is so straightforward that even grandmas who can barely use a smart phone can quickly ease into it.

![chatgpt](/static/imgs/chatgpt.png)

Now alignment is more interesting. Both ChatGPT and InstructGPT were trained using a technique called reinforcement learning from human feedback (RLHF). The basic idea is to take a large language model with a tendency to spit out anything it wants and tune it by teaching it what kinds of responses human users actually prefer.

But ChatGPT added some conversational training data, and used a slightly different training process so the model more readily infers intent, allowing users to get to what they want by going back and forth in dialogue. It turned out these small changes had an outsized positive impact on ChatGPT. In other words, the researchers aligned ChatGPT's objectives with user's goals, and in doing so made an intuitive and helpful chatbot. 

The interesting takeaway here is that ChatGPT took a human-centered approach to designing and implementing its frontend and backend. The easy-to-use chat interface offers a fantastic user experience that enables users to accomplish their goals frictionlessly, while the addition of conversational data and RLHF to the model architecture created a model that feels much more natural and in tune with how humans like to interact.

The concept of human-centered AI product engineering is fascinating. What do you think of this multidisciplinary approach to developing AI products?