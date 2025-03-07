---
layout: post
title: "Hallucinations of VLMs"
subtitle: "Are you sure that you saw that?"
date: 2025-03-04
tags: [child, VLMs, hallucination]
---

Note: That the below is a continous work in progress. This blog's ethos of writing posts is ellaborated [here](~/2025-01-18-Future-Plan.md).
All changes can be seen by looking at the history of the markdown file, [here](https://github.com/gabriel-paulos/gabriel-paulos.github.io/blob/theme-edits/_posts/2025-01-18-Hallucinations.md).


Motivating Question: Why do VLMs hallucinate? Why do they hallucinate **_more than_** LLMs? Can we do anything about it?

Partial Inspiration: [paper](https://lilianweng.github.io/posts/2024-07-07-hallucination/)


#### Table of Contents

- [What are VLMs](#what)
- [Training Methods](#training)
- [VLM Hallucinations](#hallucinations)
- [Taxonomy of Hallucinations for VLMs](#taxonomy)
- [Hallucination Detection](#detection)
- [Mitigation Methods](#mitigation)
- [Citations](#citations)
- [Appendix](#appendix)



## <a name="what">What are VLMs?</a>

Vision Language Models (VLMs) or sometimes referred to as LVLMs (Large Vision Language Models) are models that learn using the modalities of images and text. These models work well in zero-shot settings for object localization, image recognition and visual question answering among other things. Examples of VLMs include LLaVA, the DeepSeek VL model, OLMo. There exists a couple of training objectives for VLMs: contrastive, masking, and generative [[1](https://arxiv.org/pdf/2405.17247)]. The most popular method for construcitng these models is to use pre-trained backbones, as it is one of the cheapest and fastest ways to build a VLM. These systems are realized using a projection matrix to create a joint embedding space between the (pre-trained) CLIP encoder and a LLM model. Due to the popularity of such models I will be focusing this article on these types of VLMs.

<figure>
    <img src="/assets/images/Hallucination_blog_fig_1" alt="Families of VLMs" class="img-posts">
    <figcaption>Fig.1: Image of Families of VLMs (source: <a href="https://arxiv.org/pdf/2405.17247"> (Bordes et al. 2024) </a></figcaption>
</figure>

## <a name="training"></a>How are they trained?

These can be trained in similar ways to LLMs. Some of the training methods include: Parameter Efficient Finetuning (PEFT), and supervised learning. It should be noted that many of these systems are trained with a contrastive objective. This is due to the nature of the CLIP encoder (which is also trained contrastively). For CLIP, this means that we use image-caption pairs to train the CLIP encoder. Contrastive training would ask the CLIP model to output whether it is a positive sample (the image and caption correspond to each other) or a negative sample (they do not correspond with each other). Along with the fact that the image modality is so rich, the limited nature of the training paradigm makes it difficult for these systems to learn fine-grained details of an image. 


## <a name="hallucinations">VLM Hallucinations? </a>

The struggles with hallucinations for LLMs are well documented in text generation. The same problems occur and appear more grave for VLMs, specifically in the context of long-form visual reasoning. Below we will go through common VLM hallucinations and some of the reasons why they occur. 

<figure>
    <img src="/assets/images/HalluEx.png" alt="Language Prior Hallucination" class="img-posts">
    <figcaption>Fig.2: Example of a hallucination caused by the language priors of the model (source: <a href="https://arxiv.org/pdf/2502.12359"> (Wu et al. 2025)) </a></figcaption>
	</br></br>
</figure>



VLM hallucinations differ from normal LLM hallucinations as the latent space for VLMs is more coarse than the latent space for LLMs. This has to do with a carousel of reasons: from the architecture of VLMs, the tendency of VLMs to bias their outputs more on the text modality, the loss function used to align the CLIP and LLM modules, misalignment with abstract human concepts and CLIP’s latent space. In fact, there is reason to believe that the embedding space used by VLMs does not include a rich representation of visual tokens [[2](https://arxiv.org/pdf/2407.06581)].

### <a name="diffs">Are VLMs more hallucination prone that LLMs? Why or why not? </a>

Due to the rich nature of the visual modality and the training objectives of VLMs, these systems are more prone to hallucinations than normal LLMs. This manifests itself in these systems being extremely fragile to changes in answer permutations for Multiple Choice Question Answering (MCQA) and restricts its ability to visually reason [[3](https://arxiv.org/pdf/2310.01651)], [[4](https://arxiv.org/pdf/2310.06627)]. VLMs actually exhibit *worse* performance in spatial reasoning tasks when visual input is included [[5](https://arxiv.org/html/2406.14852v2#S3)]. The fact of the matter is that this makes VLMs a higher risk than LLM when attacked adversarially.  

## <a name="taxonomy">Taxonomy of VLM hallucinations</a>:

Broadly hallucinations come in two forms: limitations in understanding input images, and the overreliance of lingusitic priors of the LLM. However this manifests itself in various ways:

- Identification and localization of non-existent objects in the input image 
- Object, Attribute, relational hallucinations (Same as above basically)
- Action/verb-related Concepts (https://arxiv.org/pdf/2412.14487)
- Misunderstanding of spatial relations between objects in an input image
- Miscounting objects in the image
-  Event Hallucination: Describes a non-existent target and constructs completely non-existent events around those imagined targets, including its attributes, relations and actions.  (ref: https://arxiv.org/pdf/2402.15721)
- Modality conflict between the text and image components (arXiv:2403.11116)
 

- Bias towards Linguistic Priors: specifically in long context or long answers where previous text influences the current output (ref: https://arxiv.org/pdf/2501.15046); or in situations where the input image and a the language model’s world knowledge disagree
	- Benign Hallucination: When a linguistic prior is found within the input image, and is used without any regards towards the 	representations found within the image; a second version of this would be when the model hallucinates without any adverse effects on its final answer in a VQA dataset.
	- Image-biased Hallucination: The visual content conflicts with the language model’s world knowledge, and steers the model towards generating false premises, example shown below
	- Counterfactual reasoning 

(IBD image here) 

## <a name="detection">Hallucination Detection</a>

There are various metrics used to evaulate how hallucination prone models are. These will be discussed in the appendix. 

Various benchmarks have been constructed to detect hallucinations. The hope of using these hallucination detection methods is to gather a large enough dataset of negative and positive samples such that these hallucinations can be trained away. However, we remain far from that reality. For one we do not have an agreed upon evaluation metric. Nor, do we have satisfactory evaluation benchmark format to probe the understanding of these models. These evaluation metrics use hallucination metrics that will be discussed in detail in the appendix. Currently, there exists two types of evaluation benchmarks:

- Generative evaluations
- Discriminative evaluations

Generative evaluations apply VLMs to describe the image then evaluate the completions of the VLMs outputs using LLM evaluators. An example of the difference between a discriminative and a generative evaluation framework is shown below. A limitation of this type of evaluation is dependent on the ability of LLMs to remain faithful to the answer, a bar that is rather unstable. 

<figure>
    <img src="/assets/images/GenVsDisc" alt="Generative vs discriminative task difference" class="img-posts">
    <figcaption>Fig.3: Generative vs Discriminative format difference (source: <a href="https://arxiv.org/pdf/2405.05256"> (Kaul et al. 2024)) </a></figcaption>
</br></br>
</figure>

Discriminative evaluations are asked about the existence of objects in an image, in which the VLM must answer in a yes-or-no format. This is very limited and is more an artifiact of the previous benchmarks used before the invention of VLM models (I am speaking pre-2023). However, they still remain a go-to method for hallucination as they are quite cheap to verify and to create. 

Both of these types of evaluations are inherently limited in their ability to probe and define hallucinations found within these systems. Recently, there have been efforts in creating evaluations that include generative and discriminative evaluation tasks. AMBER (https://arxiv.org/abs/2311.07397) uses no LLM evaluator, instead using a new metric named AMBER score (which utilizes the CHAIR metric as part of its score). This metric will be further discussed in the appendix. However the format of AMBER benchmark’s task format remains similar to other traditional discriminative and generative benchmarks’ task formats. LongHalQA is a recent effort within the class of benchmarks that contain generative and discriminative tasks. However it differentiates itself two-fold: by including evaluations with and without LLM-evaluators, and by formating tasks as a multi-choice question-answering task. This departure seems to be quite useful as it significantly lowers evaluation times, especially compared to generative evaluations.

<figure>
    <img src="/assets/images/LongHalQA" alt="Comparison of evaluation times required to complete 1000 image-text pairs for different benchmarks" class="img-posts">
    <figcaption>Fig.4: The following comparison evaluates the  (source: <a href="https://arxiv.org/pdf/2405.05256"> (Kaul et al. 2024)) </a></figcaption>
</br></br>
</figure>

Future evaluations should look more in depth into creating subject-specific benchmarks in a similar vain to LongHalQA. However, there remains much room for exploration specifically in the creation of hallucination tasks that evaluate the reasoning ability of these models or in having a dialogue-level hallucination evaluation benchmark (https://aclanthology.org/2024.findings-emnlp.529.pdf). 

## <a name="Mitigation">Current Hallucination Mitigation methods for VLMs?</a>

There exist numerous proposed solutions to different types of VLM hallucinations:

- Finetuning 
- Post training RLHF and DPO 
- Contrastive decoding techniques
- Attention Calibration Methods

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

CHAIR: https://arxiv.org/pdf/1809.02156
