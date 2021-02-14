---
title: "Reprojection Losses: Deep Learning Surpassing Classical Geometry in Computer Vision?"
layout: single
read_time: true
comments: true
share: true
author_profile: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/escher.jpg
excerpt: "<br><br><br>"
categories:
  - computer_vision
tags:
  - computer vision
  - deep learning
  - geometry
---

**2017 was an exciting year as we saw deep learning become the dominant paradigm for estimating geometry in computer vision.**

Learning geometry has emerged as one of the most influential topics in computer vision over the last few years. 

> "Geometry is ... concerned with questions of shape, size, relative position of figures and the properties of space” ([wikipedia](https://en.wikipedia.org/wiki/Geometry)).

We've first seen end-to-end deep learning models for these tasks using supervised learning, for example depth estimation ([Eigen et al. 2014](https://cs.nyu.edu/~deigen/depth/)), relocalisation ([PoseNet 2015](http://mi.eng.cam.ac.uk/projects/relocalisation/)), stereo vision ([GC-Net 2017](https://arxiv.org/pdf/1703.04309.pdf)) and visual odometry ([DeepVO 2017](http://ieeexplore.ieee.org/abstract/document/7989236/?reload=true)) are examples.
Deep learning excels at these applications for a few reasons.
Firstly, it is able to learn higher order features which reason over shapes and objects with larger context than point-based classical methods.
Secondly, it is very efficient for inference to simply run a forward pass of a convolutional neural network which approximates an exact geometric function.

