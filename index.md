---
layout: default
title: home
permalink: /
---



## about me 
<div class="container">
<img src="/assets/images/me copy.jpg" alt="Sample Image" style="border-radius: 70%; max-width: 300px; max-height:auto"; margin-bottom: 1em;>


I am a recent computer engineering graduate at the University of Toronto. Currently,
I am currently collaborating with Prof. Xujie Si on developing neuro-symbolic AI systems to 
ground visual object motions to DSL programs.

My ultimate goal is in building socially-intelligent AI systems that are powerful, safe,
and interpretable. Pursuing this goal requires interdisciplinary work that I hope to 
explore in the future, as it will require a blend of expertise in social sciences and in 
CS to accomplish this.

Previously, I have worked with Prof. Hans-Arno Jacobsen at the MSRG lab at UofT, where I 
worked on developing private distributed networks to examine the effects of transferring 
large data on the throughput and latency of resource constrained distributed network.

<p style="text-align:center">
  <a href="mailto:gabrielp7700@gmail.com">Email</a> &nbsp;/&nbsp;
  <a href="/assets/data/myCV.pdf">CV</a> &nbsp;/&nbsp;
  <a href="https://ca.linkedin.com/in/gabriel-paulos">Linkedin</a> &nbsp;/&nbsp;
  <a href="https://github.com/gabriel-paulos/">Github</a>
</p>
</div>
## Motivating Questions (WIP)
  
  - What constitutes social intelligence for AI systems? How will this align with human
    values?
  - How can we align machine and human representations of complex data across abstraction levels?
  - How can we enable these systems to learn in highly dense modalities at varying levels of abstraction?
  - What type of relationships should humans and their AI companions have with each other,
    and what should constitute the limitiations of these relationships?
  - How should we assess the safety risks of human-AI relationships?
  - How can we assess the risks associated to powerful AI systems, that have access to real
    world tools and data?



## Ongoing Projects (independent)

### **MCTS DPO for VLMs:**

VLMs are trained by using image-text pairs to map the image embedding space
and the text embedding space into a joint embedding space. However there exists problems with
this approach: the first being that images are extremely information dense in comparison to text (making it more noisy at specific levels of abstraction or fine-grainedness), secondly VLMs are prone to bias towards the biases of its LLM component, lastly it struggles with solving complex questions that require multi-step reasoning. 

Similar to O1 there is a requirement for building reasoning trees or graphs such that we could reach a final conclusion
by exploring the space of possible explanations. However the added modality of vision introduces potential counterfacutal information [1](https://arxiv.org/pdf/2310.06627). In order to improve how we can reach a state of improving the "intuition" of these systems we will need a policy that is able to reward the system step-wise rather than conclusion-wise. This can be done using iterative learning [2](https://arxiv.org/pdf/2405.00451).

### **Generating better captions by treating visual and text tokens as a form of machine translation:**

In order to improve datasets we need to be able to create systems that are able to reason about images
over various abstraction levels. In order to do this we need to improve the development of our datasets. 
This involves creating systems that can automatically do this. Problem: VLMs struggle to connect an object with its
parts. This makes automatic detailed caption annotation difficult. Potentially, treating visual and text tokens as machine translation can lead towards improvement in this area. A key objective that has been overlooked by current caption models is diversity of caption quality. Given the richness of the modality, a top-k approach should be taken, as the maximization of log likelihood makes captions rather limited. I am currently exploring this. 

## publications

Gabriel Paulos, Tongkun Zhang, Yuqiu Zhang, Gerry Zhu, Jeyhun Karimov, and Hans Arno Jacobsen. 2023. Efficient Data Transfer in Shared-storage Cloud Data Processing Systems with OPTICS. In Proceedings of the 33rd Annual International Conference on Computer Science and Software Engineering (CASCON '23). IBM Corp., USA, 230–234.[paper](https://dl.acm.org/doi/pdf/10.5555/3615924.3623630)
