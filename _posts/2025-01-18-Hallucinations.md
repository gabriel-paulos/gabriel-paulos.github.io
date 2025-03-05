---
layout: post
title: "Hallucinations of VLMs"
subtitle: "Are you sure that you saw that?"
date: 2025-01-18
tags: [embryo, VLMs, hallucination]
---

Motivating Question: Why do VLMs hallucinate? Why do they hallucinate **_more than_** LLMs? Can we do anything about it?

Partial Inspiration: [paper](ttps://lilianweng.github.io/posts/2024-07-07-hallucination/)


#### Table of Contents

- [What are VLMs](#what)
- [Training Methods](#training)
- [Hallucinations](#hallucinations)
    -[LLMs](#llms)
    -[VLMs](#vlms)
    -[Differences](#diffs) 
- [Taxonomy of Hallucinations for VLMs](#taxonomy)
- [Mitigation Methods](#mitigation)
- [Citations](#citations)
- [Appendix](#appendix)

Agenda:

## <a name="what">What are VLMs?</a>

Vision Language Models or sometimes referred to as LVLMs (Large Vision Language Models) are models that learn using the modalities of images and text. These models work well in zero-shot settings for object localization, image recognition and visual question answering among other things. Examples of VLMs include LLaVA, the DeepSeek VL model, OLMO. There exists a couple of training objectives for VLMs: contrastive, masking, and generative [1](#https://arxiv.org/pdf/2405.17247). The most popular method for construcitng these models is to use pre-trained backbones, as it is one of the cheapest and fastest ways to build a VLM. These systems are realized using a projection matrix to create a joint embedding space between the (pre-trained) CLIP encoder and a LLM model. Due to the popularity of such models I will be focusing this article on these types of VLMs.

## <a name="training"></a>How are they trained?

These can be trained in similar ways to LLMs. Some of the training methods include: Parameter Efficient Finetuning (PEFT), and supervised learning. It should be noted that many of these systems are trained constrastively. This is due to the nature of the CLIP encoder (which is trained contrastively). Recently, there has been much investigattion into understanding how the CLIP encoder effects the ability of these models to learn fine-grained properties of the objects in an image (need a ref). This has an effect on the ability of these systems to reason over images or documents. 


## <a name="hallucinations">What are hallucinations? </a>

### <a name="llms">LLMs </a>

### <a name="vlms">VLMs </a>

### <a name="diffs">Are VLMs more hallucination prone that LLMs? Why or why not? </a>

## <a name="taxonomy">Taxonomy of VLM hallucinations</a>

## <a name="Mitigation">Current Hallucination Mitigation methods for VLMs?</a>

## <a name="citations">Citations</a>Citations

## <a name="appendix">Appendix (maybe)</a>


