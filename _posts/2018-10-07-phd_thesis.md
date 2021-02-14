---
title: "PhD Thesis: Geometry and Uncertainty in Deep Learning for Computer Vision"
layout: single
read_time: true
comments: true
share: true
author_profile: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/research/phd_red_door.jpg
excerpt: "<br><br><br>"
categories:
  - computer_vision
tags:
  - computer vision
  - deep learning
  - geometry
gallery_uncertainty:
  - image_path: /assets/images/research/input.png
    alt: "Input Image"
  - image_path: /assets/images/research/segmentation.png
    alt: "Semantic Segmentation"
  - image_path: /assets/images/research/uncertainty.jpg
    alt: "Uncertainty"
---


Today I can share my final PhD thesis, which I submitted in November 2017. It was examined by Dr. Joan Lasenby and Prof. Andrew Zisserman in February 2018 and has just been approved for publication.
This thesis presents the main narrative of my research at the University of Cambridge, under the supervision of Prof Roberto Cipolla. 
It contains 206 pages, 62 figures, 24 tables and 318 citations.
You can download [the complete .pdf here](/media/papers/alex_kendall_phd_thesis_compressed.pdf).

{% capture fig_thesis %}
![PhD Thesis]({{ "/assets/images/research/thesis.jpg" | absolute_url }})
{% endcapture %}<figure>
  {{ fig_thesis | markdownify | remove: "<p>" | remove: "</p>" }}
</figure>

My thesis presents contributions to the field of computer vision, the science which enables machines to see.
This blog post introduces the work and tells the story behind this research.

<video autoplay loop>
  <source src="/assets/images/research/multitask_scene_understanding.mp4" type="video/mp4">
</video>

