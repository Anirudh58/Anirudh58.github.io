---
layout: single
read_time: false
comments: false
share: false
title: Research
permalink: /research/
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/gt.jpg
  caption: ""
excerpt: ""
---

> ### EXPLORATORY VIDEO ANALYTICS (2022)

- <small> EVA is a visual data management system (think MySQL for videos). It supports a declarative language similar to SQL and a wide range of commonly used computer vision models. I have been working on this project with the Georgia Tech Database Research group, advised by [Prof. Joy Arulraj](https://www.cc.gatech.edu/~jarulraj/) since Fall 2021. </small>
- <small> See repo [here](https://github.com/georgia-tech-db/eva) to know more. </small>

> ### ANOMALOUS CONTENT FROM SURVEILLANCE VIDEOS (2019)

- <small> One of the main driving goals behind this project is the high number of false positivies typically associated with naive monitoring systems. For eg. Surveillance cameras in smarthomes send alerts to the user every time it detects motion. We wanted to see if it's possible to reduce such high false alerts. </small>
- <small> We used Facebook's [C3D](https://research.fb.com/blog/2014/12/c3d-generic-features-for-video-analysis/) to extract spatiotemporal features from videos taken from the [UCF-Crimes dataset](https://webpages.uncc.edu/cchen62/dataset.html) and fed them to a multi-input CNN. Modeling it as a multi-classification problem didn't give great results due to very limited training set, however, the model was able to sufficiently correlate highly anomalous segments of a video with high regression scores. </small> 
- <small> This [publication](https://ieeexplore.ieee.org/document/9092161) was accepted and presented at ICinPro-2019. This being my first research project, helped me learn a lot of interesting things. I also realized the immense complexity/scope in the domain of video understanding and instilled in me a desire to learn more. </small> 