---
layout: single
read_time: false
comments: false
share: false
title: "Projects"
permalink: /projects/
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/nitt.jpg
  caption: ""
excerpt: "Some recent projects in chronological order"
---

> ### BERKELEY DEEPDRIVE (2021)

- <small> Worked on a simple, configurable [implementation](https://github.com/Anirudh58/berkeley_deepdrive_experimentation) to pre-train a network over FasterRCNN and similar models. </small>
- <small> I used the [Berkeley Deep Drive](https://bdd-data.berkeley.edu/) dataset for this task targetting specific labels of choice like cars, signs, pedestrians etc. It is configurable to scale for more labels with minor tweaks. </small>
- <small> Found this dataset super interesting because of how comprehensive it is. Would definitely want to experiment more, especially on ideas related to autonomous driving in the future (lane segmentation, steering prediction, etc.). </small>

> ### CRICBOARD (2021)

- <small> Cricboard is a cricket statistics page, aimed to provide cool insights to users in a dynamic, interactive UI. Head over to the FAQ section at [cricboard](http://cricboard.in) to know more! </small>


> ### SUBWAY-SURFER (2020)

- <small> This was a fun, little project I worked on during the 2020 lockdown, aimed to keep people fit at home. Idea is to use standard Computer Vision techniques to capture body motions and use that as inputs to any game. I chose subway surfer due to it's simplicity and popularity. I was surprised how little code is required to build such interesting applications these days. </small>
- <small> Hope to find inspiration/time to work on some major improvements (scaling to any user environment, reducing latency, maybe even building a simple mobile app?). You can check out the project [here](https://github.com/Anirudh58/subway_surfer) and maybe even issue PRs or send suggestions. </small> 


> ### ANOMALOUS CONTENT FROM SURVEILLANCE VIDEOS (2019)

- <small> We used Facebook's [C3D](https://research.fb.com/blog/2014/12/c3d-generic-features-for-video-analysis/) to extract spatiotemporal features from videos taken from the [UCF-Crimes dataset](https://webpages.uncc.edu/cchen62/dataset.html) and fed them to a multi-input CNN. Modeling it as a multi-classification problem didn't give great results due to very limited training set, however, the model was able to sufficiently correlate highly anomalous segments of a video with high regression scores. </small> 
- <small> This [publication](https://ieeexplore.ieee.org/document/9092161) was accepted and presented at ICinPro-2019. This being my first research project, helped me learn a lot of cool stuff. I also realized the immense complexity/scope in the domain of video understanding and instilled in me a desire to learn more. </small> 


> ### REAL-TIME HOME AUDIO MONITORING SYSTEM (2019)

- <small> Worked on this proposal as part of Samsung's home monitoring solutions. Aim was to detect some household emergency sounds through our home assistant (without compromising user privacy) and accordingly send real-time alerts to users.  </small>
- <small> It was interesting to see how an audio problem was converted to a Computer Vision problem statement with the help of Mel Spectrograms. I used [yamnet](https://github.com/tensorflow/models/tree/master/research/audioset/yamnet) as the dataset and experimented with building networks from scratch. However, using a pretrained network, fine-tuned with our target sounds (baby-cry, dog-bark, cooker whistle etc.,) gave the best performance. I was also able to successfully port this as a real-time solution on our home assistant and demo it. </small> 


> ### PRODUCTIVITY CHATBOT (2019)

- <small> Worked on this [project](https://drive.google.com/file/d/150PzQSZqPvX9ytX8juFgM9AssuoHY2Wc/view?usp=sharing) during an internal samsung hackathon aimed at improving employer efficiency. </small>
- <small> Demonstrated the ability to learn simple actions (commits, deploys, logging etc.,) from users and reuse anytime later through the bot. </small>
- <small> Long term goal was to integrate this chatbot to our internal messenger to event assist employees in doing daily simple tasks like booking meeting rooms, applying leave, etc.</small> 


> ### EMOJI PREDICTION SYSTEM - UNDERGRAD THESIS (2018)

- <small> The foundations I acquired in my summer internship motivated me to pick a project in the NLP domain for my final year project. Interested by emojis and how they can give a deeper idea behind sentiments involved, we developed an Emoji Prediction System under the guidance of [Dr. A Santhana Vijayan](https://www.nitt.edu/home/academics/departments/cse/faculty/vijayan/). </small>
- <small> We built a Network fed by pre-trained GloVe embeddings on a dataset of 10000 tweets as they represent an informal typing pattern and are a great source of emojis. We were able to achieve an accuracy of 56% by modelling this as a multi-class problem statement targeting the top 30 most used emojis.</small> 


> ### KEYBOARD INSIGHTS - SUMMER INTERNSHIP (2017)

- <small> Worked on this project during my summer internship at [Samsung](https://research.samsung.com/sri-b) with the On-Device AI team. Broad aim of this project was to capture important keyboard insights, without compromising user privacy (NER Masking etc.,). I also ended up building a web-based proposal of a language model to perform autocorrections and next-word predictions assisted by local history. </small>


