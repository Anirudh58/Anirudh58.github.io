---
layout: single
read_time: false
comments: false
share: false
title: Research Highlights
permalink: /research/
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/kings.jpg
  caption: "Photo: [Olly McMillan](https://www.youtube.com/watch?v=kQkZeXHfgwA&t=1s)"
gallery_uncertainty:
  - image_path: /assets/images/research/input.png
    alt: "Input Image"
  - image_path: /assets/images/research/segmentation.png
    alt: "Semantic Segmentation"
  - image_path: /assets/images/research/uncertainty.jpg
    alt: "Uncertainty"
---

I am excited about research which advances the perception and control of mobile robotics.
In particular, I am currently working on improving the robustness and accuracy of computer vision algorithms, leveraging geometry for self-supervised learning and developing end-to-end systems which can reason from perception to control.

# Reasoning from Perception to Action

The computer vision systems which I develop are primarily motivated to extract a representation which can be used to make a decision or action.
I'm interested in learning representations to understand scenes and control the behavior of real world robots.
For example, we designed a reinforcement learning agent which can learn to [drive a car with deep reinforcement learning](https://wayve.ai/blog/learning-to-drive-in-a-day-with-reinforcement-learning).
We also showed, for the first time, a self-driving car which [learned to drive in simulation](https://wayve.ai/blog/sim2real).

![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/l2diad.gif){: .align-center}

---

# Scene Understanding

Scene understanding is a computer vision task to generate a representation of a scene which can be used to evaluate decisions or actions.
This typically requires understanding information such as the scene's semantics, geometry and motion.
Initially, I worked on a semantic segmentation algorithm called [SegNet](http://mi.eng.cam.ac.uk/projects/segnet/).
More recently, I have been interested in learning a representation from a [multitask deep learning architecture](https://arxiv.org/pdf/1705.07115.pdf).

![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/multitask.jpg){: .align-center}

---

# Bayesian Deep Learning

Deep learning is great for achieving state-of-the-art results, however these models cannot understand what they don't know.
Bayesian deep learning (BDL) is a promising framework for understanding our model's uncertainty.
[This paper](https://arxiv.org/pdf/1703.04977.pdf) is an introduction to Bayesian deep learning for computer vision. 
I have also found BDL useful for [localisation](http://arxiv.org/abs/1509.05909), [scene understanding](http://arxiv.org/abs/1511.02680) and [autonomous driving](https://www.ijcai.org/proceedings/2017/0661.pdf).

{% include gallery id="gallery_uncertainty" caption="Bayesian deep learning for semantic segmentation. From left to right: input image, semantic segmentation and model uncertainty." %}

---

# Localisation

[PoseNet](http://www.cv-foundation.org/openaccess/content_iccv_2015/papers/Kendall_PoseNet_A_Convolutional_ICCV_2015_paper.pdf) was the first end-to-end deep learning algorithm for relocalisation - 
estimating the position and orientation of the camera from an image within a previously explored area. 
It works over large outdoor urban environments or inside buildings. 
It takes only 5ms to do this from a single colour image, [here is a demo](http://mi.eng.cam.ac.uk/projects/relocalisation/).

Check out some 3D reconstructions of [King's College](http://mi.eng.cam.ac.uk/~agk34/map.html) and [central Cambridge](http://mi.eng.cam.ac.uk/~agk34/viewer.html) in your web browser.

![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/research/localisation.jpg){: .align-center}

---

# Other Projects

Some more details of other projects, including an autonomous drone and augmented reality, [can be found here](/other_projects/).
