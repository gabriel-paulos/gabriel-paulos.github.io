---
layout: post
title: "Hallucinations of VLMs"
subtitle: "Are you sure that you saw that?"
date: 2025-03-04
tags: [child, VLMs, hallucination]
---

Motivating Question: Why do VLMs hallucinate? Why do they hallucinate **_more than_** LLMs? Can we do anything about it?

Partial Inspiration: [paper](https://lilianweng.github.io/posts/2024-07-07-hallucination/)


#### Table of Contents

- [What are VLMs](#what)
- [Training Methods](#training)
- [VLM Hallucinations](#hallucinations)
- [Taxonomy of Hallucinations for VLMs](#taxonomy)
- [Mitigation Methods](#mitigation)
- [Citations](#citations)
- [Appendix](#appendix)

Agenda:

## <a name="what">What are VLMs?</a>

Vision Language Models or sometimes referred to as LVLMs (Large Vision Language Models) are models that learn using the modalities of images and text. These models work well in zero-shot settings for object localization, image recognition and visual question answering among other things. Examples of VLMs include LLaVA, the DeepSeek VL model, OLMo. There exists a couple of training objectives for VLMs: contrastive, masking, and generative [[1](https://arxiv.org/pdf/2405.17247)]. The most popular method for construcitng these models is to use pre-trained backbones, as it is one of the cheapest and fastest ways to build a VLM. These systems are realized using a projection matrix to create a joint embedding space between the (pre-trained) CLIP encoder and a LLM model. Due to the popularity of such models I will be focusing this article on these types of VLMs.

<p>
    <img src="/assets/images/Hallucination_blog_fig_1" alt="Families of VLMs" class="img-posts">
    <em>Fig.1: Image of Families of VLMs (source: <a href="https://arxiv.org/pdf/2405.17247"> (Bordes et al. 2024) </a></em>
</p>

## <a name="training"></a>How are they trained?

These can be trained in similar ways to LLMs. Some of the training methods include: Parameter Efficient Finetuning (PEFT), and supervised learning. It should be noted that many of these systems are trained with a contrastive objective. This is due to the nature of the CLIP encoder (which is also trained contrastively). For CLIP, this means that we use image-caption pairs to train the CLIP encoder. Contrastive training would ask the CLIP model to output whether it is a positive sample (the image and caption correspond to each other) or a negative sample (they do not correspond with each other). Along with the fact that the image modality is so rich, the limited nature of the training paradigm makes it difficult for these systems to learn fine-grained details of an image. 


## <a name="hallucinations">VLM Hallucinations? </a>

The struggles with hallucinations for LLMs are well documented in text generation. The same problems occur and appear more grave for VLMs (Vision Language Models), specifically in the context of long-form visual reasoning. Below we will go through common VLM hallucinations and some of the reasons why they occur. 


VLM hallucinations differ from normal LLM hallucinations as the latent space for VLMs is more coarse than the latent space for LLMs. This has to do with a carousel of reasons: from the architecture of VLMs, the tendency of VLMs to bias their outputs more on the text modality, the loss function used to align the CLIP and LLM modules, misalignment with abstract human concepts and CLIP’s latent space. In fact, there is reason to believe that the embedding space used by VLMs does not include a rich representation of visual tokens [[2](https://arxiv.org/pdf/2407.06581)].

## <a name="taxonomy">Taxonomy of VLM hallucinations</a>:

- Misalignment between text and image modality
- In-Context: where the hallucination has to do with the VLM not aligning itself with the interaction it is a part of
- Bias towards linguistic priors (IBD: Alleviating Hallucinations in Large Vision-Language Models via Image-Biased Decoding), specifically in long text
- Benign Hallucination: When a linguistic prior has a bias that is acutally present in the image that it retrieves without any focus on the image
- Image-biased hallucination: the visual content conflicts with the langugage model’s world knowledge
 
I would like to further explore image-biased hallucinations as they have not been formally explored but can pose extreme difficulties given the fragile nature of VLMs to prompts, due to the biased nature they have towards text tokens.


### <a name="diffs">Are VLMs more hallucination prone that LLMs? Why or why not? </a>

Due to the rich nature of the visual modality and the training objectives of VLMs, these systems are more prone to hallucinations than normal LLMs. This manifests itself in these systems being extremely fragile to changes in answer permutations for Multiple Choice Question Answering (MCQA) and restricts its ability to visually reason [[3](https://arxiv.org/pdf/2310.01651)], [[4](https://arxiv.org/pdf/2310.06627)]. VLMs actually exhibit *worse* performance in spatial reasoning tasks when visual input is included [[5](https://arxiv.org/html/2406.14852v2#S3)]. The fact of the matter is that this makes VLMs a higher risk than LLM when attacked adversarially.  

## <a name="Mitigation">Current Hallucination Mitigation methods for VLMs?</a>

There exist numerous proposed solutions to different types of VLM hallucinations:

- Finetuning 
- Post training RLHF and DPO 
- Contrastive decoding techniques

Below I will include some of these solutions (this will be fleshed out):

[V-DPO](https://arxiv.org/abs/2411.02712)

[IBD](https://arxiv.org/pdf/2402.18476)

[MIA-DPO](https://arxiv.org/pdf/2410.17637)

[CLIP-DPO](https://arxiv.org/pdf/2408.10433)

[HA-DPO](https://opendatalab.github.io/HA-DPO/)

[OPA-DPO](https://arxiv.org/pdf/2501.09695)

[SUMGD](https://arxiv.org/pdf/2410.13321)

[ISR-DPO](https://arxiv.org/pdf/2406.11280)



## <a name="citations">Citations</a>Citations

[[1](https://arxiv.org/pdf/2405.17247)]

[[2](https://arxiv.org/pdf/2407.06581)]

[[3](https://arxiv.org/pdf/2310.01651)]

[[4](https://arxiv.org/pdf/2310.06627)]



## <a name="appendix">Appendix: Evaluation Benchmarks</a>

POPE: https://github.com/RUCAIBox/POPE 
