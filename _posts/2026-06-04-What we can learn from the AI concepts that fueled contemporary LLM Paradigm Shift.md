---
layout: post
title: What We Can Learn from the AI Concepts That Fueled the Contemporary LLM Paradigm Shift
categories: self-reflection
excerpt: 
image: assets/images/blog/human_ai.jpg
---

This blog post is inspired by a video from Varun Mayya ([link](https://youtu.be/TT385EFm6jM)). The neural network conceptualized in the 50s — which acts as the backbone of modern AI — was actually designed by observing biological neurons. Decades later, we scraped the whole internet, invented transformer architecture, RLHF, distillation, etc., and made incredible progress. Now, can we humans become better by using the frameworks that made AI better?

## Pretraining

This is when the model reads the entire internet, without any goal.
For us humans, this is like reading a book without an objective, having diverse experiences, talking to other people, travelling, and going to school to learn general things. Because of this stage, we can observe patterns from different domains that nobody else can see.

## Fine-Tuning

This is when a pretrained model is trained further on a smaller domain-specific dataset. It already knows a lot, but now it becomes good at one thing.
For humans this is specialization. After learning general things, we should go deep into one domain. A doctor, lawyer, entrepreneur, engineer all starts with general knowledge, but eventually gets fine-tuned into their craft.

## Retrieval Augmented Generation (RAG)

This is when the model retrieves information from external source instead of relying only on its memory.
Humans should do the same. We should not try to memorize everything. We should build our own retrieval system using notes, journals, bookmarks, personal wiki and trusted sources. Knowing where to find information is often more important than remembering it.

## Context Window

This is the amount of information the model can hold in its working memory at a given time. If important information falls outside the context window, the model performs worse.
For humans this is attention and focus. We may know a lot, but if we are distracted by ten different things, we cannot perform at our best. Deep work is essentially increasing the quality of our context window.


## Reasoning

This is when the model breaks the problem into steps, then thinks step by step. Techniques include Chain-of-Thought, Self-Critic, etc.
We humans are obviously better at reasoning, but there are frameworks that we can use to be better at reasoning. We can use steelmanning, first-principles thinking, second-principles thinking, and inversion. We need to journal our decisions so that we can review them later and make our reasoning better.

## Evaluation & Benchmarks

AI researchers constantly evaluate models on benchmark to measure progress. Without evaluation, it is impossible to know if the model is actually getting better.
Humans should do the same. We should periodically test ourselves. This can be exam, project, publication, fitness goal, business outcome or performance review. Learning without evaluation can create an illusion of progress.

## RLHF (Reinforcement Learning from Human Feedback)

This is when humans provide feedback to the model so that it learns which responses are useful and which are not. This stage made AI much more helpful.
For humans this is mentors, coaches, managers, peers and customers. We improve when we receive feedback from others. The challenge is not finding feedback, but learning how to accept it without becoming defensive.


## Tool Usage

This is when the model uses MCP, defined API-based tools, and the shell to perform actions.
We humans need to constantly learn one tool at a time. The best way to learn is by doing end-to-end projects. Once we get good at learning tools, we need to combine tools and finally learn which tool to use (and not use) when.

## Multimodal Learning

This is when the model gets beyond text and learns to work with images, video, and audio. Different modalities enforce one another.
As humans, we should learn from multiple modalities (books, blogs, podcasts, videos, conversations) and output in different modalities. People who make videos on a topic have a better general understanding of that topic than the person who wrote about it.

## In-Context Learning

This is when AI models can do entirely new tasks from examples in the prompt that were not in their training data.
For humans, it is reading cues in the room and situational learning. To learn this, we need to deliberately put ourselves in novel situations. If we are given five examples, we should be able to create the sixth.

## Distillation

This is when a small model learns from a larger model.
We can summarize everything we know about a particular domain into distilled content and teach it to others. Feynman Technique, yeah. It will allow us to compress knowledge and make room for others.

## Self-Alignment

Modern AI models have a set of guardrails to prevent them from providing harmful responses.
As humans, we can write all our values in a document, occasionally review them, and update them. We should be guided by our values.

## Self-Play

AlphaGo became great by playing against itself thousands of times. It found new strategies that humans didn't see.
As humans, we can learn this framework by doing pre-mortems, thought experiments, scenario playing, and red-teaming our own strategy.

## Mixture of Experts (MoE)

This is when the main model has specialized sub-networks for domain-specific tasks. The model activates the right part for a specific task.
For humans, this is like having different modes, i.e., the creative mode and the analytical mode. For example, we should not bring the engineer mindset into a board meeting where we should have brought an entrepreneurial mindset.

## Continual Learning

LLMs can't unlearn just the right amount. When introducing new information to the model, it goes through catastrophic forgetting. Because of this, Google, Anthropic, and OpenAI build models from scratch every time.
But humans are better at this. We don't forget how to ride a bike once we train ourselves to drive a car. For humans, the challenge is psychological. We have identity attachment, sunk-cost reasoning, and pruning failure.