> This thesis presents deep learning models for an array of computer vision problems: [semantic segmentation](https://arxiv.org/abs/1511.00561), [instance segmentation](https://arxiv.org/abs/1705.07115), [depth prediction](https://arxiv.org/abs/1705.07115), [localisation](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/Kendall_PoseNet_A_Convolutional_ICCV_2015_paper.pdf), [stereo vision](https://arxiv.org/pdf/1703.04309.pdf) and [video scene understanding](/media/papers/alex_kendall_phd_thesis_compressed.pdf).

## The abstract

Deep learning and convolutional neural networks have become the dominant tool for computer vision. These techniques excel at learning complicated representations from data using supervised learning. In particular, image recognition models now out-perform human baselines under constrained settings. However, the science of computer vision aims to build machines which can see. This requires models which can extract richer information than recognition, from images and video. In general, applying these deep learning models from recognition to other problems in computer vision is significantly more challenging.

This thesis presents end-to-end deep learning architectures for a number of core computer vision problems; scene understanding, camera pose estimation, stereo vision and video semantic segmentation. Our models outperform traditional approaches and advance state-of-the-art on a number of challenging computer vision benchmarks. However, these end-to-end models are often not interpretable and require enormous quantities of training data.

To address this, we make two observations: (i) we do not need to learn everything from scratch, we know a lot about the physical world, and (ii) we cannot know everything from data, our models should be aware of what they do not know. This thesis explores these ideas using concepts from geometry and uncertainty. Specifically, we show how to improve end-to-end deep learning models by leveraging the underlying geometry of the problem. We explicitly model concepts such as epipolar geometry to learn with unsupervised learning, which improves performance. Secondly, we introduce ideas from probabilistic modelling and Bayesian deep learning to understand uncertainty in computer vision models. We show how to quantify different types of uncertainty, improving safety for real world applications.

## The story

I began my PhD in October 2014, joining the controls research group at Cambridge University Engineering Department.
Looking back at my original research proposal, I said that I wanted to work on the 'engineering questions to control autonomous vehicles... in uncertain and challenging environments.'
I spent three months or so reading literature, and quickly developed the opinion that the field of robotics was most limited by perception.
If you could obtain a reliable state of the world, control was often simple.
However, at this time, computer vision was very fragile in the wild.
After many weeks of lobbying Prof. Roberto Cipolla (thanks!), I was able to join his research group in January 2015 and begin a PhD in computer vision.

When I began reading computer vision literature, deep learning had just become popular in image classification, following inspiring breakthroughs on the ImageNet dataset.
But it was yet to become ubiquitous in the field and be used in richer computer vision tasks such as scene understanding.
What excited me about deep learning was that it could learn representations from data that are too complicated to hand-design.

I initially focused on building end-to-end deep learning models for computer vision tasks which I thought were most interesting for robotics, such as [scene understanding (SegNet)](http://mi.eng.cam.ac.uk/projects/segnet/) and [localisation (PoseNet)](http://mi.eng.cam.ac.uk/projects/relocalisation/).
However, I quickly realised that, while it was a start, applying end-to-end deep learning wasn't enough.
In my thesis, I argue that we can do better than naive end-to-end convolutional networks. 
Especially with limited data and compute, we can form more powerful computer vision models by leveraging our knowledge of the world.
Specifically, I focus on two ideas around geometry and uncertainty.

 - *Geometry* is all about leveraging structure of the world. This is useful for improving architectures and learning with self-supervision.
 - *Uncertainty* understands what our model doesn't know. This is useful for robust learning, safety-critical systems and active learning.

Over the last three years, I have had the pleasure of working with some incredibly talented researchers, studying a number of core computer vision problems from localisation to segmentation to stereo vision.

{% include gallery id="gallery_uncertainty" caption="Bayesian deep learning for modelling uncertainty in semantic segmentation." %}

## The science

This thesis consists of six chapters. Each of the main chapters introduces an end-to-end deep learning model and discusses how to apply the ideas of geometry and uncertainty.

*Chatper 1 - Introduction.* Motivates this work within the wider field of computer vision.

*Chapter 2 - Scene Understanding.* Introduces SegNet, modelling aleatoric and epistemic uncertainty and a method for learning multi-task scene understanding models for geometry and semantics.

*Chapter 3 - Localisation.* Describes PoseNet for efficient localisation, with improvements using geometric reprojection error and estimating relocalisation uncertainty.

*Chapter 4 - Stereo Vision.* Designs an end-to-end model for stereo vision, using geometry and shows how to leverage uncertainty and self-supervised learning to improve performance.

*Chapter 5 - Video Scene Understanding.* Illustrates a video scene understanding model for learning semantics, motion and geometry.

*Chapter 6 - Conclusions.* Describes limitations of this research and future challenges.

{% capture fig_phd %}
![PhD Overview]({{ "/assets/images/research/phd_demo.jpg" | absolute_url }})
{% endcapture %}

<figure>
  {{ fig_phd | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>An overview of the models considered in this thesis.</figcaption>
</figure>

# As for what's next?

This thesis explains how to extract a robust state of the world -- semantics, motion and geometry -- from video.
I'm now excited about applying these ideas to robotics and learning to reason from perception to action.
I'm working with an amazing team on autonomous driving, bringing together the worlds of robotics and machine learning. 
We're using ideas from computer vision and reinforcement learning to build the most data-efficient self-driving car.
And, we're hiring, come work with me! [wayve.ai/careers](https://wayve.ai/careers)

> I'd like to give a huge thank you to everyone who motivated, distracted and inspired me while writing this thesis.

Here's the bibtex if you'd like to cite this work.

<div id="bibtex_phd">
<small><div class="highlighter-rouge"><pre class="highlight">
<code>@phdthesis{kendall2018phd,
  title={Geometry and Uncertainty in Deep Learning for Computer Vision},
  author={Kendall, Alex},
  year={2018},
  school={University of Cambridge}
}
</code></pre></div></small>
</div>

And the source code for the latex document is [here](https://github.com/alexgkendall/thesis).
