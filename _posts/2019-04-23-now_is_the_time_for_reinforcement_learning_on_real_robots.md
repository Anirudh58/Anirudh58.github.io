---
title: "Now is the Time for Reinforcement Learning on Real Robots"
layout: single
read_time: true
comments: true
share: true
author_profile: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/blog/wayve_drone.jpg
excerpt: "<br><br><br>"
categories:
  - reinforcement_learning
tags:
  - robotics
---


The purpose of this post is to encourage more people to work on machine learning algorithms for real-world robots.
End-to-end deep learning has become ubiquitous with most of today's challenging artificial intelligence problems, such as image recognition, natural language processing, protein folding prediction and game playing agents.
In fact, you would probably be laughed at for not using deep learning for these problems.

But the same is not yet true for mobile robotics. Why?

Deep learning has the potential to completely revolutionise mobile robotics. 
It understands vast quantities of data, simplifies engineering and creates representations which generalise beyond anything we can hand-engineer.
We've seen this over and over again in other fields rich in data.
However, today deep learning is typically only seen in isolated parts of mobile robotics systems, such as computer vision front-ends.
Most leading robotics applications rely on hand-engineered control policies, such as [Waymo's self-driving car](https://waymo.com/) or [Boston Dynamic's Atlas](https://www.bostondynamics.com/atlas).

So what are the world's talented machine learning researchers doing about this?
Unfortunately in my experience there are seldom examples of world-leading mobile robotics research labs which also have outstanding machine learning people. 
Many of the strategic leaders in the world's biggest AI labs are reluctant; they are of the opinion that real-world experiments will hold back progress towards A.G.I. (artificial general intelligence).
They see hardware, and the problems (and opportunities) that come with it, as a distraction.
They'd rather iterate more quickly with game-playing agents in simulation from the comfort of their office.
Unfortunately in my experience it's often not possible to transfer these algorithms developed in simulation to real-world robots.

I believe if we are going to see the positive effect of robotics on our society, we need to concentrate more effort on challenging real-world applications with machine learning.
While blogs like "[Deep Reinforcement Learning Doesn't Work Yet](https://www.alexirpan.com/2018/02/14/rl-hard.html)" have some truth today, I think robotics is about to go through its _2012 ImageNet_ moment.
Yes, reinforcement learning may be the [cherry on the cake](https://cdn-images-1.medium.com/max/1600/0*sQmcKODThlssh2V5.png), but the critical component is end-to-end machine learning.
This is what will bring self-driving cars, smart manufacturing and domestic robotics to society before 2030.
Focusing the majority of the world's talent on advancing A.I. with video games (such as StarCraft or DOTA) is coming at a large opportunity cost.

![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/blog/deep_learning_and_robotics1.gif){: .align-center}
![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/blog/deep_learning_and_robotics2.gif){: .align-center}

There are some awesome teams working intensively on machine learning for robotics, but are largely still in the minority.
To share a few in the figure above: [Skydio](https://www.skydio.com/) for drones (top-left), [OpenAI](https://openai.com/) with dexterous manipulation (top-right), 
[Berkeley's](http://rail.eecs.berkeley.edu/) learning manipulation robots (bottom-left) and [Wayve](https://wayve.ai/) with self-driving cars (bottom-right).
We are seeing some progress!
For example, in 2018 our team at [Wayve](https://wayve.ai/) showed two world-firsts for mobile robotics, using deep learning:

 - first example of [deep reinforcement learning on a self-driving car](https://wayve.ai/blog/learning-to-drive-in-a-day-with-reinforcement-learning), learning to lane-follow from 11 episodes of training data.
 - [sim2real](https://wayve.ai/blog/sim2real), where we demonstrated that it is possible to train a robot in simulation, then transfer the policy to the real-world. 
 We drove a car for 3km+ on UK roads using a policy trained only from labelled simulated data using image-to-image translation techniques.

Some of the most important things we learned from this work so far could not have come from studies on static computer vision datasets or simulation alone.
In fact, many times we found standard practices and algorithms in machine learning did not work for real-world robotics. 
I'll spend the rest of this blog discussing a few of these problems and the insights I learned.

# Exploration: it's not a big deal for robotics

A large amount of research in reinforcement learning has focused on the problem of exploration: taking actions in order to learn about the world.
For example, [Montezuma’s Revenge](https://en.wikipedia.org/wiki/Montezuma's_Revenge_(video_game)) is a simulation environment which is notoriously difficult to solve because it requires extreme exploration with infrequent feedback and sparse rewards.
This has challenged researchers, with solutions proposed in 2018, e.g. by [a single demonstration](https://blog.openai.com/learning-montezumas-revenge-from-a-single-demonstration/) or by [Go-Explore](https://eng.uber.com/go-explore/).

However these ideas are of little use in robotics.
In robotics, we typically have data collected by a demonstrator available to us, e.g. by a human or other hand-coded system.
It is simply too dangerous to let a robot randomly explore the world with epsilon-greedy.
In fact, control policies must often be learned from predominantly off-policy data.

The more pressing problem is to be able to learn in a very data-efficient manner, retaining information and avoiding catastrophic forgetting of information.
When we first applied a model-free reinforcement learning algorithm to our self-driving car, [DDPG](https://arxiv.org/abs/1509.02971), it was very difficult to get it to learn quickly, and then to not forget stable policies.
Dealing with the random-ness of random exploration made experiments incredibly stochastic and unreliable.
We found [model-based reinforcement learning](https://wayve.ai/blog/dreaming-about-driving-imagination-rl) to be more repeatable and effective.
This allowed us to learn off-policy with much more deterministic results, with policies which improved with more data.
Ultimately, to scale our driving policy to [public UK roads](https://wayve.ai/blog/driving-like-human), we needed to use expert demonstrations.

# What is the reward in real life?

In real life, there is no game score we need to optimise, unlike in Atari games. 
Philosophers have debated for millennia what optimal behavior is, but the answer to key questions such as the [Trolley Problem](http://moralmachine.mit.edu/) is still still unclear.

I've thought a lot about how to design a reward for self-driving. 
We can't use privileged information like 'distance to lane' which is available in simulation.
If we want to be data-efficient it can't be sparse, such as 'did we get safely to the destination'.
We can't learn by failure in the real-world as it is unsafe (well maybe sometimes we can... see [Gandhi et al. 2017](https://arxiv.org/abs/1704.05588)).

It is important to note that for mobile robotics, train environment != test environment. 
Unlike other academic literature, we should not report best case, but worst case.
The reward should encourage generalisation, robustness and safety.

For an interesting anecdote for reward design, we observed that when our car was trained with the reward to drive as far as possible without safety driver intervention, it learned to zig-zag down the road, as it didn't leave the lane and cause intervention, but drove a greater distance by zig-zaging, therefore maximising the reward.
This is a phenomenon known as reward hacking, where the agent earns reward using unintended behavior.
For an excellent treatment of reward-hacking and other problems in AI safety, see [Amodei et al. 2016](https://arxiv.org/abs/1606.06565).

I believe ideas like reward-learning, inverse reinforcement learning, preference learning and imitation learning are going to be very important to real-life robotics.
Ultimately, the best reward will be learned from demonstration and feedback.

# Combining computer vision and control

There are not many reinforcement learning systems that work with computer vision.
There are also not many reinforcement learning systems that work with state-spaces with millions of dimensions.
Therefore if our robots are going to work with mega-pixel camera sensors, we are going to need to learn policies that combine RL and computer vision.

This is not as trivial as taking a semantic segmentation representation and passing it to a policy or value function.
The representation needed for control is different from recognition problems.
In contrast, most state-of-the-art semantic segmentation algorithms, like [PSPNet](https://arxiv.org/abs/1612.01105) or [DeepLab](https://arxiv.org/abs/1706.05587), don't compress the state.
They explicitly design architectures to retain features with large spatial resolution because this performs better at the IoU metric used for this task.
For example, with a 1000 x 1000 x 3 RGB pixel input (1 megapixel), the resulting feature representation from [DeepLabV3](https://arxiv.org/abs/1706.05587) is a tensor with dimensions 125 x 125 x 256.
This hasn't compressed the state - it has expanded it by a factor of 1.33!

We need to design computer vision systems which compress the state and learn features relevant for the control task.
Fortunately supervised learning is very good at learning [semantics, motion and geometry](https://arxiv.org/abs/1705.07115).

But what are the metrics we need to optimise? Counter-intuitively, I've often seen systems which perform better at computer vision metrics be worse representations to use for learning control.
We don't care about the pixel accuracy of segmentation masks in order to interact with an object. 
The robustness of object detection is more essential. 
We need to focus on the right semantics, geometry and motion representations and metrics.

This requires a new attitude towards computer vision metrics. Improving IoU or accuracy metrics on computer vision problems are often no longer a good proxy for improving the end-to-end control system.
When we get to 90%+ performance on a computer vision task, it now becomes more important to learn the right representation, rather than improving the metric.

# Learning with noisy data

Real data is noisy.
Datasets like [KITTI](http://www.cvlibs.net/datasets/kitti/) and [CityScapes](https://www.cityscapes-dataset.com/) are painstakingly labelled and cleaned.
But their scope is tiny, to build real world robots we need to learn on much more vast datasets.
Perhaps the [Oxford Robot Car dataset](https://robotcar-dataset.robots.ox.ac.uk/) is much more representative of what real data at scale looks like.

One interesting observation I've made, is that on clean computer vision benchmark datasets, methods which increase the weighting of hard data points perform better.
Recently examples include [focal-loss](https://arxiv.org/abs/1708.02002) and other hard mining or loss weighting techniques.
However, these methods are less effective on real-data, where hard data points are due to noise, not learning difficulty.

In contrast, probabilistic deep learning (see my [previous blog here](/computer_vision/bayesian_deep_learning_for_safe_ai/)) down-weights noisy data points.
These approaches perform worse on clean benchmark computer vision datasets.
However, in the real-world, probabilistic deep learning often performs better than hard-negative-mining approaches.
This is because it down-weighs the most noisy examples, reducing errors.

![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/blog/wayve_twizy.jpg){: .align-center}

# Summary

If we take the approach of, 'let's solve A.G.I. in simulation first and only then let's solve it in the real-world', we are not going to see real benefits of intelligent robotics in the near future.
There is a huge opportunity to work on A.I. for robotics today.
Hardware is cheaper, more accessible and reliable than ever before.
I think mobile robotics is about to go through the revolution that computer vision, NLP and other data science fields have seen over the last five years.

Autonomous driving is the ideal application to work on. Here's why; the action space is relatively simple. 
Unlike difficult strategy games like [DOTA](https://openai.com/five/), driving does not require long term memory or strategy.
At a basic level, the decision is either left, right, straight or stop. 
The counter point to this is that the input state space is very hard, but computer vision is making [remarkable progress](https://wayve.ai/blog/2018/10/8/vision-for-driving-with-deep-learning) here. 

If you share my excitement and want to work with me at [Wayve](https://wayve.ai/) on deep learning for autonomous vehicles, please get in touch: [wayve.ai/careers](https://wayve.ai/careers)


---

> Thank you to my team who make this work possible and to my friends who gave feedback on this post before publication.