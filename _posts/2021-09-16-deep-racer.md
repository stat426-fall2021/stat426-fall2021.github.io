---
title: Reinforcement Racing
layout: post
author: izzy64
post-image: "https://github.com/izzy64/stat426-fall2021.github.io/blob/79069163427dc774ff39efaa3a24ee217359349a/assets/images/deepracer.jpeg"
description: Learn about reinforcement learning on the racetrack
tags:
- reinforcement
- learning
- deep
- racing
---

### What is Reinforcement learning?

In the late 1800s, a psychologist named Ivan Pavlov conducted now famous experiments, proving that over time, dogs could learn to associate the sound of a bell with food. This lead to the concept of classical conditioning, and modern learning theories.

We've known for a long time that incentives change behavior. You can teach a dog tricks by offering treats, and you can improve a child's attitude by offering cookies. Reinforcement learning is applying the same tactics to an artificial intelligence. 

### Reward Functions

But how can we incentivize a computer to behave in the ways we want, when it neither needs or understands a primal desire for food? Or anything for that matter? 

Well, computers have always been a lot better than humans at math, so what if we programmed them to optimize a number? Many reinforcement learning models start with rules for awarding points. This is often called a reward function. Through a process of trial and error, the program will start to discover which behaviors maximize it's points, and it will try successful strategies more often. 

### Amazon DeepRacer

Amazon DeepRacer is a way to learn about and practice reinforcement learning by training a small racecar to drive around a track.  

Here's footage from BYU's 2019 DeepRacer event to give you an idea what it looks like.

<iframe width="560" height="315" src="https://youtu.be/6yUcWqdQH5w" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
https://youtu.be/6yUcWqdQH5w

In machine learning terms, the racetrack is the *environment*. 

The car is an *agent*. An agent is the entity that can take actions, with the consequences of those actions altering the environment, and hopefully 'teaching' the agent to make better decisions. For an Amazon DeepRacer vehicle, the actions it can take are to change the angle of its wheels, and change it's speed. 

The agent regularly receives data about it's *state*. Where is the agent in the environment and what kind of conditions is the car in? What is the turning angle? Are all wheels on the track? How fast is the car going? In addition to all of this, the deepracer vehicle has a camera in the front to take a picture of whats in front of it. The model crunches all this data to decide how the car will drive. 

But you don't make the model. All you write is the reward function, and the model is written and changed as the model trains. During these training simulations, the car drives around a virtual track, and you can watch in real time as the model improves. The racecar will truly learn to drive itself, starting with random decisions and refining them as it gets points in each iteration. 

You'll definitely want at least an hour of training, but eventually, your model may become overfit for the specific track you trained on. The ideal training parameters and time of the training are all part of the secret sauce that makes deepracing fun.

![Simulation](https://github.com/izzy64/stat426-fall2021.github.io/blob/79069163427dc774ff39efaa3a24ee217359349a/assets/images/DRsimulation.png)

### Let's Race!

I challenge you to beat my model (though I doubt it will be very hard). Luckilly, reward functions are written in Python, and aren't complicated to get started with! 

I've created a link where our class can pit our models against each other:
https://console.aws.amazon.com/deepracer/home#raceToken/g_Jv-1ZVQrynlcB1GgLPpg

You'll need to sign up for an AWS account, which would normally require your credit or debit card, but as a student, you can sign up for an AWS educate account and have one year of free-tier computing for free:
https://www.awseducate.com/registration#APP_TYPE

If, like me, you've already timed out of your educate account, don't worry, Amazon offers ten hours of model training/evaluation for free in a generic account (but you do need to supply card details). As always, when working in the cloud, pay attention to costs, know where the free-tier cutoffs are, and keep your login credentials private!

Once you have an account, the free training I've linked below provides everything you need to get started. It's honestly a little addicting watching your little bot scoot around the virtual track while doing training simulations.
https://www.aws.training/Details/eLearning?id=32143

Happy racing!
