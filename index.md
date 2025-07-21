---
layout: project_page
permalink: /

title: "FlashTalker: Efficient Audio-Driven Speaker-Specific Talking Head Synthesis via Mesh-Embedded Gaussians"

authors:
    Jianjiang Yao, Ke Xian, Renxiang Dai, Lingwei Chen, Caiming Qiu 
affiliations:
    Huazhong University of Science and Technology
paper: "coming-soon"
video: "coming-soon"
code: "coming-soon"
data: "coming-soon"
# data: https://huggingface.co/docs/datasets
---

<!-- Using HTML to center the abstract -->
<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
    Thanks to its quick rendering speed and high visual quality, 3D Gaussian Splatting (3DGS) has been adopted for audio-driven talking head synthesis. However, existing 3DGS-based methods often underutilize the geometric priors provided by parameterized head models, making it challenging to learn accurate appearance and facial dynamics. Moreover, the lack of intermediate supervision during training leads to mismatches between facial expressions and lip movements, resulting in incorrect Gaussian deformations, visual artifacts, and jitter.
    To overcome these limitations, we introduce FlashTalker, a novel framework that adopts a “template + offset” paradigm for audio-driven talking head generation. We attach 3D Gaussians uniformly to the mesh surface of a parameterized FLAME head model and use audio signals as the primary driver for expression synthesis, enabling dynamic and semantically guided mesh deformation. To improve efficiency, we propose UV-based Gaussian sampling that adapts the number of Gaussians to the resolution, reducing spatial redundancy and accelerating inference.
    Additionally, FlashTalker incorporates a disentangled cross-region attention mechanism and lip-guided Gaussian supervision. These modules enable localized control of 3D Gaussian motion and introduce intermediate guidance to better align lip motion with audio cues. Compared to previous methods, FlashTalker achieves more accurate eye-blinking, enhanced reproduction of fine facial details such as wrinkles, and superior overall performance. Extensive experiments demonstrate its advantages in facial realism, lip-sync precision, and rendering speed.
        </div>
    </div>
</div>



## Method

![Turing Machine](/static/image/overview.png)

*Figure 1: Overview of FlashTalker. The Audio-to-Expression Translation module predicts FLAME expression parameters from audio input and combines them with tracked FLAME parameters to drive the deformation of a parameterized head model.
UV-based sampling is employed to uniformly distribute 3D Gaussians across the mesh surface, while additional Gaussians are placed on the teeth to construct the template Gaussian field.
The Disentangled Cross-Region Attention module partitions the head into upper-face, lower-face, and other regions, and applies region-specific cross-attention using corresponding driving features.
A global Head-Region Cross-Attention is introduced to ensure motion continuity across regions. Finally, an Offset MLP predicts spatial offsets of the template Gaussians relative to the target talking head.*

## Video
<video src="static\image\video_demo.mp4" controls width="1280"></video>

##  Comparison
Self-Driven Setting
![Turing Machine](/static\image\Self-Driven.svg)


Cross-Driven Setting
![Turing Machine](/static\image\Cross-Driven.svg)

## Ablation Study

<div style="display: flex; gap: 20px; align-items: center;">
  <img src="/static/image/teeth-lip_ablation.svg" alt="Turing Machine" width="45%">
  <img src="/static/image/wrinkles-eyes_ablation.svg" alt="Turing Machine" width="45%">
</div>
```
