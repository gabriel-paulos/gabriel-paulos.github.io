---
layout: post
title: "On-Device and Cloud Agent Collaboration"
subtitle: "Make distributed systems hip again"
date: 2025-05-04
tags: [embro, distributed systems, agents]
---

WIP

Distributed Agents and what it means for foundational models?

Minions paper: https://arxiv.org/pdf/2502.15964

Google A2A: https://github.com/google/A2A

A problem with the centralization of the largest models on the cloud infra of some of the largest companies in the world, is that the data sent to these models may be 
highly sensitive and there is risk of these models having access to information it should otherwise not have. An obvious workaround would be to create your own model, either
by training one from scratch or fine-tuning an open-source model locally (using Ollama for example). A problem with this solution is that this requires an immense amount 
of resource allocation to build, host and maintain these models. Many companies would not be willing to take on such a proposition. 

Luckily, a better solution has arrived: using a distributed systems of local AI agents that connect to a cloud foundational model. There has been siginificant work in this area (instead for dealing with environments where the context is significantly longer than the windows of any single LLM). Distributed systems concepts have appeared (such as the LLMxMapReduce paper), but there has yet to be a full deep dive of AI agents in distributed systems.  The effectiveness of the solution was recently demonstrated by the Minions paper. 
