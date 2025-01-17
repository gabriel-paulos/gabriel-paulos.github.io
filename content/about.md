+++
title = "About"
+++

## about me 

{{< headshot src="/static/me.jpg" name="" add="" >}}

I am a recent computer engineering graduate at the University of Toronto. Currently,
I am currently collaborating with Prof. Xujie Si on developing neuro-symbolic AI systems to 
ground visual object motions to DSL programs.

My ultimate goal is in building socially-intelligent AI systems that are powerful, safe,
and interpretable. Pursuing this goal requires interdisciplinary work that I hope to 
explore in the future, as it will require a blend of expertise in social sciences and in 
CS to accomplish this.

To this end, I have particular interests in exploring the alignment issues with AI systems,
how best to track these changes, and how to 

Previously, I have worked with Prof. Hans-Arno Jacobsen at the MSRG lab at UofT, where I 
worked on developing private distributed networks to examine the effects of transferring 
large data on the throughput and latency of resource constrained distributed network.

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

**MCTS DPO for VLMs:**

VLMs are trained by using image-text pairs to map the image embedding space
and the text embedding space into a joint embedding space. However there exists two problems with
this approach: the first being that images are significantly denser modalities than text and hold much more noise than text could ever possibly hold, secondly there exists an imbalance with the ratio between visual tokens and text tokens in these systems as there are way more text tokens than visual tokens, lastly it struggles with solving complex questions that require multiple steps.
   
Similar to O1 there is a requirement for building reasoning trees or graphs such that we could reach a final conclusion
by exploring the space of possible explanations. However the added modality of vision makes this task more complex. In order to improve how we can reach a state of improving the "intuition" of these systems we will need a policy that is able to reward the system step-wise rather than conclusion-wise. This can be done using DPO.

**Generating better captions by treating visual and text tokens as a form of machine translation:**

In order to improve datasets we need to be able to create systems that are able to reason about images
over various abstraction levels. In order to do this we need to improve the development of our datasets. 
This involves creating systems that can automatically do this. Problem: VLMs struggle to connect an object with its
parts. This makes creating detailed captions hard automatically. Potentially treating visual and text tokens as machine translation can potentially improve this by treating it as a translation problem whose objective is not necessarily 
the maximazation of hte log likelihood of the system, rather it should be able to look at the highest likelihoods and use that to create captions. The density of images renders the max log likelihood answer implicitly limited. 


candidate in the Earth System Science department at the [Stanford
Doerr School of Sustainability][5]. I am part of the [EchoLab][6] and lucky to
be advised by [Marshall Burke][7]. I am supported by a [Stanford Data Science
Fellowship][9] and the Ram and Vijay Shriram Sustainability Fellowship. In the
past, I was a pre-doctoral fellow at the Energy Policy Institute (EPIC) at the
University of Chicago, working at the [Climate Impact Lab][3]. In a previous
life, I was a Data Scientist at [DSaPP][4] (now @CMU), and a career bureaucrat
at the Central Bank of Colombia. 

## research interests

I evaluate the effects of environmental changes on humans. I also develop
machine learning models to create cool datasets that help us track humans and
nature in data-scarce scenarios. I am interested in downscaling climate data
products, multi-modal classification, measurement error in causal inference
models, and wildfires in the Western US.

## news and updates

  
  - **[11/23]** Me and my ~~weak~~ accepted paper on wildfire house' burning
    risk will be in the CompSust Workshop at NeurIPS 2023 in New Orleans. 
  - **[09/23]** I received the Stanford Data Science Fellowship (2 years) and
    now I am part of the SDS PhD Scholars 💻🤖.
  - **[08/23]** I am presenting our work on wildfire house' burning risk using
    multimodal classification and recent developments in contrastive learning
    in [TWEEDS][8] in Portland.

## <u class="publications">publications</u>, <u class="working">working papers</u> & <u class="conferences">workshops</u>
 
<p>&nbsp;</p>

<mark class="confm">1. **Higuera-Mendieta, I**, Wen, J., & Burke, M. (2023). A table is worth a thousand pictures: Multi-modal contrastive learning in house burning classification in wildfire events. *NeurIPS 2023 Computational Sustainability: Promises and Pitfalls from Theory to Deployment*.</mark>
   
   <button class="button" onclick="location.href='https://openreview.net/forum?id=7KTQsrUIOy'" id="paper-button">OpenReview</button>
   
<mark class="workm">2. Farah, A., **Higuera-Mendieta, I**, Song, Y., Franke, J. A., Moyer, E.,
   & Nakamura, N. (2020). Arctic airmass displacement and reduced midlatitudes
   wintertime temperature variability under climate change. [In preparation for
   *Geophysical Research Letters*].</mark> 
   - Presented at the American Geophysical Union Meeting AGU  2020.

<mark class="pubm">3. Rodolfa, K. T., Salomon, E., Haynes, L., **Higuera-Mendieta, I**, Larson, J.,& Ghani, R. (2020). Case study: Predictive fairness to reduce misdemeanor
   recidivism through social service interventions. In *Proceedings of the 2020
   conference on fairness, accountability, and transparency* (142–153). FAT\* '20</mark>
   
   <button class="button" onclick="location.href='https://arxiv.org/abs/2001.09233'" id="paper-button">Paper</button>
   <button class="button" onclick="location.href='https://github.com/dssg/aequitas'" id="code-button">Code</button>

<mark class="pubm">4. Bonilla-Mejia, L., & **Higuera-Mendieta, I.** (2019). Protected Areas under Weak Institutions: Evidence from Colombia. *World Development*, 122</mark> 
   
   <button class="button" onclick="location.href='https://www.sciencedirect.com/science/article/pii/S0305750X19301718'" id="paper-button">Paper</button>
   <button class="button" onclick="location.href='https://github.com/banco-republica-research/deforestacion'" id="code-button">Code</button>
 
   - Ranked second-best paper by the International Sustainable Development
      Research Society.
   - Press coverage (in Spanish): [El Tiempo][1]


[1]: https://www.eltiempo.com/vida/medio-ambiente/deforestacion-en-colombia-territorios-colectivos-para-frenarla-379204
[3]: http://www.impactlab.org/ 
[4]: http://www.datasciencepublicpolicy.org/
[5]: https://sustainability.stanford.edu/
[6]: https://www.stanfordecholab.com/
[7]: https://web.stanford.edu/~mburke/
[8]: https://tweeds.io/
[9]: https://datascience.stanford.edu/programs/stanford-data-science-scholars-program


