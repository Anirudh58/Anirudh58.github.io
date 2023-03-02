---
layout: single
read_time: false
comments: false
share: false
title: "<br><br><br>  Recent Work"
permalink: /work/
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/gt.jpg
  caption: ""
excerpt: ""
---

> ### EXPLORATORY VIDEO ANALYTICS (2022)

- <small> EVA is a visual data management system (think MySQL for videos). It supports a declarative language similar to SQL and a wide range of commonly used computer vision models. The key idea behind EVA is that simple to moderate analysis on videos should be as easy as writing SQL queries. </small>

- <small> This is a sample query to run an emotion detector on all faces in a video and the corresponding output. Without EVA, such a task would require a lot of boilerplate code to extract the faces and run the emotion detector on each of them, assuming you have the models in the first place.

```sql
  SELECT id, bbox, EmotionDetector(Crop(data, bbox)) 
  FROM MyVideo JOIN LATERAL UNNEST(FaceDetector(data)) AS Face(bbox, conf);
```

<!-- <img src="/assets/images/gangubai-output.webp" alt="query_output" height="400" width="500" style="display: block; margin: auto;"/> -->
[ ![](/assets/images/gangubai-output.gif) ](/assets/images/gangubai-output.gif)

- <small> This is a running project as part of the [Georgia Tech Database Research Group](https://db.cc.gatech.edu/). I worked with the team on this for 3 semesters as part of my Masters project, with primary contributions from the ML side. See [project docs](https://evadb.readthedocs.io/en/stable/) to know more. </small>


> ### USING BILINEAR CNNs FOR VEHICLE MAKE AND MODEL PREDICTION (2022)

- <small> In this project, we have taken up a fine-grained classification of predicting a vehicle's make and model given an input image of a vehicle using various neural networks. We used [VMMRdb](https://github.com/faezetta/VMMRdb) as the main dataset source.</small>
- <small> We compared the performance of 3 methods. Transfer learning with various backbone models (ResNet18, ResNet50, MobileNetv2), Bilinear CNNs and Vision Transformers. As the number of labels increased, we found that Bilinear CNNs outperformed the other networks in terms of accuracy, as it was able to learn the fine details better. This poster summarizes our findings. 

<!-- <img src="/assets/images/vp_poster.jpg" alt="vp_poster" height="500" width="700" style="display: block; margin: auto;"/> -->
<!-- <img src="/assets/images/vp_test_images.png" alt="vp_poster" height="300" width="400" style="display: block; margin: auto;"/> -->
[ ![](/assets/images/vp_poster.jpg) ](/assets/images/vp_poster.jpg)

- <small> This project was done as part of CS 7643 (Deep Learning). Please find the code [here](https://github.com/Anirudh58/vehicle-predictor) and the research report [here](https://github.com/Anirudh58/vehicle-predictor/blob/main/Vehicle_Predictor_Final_Report.pdf) </small>

> ### EMOJI CATEGORY AND POSITION PREDICTION IN TEXT PASSAGES (2022)

- <small> Curated a new dataset by scraping and cleaning emoji information along with character and word level index for about 350K tweets. </small>
- <small> Implemented a Bi-LSTM network with pre-trained GloVe embeddings for predicting the type and position of an emoji given a text.
Achieved 62% accuracy in emoji prediction (modeled as a top-10 clustering problem) and a 78% accuracy in position prediction. The table below show some examples of the predictions. 

[ ![](/assets/images/ep_preds.jpg) ](/assets/images/ep_preds.jpg)

- <small> This project was done as part of CS 7650 (Natural Language). Please find the repo [here](https://github.com/Anirudh58/emoji-prediction) and the research report [here](https://github.com/Anirudh58/emoji-prediction/blob/main/report.pdf) </small>


> ### JINGLECRAFT - MACHINE LEARNING IN MUSIC (2022)

- <small> This project is an in-depth analysis of various ML algorithms and Data visualizations for Genre Classification and Mood Prediction. </small>
- <small> We used a combination of the Million Song Dataset, GTZAN and Spotify API as our dataset source. Our models and visualizations
were based on both spectral features (mel-spectrogram) as well as metadata features. </small>
- <small> This project was done as part of CS 7641 (Machine Learning). The comprehensive report can be found [here](https://vaibhavb007.github.io/jinglecraft/) </small>


> ### PNEUMONIA DETECTION (2021)

- <small> I have always been fascinated by the applications of AI in health. I envision a future where, basic health services powered by AI, are provided free of cost. Especially, in the remote areas where it's not easy for people to consult doctors even for simple health problems. </small>
- <small> Here, I used the [Kaggle CoronaHack -Chest X-Ray-Dataset](https://www.kaggle.com/praveengovi/coronahack-chest-xraydataset) to train a simple network to differentiate a healthy chest and a pneumonic chest. </small>
- <small> See repo [here](https://github.com/Anirudh58/pneumonia-detection) for sample evaluations. </small>


> ### EXPERIMENTATION WITH VIDEO QUERIES ON DRIVING DATASETS (2021)

- <small> Worked on a simple, configurable [implementation](https://github.com/Anirudh58/berkeley_deepdrive_experimentation) to pre-train a network over FasterRCNN and similar models. </small>
- <small> I used the [Berkeley Deep Drive](https://bdd-data.berkeley.edu/) dataset for this task targetting specific labels of choice like cars, signs, pedestrians etc. It is configurable to scale for more labels with minor tweaks. Below is a demo for a sample query. </small>

```
  Sample every 3 seconds and get all timestamps with more than 2 cars, 1 sign and 1 pedestrian.
```

[ ![](/assets/images/bdd_demo.gif) ](/assets/images/bdd_demo.gif)

- <small> Found this dataset super interesting because of how comprehensive it is. Would definitely want to experiment more, especially on ideas related to autonomous driving in the future (lane segmentation, steering prediction, etc.). </small>


> ### CRICBOARD (2021)

- <small> Cricboard is a cricket statistics page, aimed to provide cool insights to users in a dynamic, interactive UI. One of the main motivations to build something like this is the potential usage in fantasy league contests. Head over to the FAQ section at [cricboard](http://cricboard.in) to know more! </small>
- <small> Received over 30k page hits on the opening day of IPL 2021, and consistently had a daily average of 1k-2k page hits until covid decided to end the tournament.  </small>
- <small> We have made the code for this website public now. Do check it out [here](https://github.com/Anirudh58/cricboard). If you have ideas for better features, visualization ideas etc. please do feel free to issue PRs. </small>


> ### SUBWAY-SURFER (2020)

- <small> This was a fun, little project I worked on during the 2020 lockdown, aimed to keep people fit at home. Idea is to use standard Computer Vision techniques to capture body motions and use that as inputs to any game. I chose subway surfer due to it's simplicity and popularity. I was surprised how little code is required to build such interesting applications these days. </small>
- <small> Hope to find inspiration/time to work on some major improvements (scaling to any user environment, reducing latency, maybe even building a simple mobile app?). You can check out the project [here](https://github.com/Anirudh58/subway_surfer) and maybe even issue PRs or send suggestions. </small> 


> ### ANOMALOUS CONTENT FROM SURVEILLANCE VIDEOS (2019)

- <small> One of the main driving goals behind this project is the high number of false positivies typically associated with naive monitoring systems. For eg. Surveillance cameras in smarthomes send alerts to the user every time it detects motion. We wanted to see if it's possible to reduce such high false alerts. </small>
- <small> We used Facebook's [C3D](https://research.fb.com/blog/2014/12/c3d-generic-features-for-video-analysis/) to extract spatiotemporal features from videos taken from the [UCF-Crimes dataset](https://webpages.uncc.edu/cchen62/dataset.html) and fed them to a multi-input CNN. Modeling it as a multi-classification problem didn't give great results due to very limited training set, however, the model was able to sufficiently correlate highly anomalous segments of a video with high regression scores. </small> 
- <small> This [publication](https://ieeexplore.ieee.org/document/9092161) was accepted and presented at ICinPro-2019. This being my first research project, helped me learn a lot of interesting things. I also realized the immense complexity/scope in the domain of video understanding and instilled in me a desire to learn more. </small> 