Over the last year, I’ve noticed epipolar geometry and reprojection losses improving these models, allowing them to learn with unsupervised learning.
This means they can train without expensive labelled data by just observing the world.
Reprojection losses have contributed to a number of significant breakthroughs which now allow deep learning to outperform many traditional approaches to estimating geometry. 
Specifically, photometric reprojection loss has emerged as the dominant technique for learning geometry with unsupervised (or self-supervised) learning. 
We’ve seen this across a number of computer vision problems:

 - **Monocular Depth**: Reprojection loss for deep learning was first presented for monocular depth estimation by [Garg et al.](https://arxiv.org/abs/1603.04992) in 2016. 
In 2017, [Godard et al.](https://arxiv.org/abs/1609.03677) show how to formulate left-right consistency checks to improve results.
 - **Optical Flow**: this requires training reprojection disparities over 2D and has been demonstrated by [Yu et al. 2016](https://arxiv.org/abs/1608.05842), [Ren et al. 2017](http://www.aaai.org/ocs/index.php/AAAI/AAAI17/paper/download/14388/13940) and [Meister et al. 2018](https://arxiv.org/abs/1711.07837).
 - **Stereo Depth**: in my PhD thesis I show how to extend our stereo architecture, [GC-Net](https://arxiv.org/abs/1703.04309), to learn stereo depth with epipolar geometry & unsupervised learning.
 - **Localisation**: I presented a paper at CVPR 2017 showing how to train relocalisation systems by learning to project 3D geometry from structure from motion models [Kendall & Cipolla 2017](https://arxiv.org/abs/1704.00390).
 - **Ego-motion**: learning depth and ego motion with reprojection loss now out performs traditional methods like ORB-SLAM over short sequences under constrained settings ([Zhou et al. 2017](https://people.eecs.berkeley.edu/~tinghuiz/projects/SfMLearner/)) and ([Li et al. 2017](https://arxiv.org/pdf/1709.06841.pdf)).
 - **Multi-View Stereo**: projection losses can also be used in a supervised setting to learn structure from motion, for example [DeMoN](http://openaccess.thecvf.com/content_cvpr_2017/papers/Ummenhofer_DeMoN_Depth_and_CVPR_2017_paper.pdf) and [SfM-Net](https://arxiv.org/abs/1704.07804).
 - **3D Shape Estimation**: projection geometry also aids learning 3D shape from images in [this work from Jitendra Malik's group](https://arxiv.org/pdf/1704.06254.pdf).

In this blog post I'd like to highlight the importance of epipolar geometry and how we can use it to learn representations of geometry with deep learning.

{% capture fig_img2 %}
![Foo]({{ "/assets/images/godard_depth.gif" | absolute_url }})
{% endcapture %}

<figure>
  {{ fig_img2 | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>An example of state of the art monocular depth estimation with unsupervised learning using reprojection geometry (<a href="https://arxiv.org/abs/1609.03677">Godard et al. 2017</a>)</figcaption>
</figure>

# What is reprojection loss?

The core idea behind reprojection losses is using epipolar geometry to relate corresponding points in multi-view stereo imagery.
To dissect this jargon-filled sentence; epipolar geometry relates the projection of 3D points in space to 2D images. 
This can be thought of as triangulation (see the figure below).
The relation between two 2D images is defined by the Fundamental matrix.
If we choose a point on one image and know the fundamental matrix, then this geometry tells us that the same point must lie on a line in the second image, called the epipolar line (the red line in the figure below).
The exact point of the correspondence on the epipolar line is defined by the 3D point's depth in the scene.

If these two images are from a rectified stereo camera then this is a special type of multi-view geometry, and the epipolar line is horizontal.
We then refer to the corresponding point's position on the epipolar line as disparity.
Disparity is inversely proportional to metric depth.

The standard reference for this topic is the textbook, "Multiple View Geometry in Computer Vision" [Hartley and Zisserman, 2004](http://www.robots.ox.ac.uk/~vgg/hzbook/).

{% capture fig_img %}
![Foo]({{ "/assets/images/epipolar_geometry.svg" | absolute_url }})
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>Epipolar geometry relates the same point in space seen by two cameras and can be used to learn 3D geometry from multi-view stereo (Image borrowed from <a href="https://en.wikipedia.org/wiki/Epipolar_geometry">Wikipedia</a>).</figcaption>
</figure>

One way of exploiting this is learning to match correspondences between stereo images along this epipolar line.
This allows us to estimate pixel-wise metric depth.
We can do this using _photometric_ reprojection loss ([Garg et al. in 2016](https://arxiv.org/abs/1603.04992)).
The intuition behind reprojection loss is that pixels representing the same object in two different camera views look the same. 
Therefore, if we relate pixels, or determine correspondences between two views, the pixels should have identical RGB pixel intensity values.
The better the estimate of geometry, the closer the photometric (RGB) pixel values will match. 
We can optimise for values which provide matching pixel intensities between each image, known as minimising the _photometric_ error.

An important property of these losses is that they are unsupervised. 
This means that we can learn these geometric quantities by observing the world, without expensive human-labelled training data.
This is also known as self-supervised learning.

The list of papers at the start of this post further extend this idea to optical flow, depth, ego-motion, localisation etc. — all containing forms of epipolar geometry. 

# Does this mean learning geometry with deep learning is solved?

I think there are some short-comings to reprojection losses.

Firstly, photometric reprojection loss makes a **photometric consistency assumption**. 
This means it assumes that the same surface has the same RGB pixel value between views. 
This assumption is usually valid for stereo vision, because both images are taken at the same time. 
However, this is not always the case for learning optical flow or multi-view stereo, because appearance and lighting changes over time. 
This is because of occlusion, shadows and the dynamic nature of scenes.

Secondly, reprojection suffers from the **aperture problem**.
The aperture problem is unavoidable ambiguity of structure due to a limited field of view. 
For example, if we try to learn depth by photometric reprojection, our model cannot learn from areas with no texture, such as sky or featureless walls. 
This is because the reprojection loss is equal across areas of homogeneous texture. To resolve the correct reprojection  we need context! 
This problem is usually resolved by a smoothing prior, which encourages the output to be smooth where there is no training signal, but this also blurs correct structure.

Thirdly, we **don’t need to reconstruct everything**. 
Learning to reproject pixels is similar to an auto encoder — we learn to encode all parts of the world equally. 
However, for many practical applications, attention based reasoning has been shown to be most effective. 
For example, in autonomous driving we don’t need to learn the geometry of building facades and the sky, we only care about the immediate scene in front of us. 
However, reprojection losses will treat all aspects of the scene equally.

{% capture fig_img3 %}
![Foo]({{ "/assets/images/context.jpg" | absolute_url }})
{% endcapture %}

<figure>
  {{ fig_img3 | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>State of the art stereo depth estimation from <a href="https://arxiv.org/abs/1703.04309">GC-Net</a>. This figure shows the saliency of the model with respect to the depth prediction for the point with the white cross. This demonstrates the model uses a wider context of the surrounding car and road to make its prediction. </figcaption>
</figure>

# How can we improve performance?

It is difficult to learn geometry alone, I think we need to incorporate semantics. 
There is some evidence that deep learning models learn semantic representations implicitly [from patterns in the data](https://arxiv.org/abs/1412.6856).
Perhaps our models could more explicitly exploit this?

I think we need to reproject into a better space than RGB photometric space. We would like this latent space to solve the problems above.
It should have enough context to address the aperture problem, be invariant to small photometric changes and emphasise task-dependant importance. 
Training on the projection error in this space should result in a better performing model. 

After the flurry of exciting papers in 2017, I'm looking forward to further advances in 2018 in one of the hottest topics in computer vision right now.




_I first presented the ideas in this blog post at the [Geometry in Deep Learning Workshop](https://sites.google.com/site/deepgeometry2017/) at the International Conference on Computer Vision 2017.
Thank you to the organisers for a great discussion._
