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

- <small> EVA is a visual data management system (think MySQL for videos). It supports a declarative language similar to SQL and a wide range of commonly used computer vision models. The key idea behind EVA is that simple to moderate analysis on videos should be as easy as writing SQL queries. </small>
- <small> See [here](https://evadb.readthedocs.io/en/stable/) to know more. </small>

> ### USING BILINEAR CNNs FOR VEHICLE MAKE AND MODEL PREDICTION (2022)

- <small> In this project, we have taken up a fine-grained classification of predicting a vehicle's make and model given an input image of a vehicle using various neural networks. We used [VMMRdb](https://github.com/faezetta/VMMRdb) as the main dataset source.</small>
- <small> We compared the performance of 3 methods. Transfer learning with various backbone models (ResNet18, ResNet50, MobileNetv2), Bilinear CNNs and Vision Transformers. As the number of labels increased, we found that Bilinear CNNs outperformed the other networks in terms of accuracy, as it was able to learn the fine details better. </small>
- <small> This project was done as part of CS 7643 (Deep Learning). Please find the code [here](https://github.com/Anirudh58/vehicle-predictor) and the research report [here](https://github.com/Anirudh58/vehicle-predictor/blob/main/Vehicle_Predictor_Final_Report.pdf) </small>

> ### EMOJI CATEGORY AND POSITION PREDICTION IN TEXT PASSAGES (2022)

- <small> Curated a new dataset by scraping and cleaning emoji information along with character and word level index for about 350K tweets. </small>
- <small> Implemented a Bi-LSTM network with pre-trained GloVe embeddings for predicting the type and position of an emoji given a text.
Achieved 62% accuracy in emoji prediction (modeled as a top-10 clustering problem) and a 78% accuracy in position prediction. </small>
- <small> This project was done as part of CS 7650 (Natural Language). Please find the repo [here](https://github.com/Anirudh58/emoji-prediction) and the research report [here](https://github.com/Anirudh58/emoji-prediction/blob/main/report.pdf) </small>

> ### ANOMALOUS CONTENT FROM SURVEILLANCE VIDEOS (2019)

- <small> One of the main driving goals behind this project is the high number of false positivies typically associated with naive monitoring systems. For eg. Surveillance cameras in smarthomes send alerts to the user every time it detects motion. We wanted to see if it's possible to reduce such high false alerts. </small>
- <small> We used Facebook's [C3D](https://research.fb.com/blog/2014/12/c3d-generic-features-for-video-analysis/) to extract spatiotemporal features from videos taken from the [UCF-Crimes dataset](https://webpages.uncc.edu/cchen62/dataset.html) and fed them to a multi-input CNN. Modeling it as a multi-classification problem didn't give great results due to very limited training set, however, the model was able to sufficiently correlate highly anomalous segments of a video with high regression scores. </small> 
- <small> This [publication](https://ieeexplore.ieee.org/document/9092161) was accepted and presented at ICinPro-2019. This being my first research project, helped me learn a lot of interesting things. I also realized the immense complexity/scope in the domain of video understanding and instilled in me a desire to learn more. </small> 