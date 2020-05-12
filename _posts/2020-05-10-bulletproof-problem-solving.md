---

layout: post
title: A Bulletproof Problem Solving Approach to Data Science
description: 
published: false
categories: [Books]
excerpt_separator: <!--more-->

---

Charles Conn and Robert McLean's book called Bulletproof Problem Solving: The One Skill that Changes Everything

## Introduction

Last year I came across Charles Conn and Robert McLean's book called Bulletproof Problem Solving: The One Skill that Changes Everything, which discussed a 7-step approach used extensively by management consultants at McKinsey & Company to address almost any complex challenge in business…and  pretty much anything in life. I was immediately intrigued by the notion of a structured framework to problem-solving, so I spent some time reading up on it. As I was learning about it, I realized how powerful and sensible the framework was, and how applicable it was for solving complex problems in our everyday lives. As Charle Coon, the author of the book, said in a 2019 (highly recommended) McKinsey podcast,
"Problem solving is the answer to the question 'What should I do?' It's interesting when there's uncertainty and complexity, and when it's meaningful because there are consequences."

Fast forward to now, as I make a career transition into data science and learn about the nuances of working on complex datasets with little foresight but with significant business implications, I realized how valuable this framework can be in tackling data-centric business problems. I think newcomers in this space do not have proper understanding of the data science methodology and workflow, so it is easy to jump straight into building machine learning models without first clearly defining a business problem to solve, and without understanding the data and the appropriate algorithms to use to solve the problems. 

To avoid this potential shortfall and to establish a best practice, in this post I will share how I think the bulletproof problem solving framework can be used in data science. In the following sections I'll outline how you can think about approaching a data science project for a business by considering these 7 steps: 

1. Define the problem
2. Disaggregate into sub-problems
3. Prioritize sub-problems
4. Plan out the work
5. Analyze each sub-problem
6. Synthesize findings 
7. Communicate the findings

## The 7-step problem solving framework

1. Define the problem

	Scope out the business problem you're trying to solve by putting it into a concise problem statement. Some questions that can be asked are: "What should I do? What are the constraints that exist for such a problem? What are the dependencies? What are the forces acting upon your decision maker? How quickly is the ML model needed? With what precision is the solution needed? Are there areas that are off limits or areas where we would particularly like to find our solution? Is the stakeholder open to exploring other areas besides ML systems?" Don't make assumptions about the problem, and don't run off with half of the idea about what the problem is and start collecting data and building models, because oftentimes people will have very different views of the problem. Therefore, it's important to clearly define a problem statement that will help you get to the heart of what matters.

2. Disaggregate

	Every interesting data problem has some complexity and some uncertainty in it, and without breaking it down into manageable chunks, the problem may seem intractable or daunting. The process of disaggregating the problem often gives you an insight into potential solutions quite quickly. Disaggregation can be done by creating a logic tree, of which there are two types (according to professor of strategy Arnaud Chevallier): diagnostic-based and solution-based. Diagnostic trees break down a "why" key question, identifying all the possible root causes for the problem (e.g. why is the current data solution not working?). Solution trees break down a "how" key question, identifying all the possible alternatives to fix the problem (e.g. how can using a new ML model improve the business?). You can read more about logic trees here.

3. Prioritize

	In the real world, data teams have limited manpower and resource to tackle problems, so sub-problems identified in the logic tree should be rigorously prioritized to make sure the team will make the most impact toward solving the big problem (see Pareto's 80/20 principle). This can be approached as a sensitivity analysis, where you vary the input parameters of the problem ("lever") and estimate how much each will have on the outcome. Here, it is important to avoid spending a lot of time arguing about branches of the tree that are either not important or that none of us can change, so you want to focus on levers that are big and movable.

4. Plan out the work
	
	Now that the important sub-problems are identified, specific data analyses should be planned out to tackle them, along with a clear timeline to accomplish them. You need to find a work plan that fits the level of precision and time frame that is agreed upon by the stakeholders. It is important to remember that problem solving is an iterative process. This means that in work planning you should always aim to get a one-month, one-day, one-week, and one-month answer to your problem, and at each stage iterate on the problem solving workflow to improve on the process.

5. Analyze
	
	Now we finally get to the analysis part of the whole process. The rule of thumb is to start simple and to rigorously explore the data first. Even clever data visualization done using simple heuristics and explanatory statistics can provide an incredible wealth of insights into the problem. At this point, ask questions such as: "Is the data right? Is it sound? Does it make sense?" When machine learning approaches are deemed appropriate, the model building process should be iterative, with repeated testing and learning. First build a minimum viable product with simple classical ML models like decision tree or regression, then work up to the big-gun tools like convolutional neural networks or recurrent neural networks. When in doubt, keep it simple, stupid (KISS)!

6. Synthesize
	
	At this point you have finished several data analyses and have built a working ML model, and you may think you have solved problem and pat yourself on the back. But of course you are not done, because you still have not synthesize the results of the analyses and weave them into a story that helps the stakeholders answer the question, "What should I do?" If you don't do this well, you've just got a bunch of analysis. So remember to take the time to craft a message that can convince everyone that your analysis is sound, or that your ML model works as intended.

7. Communicate
	
	Any analysis or ML system, no matter how detailed and accurate, is a waste of time if it does not bias to action. The outcome of a successful data project should be clearly communicated to all stakeholders, and should drive meaningful changes in the organization by actively addressing key performance indexes. Then, and only then, can a problem be considered solved. 

## Takeaways

Remember that problem solving is an iterative process that is constrained by varying priorities (time, accuracy, cost, etc) imposed by each scenario. Even when the 7-step framework is followed through to complete a project, the outcome will lead to iterations of other projects that build upon the existing solution. Truly interesting business problems are never fully solved, so happy iterating!