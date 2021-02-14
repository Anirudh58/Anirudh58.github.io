---
title: "Let's Talk About Ethics in Artificial Intelligence"
layout: single
read_time: true
comments: true
share: true
author_profile: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/rise_of_robots.jpg
excerpt: "Ethics in Algorithms: Trust, Fairness, Honesty<br><br><br>"
categories:
  - artificial_intelligence
tags:
  - trust
  - fairness
  - honesty
---

When I am in the pub and I tell people I am working on Artificial Intelligence (AI) research, the conversation that invariably comes up is, "Why are you building machines to take all our jobs?"
However, within AI research communities, this topic is rarely discussed.
My experience with colleagues is that it is often dismissed with off-hand arguments such as, "We'll make more advanced jobs to replace those which are automated".
I'd like to pose the question to all AI researchers: how long have you actually sat down and thought about ethics?
Unfortunately, the overwhelming opinion is that we just build the tools and ethics are for the end-users of our algorithms to deal with.
But, I believe we have a professional responsibility to build ethics into our systems from the ground up.
In this blog I'm going to discuss how to build ethical algorithms.

How do we implement ethics? There are a number of ethical frameworks which philosophers have designed;
[virtue ethics](https://en.wikipedia.org/wiki/Virtue_ethics) (Aristotle), [deontological ethics](https://en.wikipedia.org/wiki/Deontological_ethics) (Kant) and [teleological ethics](https://en.wikipedia.org/wiki/Teleology) (Mill, Bentham).
However Toby Walsh, Professor of AI at the University of New South Wales in Australia, has a different view:

> "For too long philosophers have come up with vague frameworks. Now that we have to write code to actually implement AI, it forces us to define a much more precise and specific moral code"

Therefore, AI researchers may even have an opportunity to make fundamental contributions to our understanding of ethics!
I have found it interesting to think about what ethical issues such as trust, fairness and honesty mean for AI researchers.

# Concrete ethical issues for machine learners

In this section I am going to discuss concrete ways to implement trust, fairness and honesty in AI models.
I will try to translate these ethical topics into actual machine learning problems.

## Trust

It is critical that users trust AI systems, otherwise their acceptance in society will be jeopardised. 
For example, if a self-driving car is not trustworthy, it is unlikely anyone will want to use it.
Building trustworthy algorithms means we must make them safe by:

 - improving accuracy and performance of algorithms. We are more likely to trust something which is accurate.
 This is something which most machine learning researchers do,
 - designing algorithms which are aware of their uncertainty and understand what they do not know. 
 This means they will not make ill-founded decisions.
 See a previous blog I wrote on [Bayesian deep learning](/computer_vision/bayesian_deep_learning_for_safe_ai/) for some ideas here,
 - making well-founded decision making or control policies which do not over-emphasise exploration over exploitation.

## Fairness

We have a responsibility to make AI fair. This means to remove unwanted bias in algorithms.
Unfortunately, there are many examples of biased / unfair AI systems today. For example:

 - systems used to estimate re-offending risk in the US are [biased towards African-Americans](https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing),
 - Google's voice recognition system has been shown to [systematically perform better with male voices rather than female voices](https://makingnoiseandhearingthings.com/2016/07/12/googles-speech-recognition-has-a-gender-bias/),
 - most self-driving cars are biased to training data in California.

There are in-fact many sources of bias in algorithms. 
For an excellent taxonomy, see [this paper](https://www.cmu.edu/dietrich/philosophy/docs/london/IJCAI17-AlgorithmicBias-Distrib.pdf).
In some situations we even want bias - but this is something we must understand.
Concrete problems to improve fairness and improve bias in AI systems include:

 - improving data efficiency to better learn rare classes,
 - improve methodologies for collecting and labelling data to remove training data bias,
 - improved causal reasoning so we can remove an algorithm's access to explanatory variables which we deem morally unusable (e.g. race).

## Honesty

Honesty requires algorithms to be transparent and interpretable.
We should expect algorithms to provide reasonable explanations for the decisions they make.
This is going to become a significant commercial concern in the EU when the [new GDPR data laws](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) go into effect in 2018.
They grant users the right to a logical explanation of how an algorithm uses our personal data.
This is going to require advances in:

 - saliency techniques which explain causality from input to output,
 - interpretablity of black box models. Models must be able to explain their reasoning. 
 This may be by forward simulation of an internal state or by analysing human interpretable intermediate outputs.

# Will we be accountable for the AI we build?

Perhaps of more immediate concern to AI researchers is if we will be accountable for the algorithms we build.
If a self-driving car fails to obey the road rules and kills pedestrians, is the computer vision engineer at fault?
Another interesting example is the venture capitalist Deep Knowledge, who [placed an AI on their board](http://www.bbc.com/news/technology-27426942) of directors in 2014.
What happens if this AI fails in its responsibilities as company director?
Today, AI cannot be legally or criminally accountable as it has no legal entity and owns no assets.
This means liability lies with the manufacturer.

Unfortunately, it is unlikely we will be able to get insurance to cover liability of autonomous systems. 
This is because there is a total lack of data on them.
Without these statistics, insurance firms are unable to estimate risk profiles.

Most professional bodies (law, medicine, engineering) regulate standards and values of their profession.
In my undergraduate engineering school we had compulsory courses on professional standards and ethics.
Why do most computer science courses not do the same?

Medical research trials involving humans have to pass several ethics committee processes before being admitted.
I don't think we need the same approval before running a deep learning experiment, but I think that there needs to be more awareness from the tech world. 
For example, in 2014 [Facebook conducted human subject trials](https://www.theguardian.com/technology/2014/jun/29/facebook-users-emotions-news-feeds) which were widely condemned. 
They wanted to see if they could modify human emotion by changing the types of content shown in their newsfeed.
Is this ethical? Did the 689,000 people involved willingly consent?
Why are tech companies exempt from the ethical procedures we place on other fields of research?

# Is AI going to steal our jobs?

Going back to the original question I was asked in the pub, "will robots steal our jobs?" I think there are some real concerns here.

The AI revolution will be different to the industrial revolution. The industrial revolution lasted 100 years, which is 4 generations. 
This was sufficient time for subsequent generations to be re-skilled in their jobs of the future.
The disruptive technology due to AI is likely to occur much more rapidly (perhaps a single generation). 
We will need to re-skill within our lifetime, or else become jobless.

It is worth noting that in some situations, AI is going to increase employment. 
For example, AI is drastically improving the efficiency of matching Kidney donors to those with Kidney disease, increasing the work for surgeons. 
But these will certainly be isolated examples.
Disruptive AI technology is going to displace many of today's jobs. 

Hopefully automation will drastically reduce the cost of living.
Perhaps this places less pressure to have a job to work for money. 
But it is well-known that humans need to feel self-worth to feel happy. 
Perhaps entertainment and education will be enough for many people?

For those for whom it is not, we need to shift to a new distribution of jobs, quickly. Here are some positive ideas I like:
 - reactive retraining of those who have jobs displaced by automation. For example, Singapore has a [retraining fund](http://www.skillsfuture.sg/) for people who have been replaced by automation,
 - proactive retraining, for example changing the way we teach accountants and radiologists today, because their jobs are being displaced,
 - allow automation to increase our leisure time,
 - redeploy labour into education and healthcare which require more human interaction than other fields,
 - [MOOCs](https://en.wikipedia.org/wiki/Massive_open_online_course) and other educational tools,
 - introducing a living wage or universal basic income.
 
Eventually, perhaps more extreme regulation will be needed here to keep humans commercially competitive with robots.


---


_Acknowledgements: I'd like to thank Adrian Weller for first opening my eyes to these issues.
This blog was written while attending the International Joint Conference on Artificial Intelligence (IJCAI) 2017
where I presented a paper on [autonomous vehicle safety](https://www.ijcai.org/proceedings/2017/0661).
Thank you to the conference organisers for an excellent forum to discuss these topics._
