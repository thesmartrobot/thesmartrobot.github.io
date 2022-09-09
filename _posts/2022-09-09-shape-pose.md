---
layout: post
title: "Disentangling Shape and Pose"
subtitle: "Grab 'm by the handle"
author: "Stefano Ferraro"
background: '/img/bg-franka.png'
paper:
video: '/img/10_moveto_mug.gif'
---

## Intro

In our daily lives, we manipulate and interact with hundreds of objects
without even thinking. In doing so, we make inferences about an 
object's identity, location in space, 3D structure, look and feel. 
In short, we learn a generative model of how objects come about. Robots 
however still lack this kind of intuition, and struggle to consistently 
manipulate a wide variety of objects.

<div style="display:flex; justify-content: center;">
  <img alt="reacher easy task, with a bigger goal sphere: successful execution" width="60%" src="/img/10_robot_fail.gif">
</div>


Following up from [our previous work](https://thesmartrobot.github.io/2021/08/26/thousand-brains.html) we opted for 
an object-centric representation to tackle the problem at hand. In 
order to further generalize the structure of the world around, us we opted for a disentanglement between 
shape and pose in the object-centric representation. For example, we encounter mugs in all kinds of shapes,
yet we all take them by the handle. By adopting a 
disentangled object-centric generative models we can equip a robot with 
the ability to reason about shape and pose of different object categories, 
and generalize to novel instances of these categories. 

## Disentangled representations

In deep learning, when encoding information, we generally do not worry 
about how the information is distributed in the learned latent space. 
We are mainly interested that all the relevant information are encoded in the latent 
dimensions. A disentangled representation however is one where changes in one (or a few) latent dimension 
are sensitive to changes in only one generative factor, while remaining invariant 
to changes in other factors. In our case, for a class of objects we want to disentangle the shape 
of the specific instance at hand and the pose of it. Hence, if we want to reach for
an object from a certain pose, we can focus on the pose latent only, and generalize to any shape.

In our experiments we trained different models for different 
categories of the ShapeNet dataset. We then visualize imagined objects by varying the latent vectors.
On the left, we only vary the shape latent, in the center we vary the pose latent, and on the right, we vary both. 

<div style="display:flex; justify-content: center;">
  <img alt="bottle morphing" width="70%" 
src="/img/10_bottle_merge.gif"><br/>
  <img alt="mug morphing" width="70%" 
src="/img/10_mug_merge.gif">
</div>
<br/>

## Can it generalize?

So now we have showed that our models can indeed disentangle shape and pose, does it help to generalize?
To put this to the test, we use a simulated 3D environment in which an [active inference](https://thesmartrobot.github.io/2020/05/27/active-inference.html) agent can move
the camera around, pointing towards the object. When we now give the agent a preferred view of a mug, it should
in theory be able to reach the same pose of novel, previously unseen mugs.
The animation below shows some of our obtained results. 
On the left, you see an example pose for a specific instance of a mug, and on the right, you see
the actions of our active inference agent to reach a similar pose for 5 different novel mug instances.


<div style="display:flex; justify-content: center;">
  <img alt="move to goal pose" width="100%" 
src="/img/10_moveto_mug.gif">
</div>
<br/>

## Next steps

Learning how to interact with different kinds of objects, and generalizing to novel instances of known object categories is paramount for
building intelligent robot manipulators. This work is a first step in this direction, enabling to disentangle shape and pose.
As a next step, we plan apply this beyond the ShapeNet dataset, and experiment with more complex, real-world objects and a robotic manipulator.

Are you curious on how we trained our models, check out the paper, or check out my talk at the [International Workshop on Active Inference (IWAI)](https://iwaiworkshop.github.io/)!
