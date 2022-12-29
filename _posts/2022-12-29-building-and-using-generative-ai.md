---
layout: post
title: Generative AI is shifting the way we use and build technology
description: Generative AI is shifting the way we use and build technology
published: true
categories: [AIML] # choose from [Career, Data-Science, Design, Diagrams, Guides, Product Research, Web3]
tags: [] # choose from [web3, ds, problem-solving, ?, career, ML, data science, thoughts, trends, products, Misc]
excerpt_separator: <!--end-->
---

I recently participated in a series of generative AI hackathons hosted by [LabLabi.ai](https://lablab.ai/event), [OpenAI](https://openai.com/), and [Cohere](https://cohere.ai/). I built a [smart personal task planner](https://hellomikelo-smarty-smarty-app-2flo6l.streamlit.app/), a [meeting transcription and summarization service](https://hellomikelo-openai-hackathon-app-wip-initial-r4od4p.streamlit.app/), and a [podcast search engine](https://hellomikelo-semantic-search-hackathon-streamlit-app-p4qpo5.streamlit.app/), all using APIs provided by generative AI startups ([OpenAI](https://openai.com/) and [Cohere](https://cohere.ai/)), and all done within 2 to 7 days (see project details [here](https://hellomikelo.com/projects)). They were really fun learning experiences, and really opened my eyes to just how fast one can prototype a functional and useful minimum viable product in such a short time using today's readily available (and often free) technologies.<!--end-->

Also, like many others, I had a chance to play with ChatGPT for various prototyping and brainstorming tasks. It was a mind blowing experience, and I came away with a lot of learning about how this kind of emerging AI technology can drastically change the way we work – both as an end user and as an application builder. Here are some of my thoughts from both perspectives.


## As an end user

Using generative AI is kind of like working with a human assistant. You provide instructions, ask questions, or describe an image the way you would to a colleague, and then you see what the model outputs. Then you tune the prompt based on the output and iterate this process until a satisfactory result is achieved. Finally, you may take the output and add some additional personal touches to make it your own. This is a paradigm shift in how we work with AI. Some described this as a kind of ["sandwich" workflow](https://archive.ph/El8P1).

This kind of back-and-forth collaboration feels really natural to us because it's similar to how we humans work together in group settings. Heck, I feel like we already do this with technologies in hacky ways using search engines. In my typical workflow, I'd Google a question and browse the top few results to see if they provide the information I need, and maybe reference a paragraph and image here and there, or copy a code snippet I need. Then I'd iterate on this search process until I assemble the final output I want. 

However, even though search engines contain all of this world's knowledge, they still haven't replaced most human jobs. Similarly, instead of taking over human jobs, generative AI will take over certain routine tasks such as information gathering and guiding brainstorming. This will free up humans to focus on more creative and fulfilling tasks. In that sense, I definitely envision generative AI becoming a productivity boosting tool. In fact, I can already see inklings of it through my short interactions with ChatGPT and DALL-E.

While playing around with generative AI technologies I am met with a new and interesting kind of challenge: how should I clearly express what I want to make so the model understands and can generate it accurately? The mental effort is no longer spent on "HOW can I use this technology" but rather "WHAT do I want to build with this technology?" From a model usage and interaction standpoint, this translates into two main tasks: 



1. Formulate an initial seed prompt to instruct the model to generate an output somewhat close to I have in my mind, then
2. Refine the prompt or output in various ways to iteratively guide the model towards my final vision (as close to it as possible).

The process of prompt formulation and refinement are still in their infancy, and I see lots of opportunities for improvement there. In other words, the challenge will become: “how can the interactive workflow be enhanced such that the user can seamlessly get from point A (describing the thing I want to make) to point B (the thing as I envisioned in my mind). For instance, what if ChatGPT or DALL-E provides multimodal editing capabilities that allow users to incorporate text, images, and even sound together to refine outputs? Or what if there is a more defined way to rephrase requests such that they can better build on top of previous prompts to refine the output? Because our interactions with generative AI are still so new and unstructured, the overall user experience still has a lot of room for improvement. Simply put, the main question to be addressed is how we can combine modalities and workflows to faithfully translate creative and abstract human ideas into generative physical representations. 


## As an application builder

The majority of the application builders out there don't want to bother with building the most sophisticated ML models that are trained on billions of parameters and require enterprise-level distributed compute infrastructures to execute. That kind of specialized human capital and infrastructure are out of most companies and developers' areas of expertise. Instead, most people and organizations simply want to use the models as a black box to retrieve some predictions that their apps can then use to solve real-world problems. In other words, what they want is a turnkey solution, which can be provided by the nicely packaged Model as a Service (MaaS). 

This trend toward MaaS is evident in the emergence of generative AI APIs and UIs from startups such as [Hugging Face](https://huggingface.co/), [OpenAI](https://openai.com/), [Cohere](https://cohere.ai/), [Stability.ai](https://stability.ai/), [Lensa AI](https://apps.apple.com/us/app/lensa-ai-photo-video-editor/id1436732536) and [Jasper AI](https://www.jasper.ai/). Similar solutions are offered by more established cloud providers such as GCP (e.g. [Cloud Vision API](https://cloud.google.com/vision/pricing), [Video AI](https://cloud.google.com/video-intelligence), [Natural Language AI](https://cloud.google.com/natural-language), etc), AWS ([AWS AI services](https://aws.amazon.com/machine-learning/ai-services/)), and Azure ([Cognitive Services](https://azure.microsoft.com/en-us/products/cognitive-services/)), and by mobile app development frameworks such as Apple's [CoreML](https://developer.apple.com/documentation/coreml)/[CreateML](https://developer.apple.com/machine-learning/create-ml/) and Google's [Tensorflow Lite](https://www.tensorflow.org/lite). In all these AI products, the ML solution providers expose APIs to the pre-trained large ML models, and developers simply call the APIs with their unstructured input data and model parameters, and get back model outputs that then feed into downstream applications. If a customized model is needed, the developers can provide proprietary training data to the providers to further fine-tune pre-trained models via transfer learning.

In a way, this paradigm democratizes the power of AI/ML beyond those highly specialized practitioners that work in the field, and in a sense commoditizes AI as a tool for all with basic tech savviness to use. So from the developer's perspective, only a high level understanding of fundamental ML concepts (e.g. classification, regression, embeddings, etc) are needed to effectively leverage those AI solutions to create some really powerful ML-driven applications. 


## Closing thoughts

Even though the creation and application of large ML models is an engineering feat that should be celebrated and recognized, the true potential of generative AI–and ML-driven products in general–can only be realized through deep understanding of user pain points and tailored user experience design. I think one product that is on the right track is ChatGPT. I say this because using it feels frictionless and intuitive, which means I am able to focus on using the tool (yes it is a tool after all) to complete my task rather than figuring out how to deal with the quirks in the tool. 

Finally, like I mentioned above, better prompt formulation and refinement workflows will take generative AI tools to the next level. Like everyone else, I definitely think generative AI holds a lot of potential to revolutionize our lives, and I am excited to keep following this space and hopefully contribute to its growth. If you're also interested in discussing this topic, I'd love to chat some more!