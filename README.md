# Stateful Prompt-Chaining

<picture>
 <img alt="a close up of a person holding a cell phone" src="readme/pradamas-gifarry-889Qh5HJj4I-unsplash.jpg">
</picture>

**Note:** The framework is currently being development as part of multiple ongoing projects. We will release a public version once the underlying concepts will be published. Contact desa[at]zhaw.ch for information or dedicated access. 

## Table of Contents
- [Introduction](#introduction)
- [Project Overview](#project-overview)
- [Note](#note)


## Goal

Stateful Prompt-Chaining is a framework developed to improve the capabilities of large language models (LLMs) in handling complex tasks where prompt dependencies and multi-layered contexts play a role. The idea is to support the development of LLM applications by breaking down complex tasks into smaller, more precise and more testable subtasks. It requires less time and effort to experiment with variations of prompts, thus facilitating evidence-based feasibility and proof-of-value studies.

## Objective

Stateful prompt chaining introduces a model-driven approach to chaining, branching, looping and merging multiple LLM prompts. This enables the design, implementation and validation of complex LLM applications with precise and testable prompts. Furthermore, additional components such as APIs, databases, knowledge bases or generative image models can be embedded to extend conversational capabilities. This setup simplifies the implementation of complex NLP tasks, such as long-term therapy support for chronic diseases, counselling of young people with hearing disabilities, providing learning aids for school subjects or de-biasing natural language texts.

## Example Application

In what follows we present an example conversation between a user and conversational agent. The conversation is annotated with references to its states and partial information related to state transitions including triggers, guards and actions.

### Pseudo State: Start

### State: Initialization
Coach: "Hello, it's great to meet with you today. I'm here to support you on your journey towards improved well-being. What's your name?"

Client: "Hello, my name is John."

Coach: "Nice to meet you, John.

**Trigger: The client shares their name.**

#### State: Connection Building
Coach: "I believe understanding personal context is crucial in our journey together. If you're comfortable sharing, could you tell me a bit about your daily routine or something you enjoy doing in your spare time?"
Client: "Well, I'm a huge fan of cycling. I usually go for a ride early in the morning before work. It's a great way to start the day and helps me clear my mind."
Coach: "That's wonderful, John. Cycling is a great way to keep both mind and body healthy. Perhaps we can also consider incorporating elements of your love for cycling into our plan."
**Trigger: The client shares a personal interest or detail about their daily life.**

#### State: Well-being Assessment
Coach: "Could you tell me about how you're currently feeling about your overall well-being?"
Client: "Well, I'm feeling a bit stressed lately, and I don't think I'm eating as well as I could be."
Coach: "Thank you for sharing, John. It sounds like stress and nutrition are two areas we could focus on."
**Trigger: The client provides information regarding their well-being.**

#### Pseudo State: Decision Node <sup>Branching</sup>
**Decision: Does the information contain at least one positive item?**
Yes: Continue with State "…"
No: Continue with State "Pain Point Identification"

#### State: Pain Point(s) Identification
Coach: "Could you tell me more about what's causing your stress?"
Client: "Most of my stress comes from work. I've been working long hours, and it feels like I never get a break."
Coach: "Thank you for sharing more about your work stress. Before we delve deeper, would you like to discuss any other areas of concern?"
Client: "Yes, I would also like to talk about my eating habits."
Coach: "Of course, we can certainly discuss that. Can you share more about your current eating habits?"
Client: "I often skip breakfast and then overeat during lunch and dinner. I also eat a lot of fast food because I don't have much time to cook."
Coach: "Ok, I took note of that. Any other area of concern?"
Client: "No, these would be the most pressing ones."
Coach: "Thanks for sharing, John. It's clear that work stress and poor eating habits are areas we can work on."
**Trigger: The client has no more concerns.**

#### Pseudo State: Decision Node (1/3) <sup>Looping</sup>
**Decision: Are there any unprocessed items in the list of pain points?**
No: Continue with State "Completion"
Yes: Continue with State "Solution Suggestion"

#### State: Solution Suggestion (1/2)
Coach: "Let's start by discussing stress management techniques. Have you ever tried mindfulness or meditation to manage stress?"
Client: "No, I haven't tried that."
Coach: "Mindfulness exercises can be really effective in managing stress. Would you be open to trying some guided meditation sessions this week?"
Client: "Yes, I think I would like to try that."
**Trigger: The client shows willingness to a suggestion.**

#### State: Agreement (1/2)
Coach: "Great, let's start with 10 minutes of guided meditation in the morning."
Coach: "What days of the week would you be able to squeeze that in?"
Client: "Monday, Thursday, Saturday, and Sunday."
Coach: "Ok. Let's start with three times per week. Choose three days out of the four you suggested before."
Client: "Monday, Thursday, and Sunday."
Coach: "Ok. So that's settled."
**Trigger: A smart goal is agreed on.**

#### Pseudo State: Decision Node (2/3) <sup>Looping Cont.</sup>

#### State: Solution Suggestion (2/2)
Coach: " Now, regarding nutrition, would you consider preparing some meals at home, maybe starting with breakfast?"
Client: "Yes, I'm willing to try that as well."
State: Agreement (2/2)
Coach: "Well then, let's try that out for tomorrow. What is it you could have for breakfast tomorrow?"
Client: "I like porridge."
Coach: "Me too. Do you have Oat, Maple Sirup and Milk?"
Client: "Yes, I have all of that."
Coach: "Perfect. You shall have an oatmeal for breakfast tomorrow."

#### Pseudo State: Decision Node (1/3) <sup>Looping Exit</sup>

#### State: Completion <sup>Merging</sup>
Coach: "Fantastic, John. So, this week, you'll try 10 minutes of guided meditation on Monday, Thursday, and Sunday morning. And you will have breakfast tomorrow."
Coach: "Let's check in again next week to see how these changes are affecting your well-being. Do you have any questions or concerns?"
Client: "No, I think I'm ready to give it a try. Thank you."
**Trigger: The client confirms no further assistance is needed.**

#### Pseudo State: Final

## Note

The framework is currently being development as part of multiple ongoing projects. We will release a public version once the underlying concepts will be published. Contact desa[at]zhaw.ch for information or dedicated access.
