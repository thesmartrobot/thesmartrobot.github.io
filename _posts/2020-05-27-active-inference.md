---
layout: post
title: "Active inference explained"
subtitle: "A self-fulfilling prophecy"
author: "Tim Verbelen"
background: '/img/bg-franka.png'
#paper: https://arxiv.org/abs/1904.08149
---


I often get put in the position in which I have to explain to other researchers, colleagues, friends or family what I am working on, which typically ends up in a primer on active inference. It occurred to me that, besides the scientific literature, there aren't many sources that explain the subject in layman's terms. Therefore, I decided to devote this first blog post to the topic.

## Intelligent Agents

Active inference is a general principle by which autonomous, intelligent agents can operate in their environment [^1]. Agents can perceive the environment by means of sensory observations. For examples we humans can see the world through our eyes, hear sounds with our ears, or touch the environment with our hands. Similarly, a robot can "see" it's environment with a camera, "hear" sounds with a microphone, or "touch" the environment with a bump sensor. At the same time, agents can interact with the environment through actions. We can move our arms and legs to walk around, pick up and move objects, etc. Similarly a robot can control it's motors to drive wheels, move arm segments or open and close a gripper. Inevitably, the agent's actions have an effect on what it will perceive next, which will appear crucial in defining it's behaviour.


## The Generative Model

In order to deliberately choose it's next action, an agent needs to plan ahead it's course of actions and their effect. This entails building an internal model of the external world, and linking causes to their effects. The agent uses this model to infer beliefs over the state it's environment is in, and to predict future sensory observations that result from certain actions. We call this a generative model as it allows the agent to *generate* possible percepts in the future.   


## Free Energy

Active inference rests upon the Free Energy principle, which basically posits that in order to exist, an entity needs to minimize it's Free Energy, or, simply put, it's prediction error or surprise. In the context of our agent, this boils down to making sure that what it perceives is close to what was predicted by it's generative model. 

Basically, an agent has two ways to minimize it's Free Energy. On the one hand, the agent can update it's generative model to better match the sensory observations it has experienced through the course of it's lifetime. This entails learning how the world works, and learning how actions can affect the world, hence minimizing the prediction error. On the other hand, the agent can select the actions that will most likely yield observations that conform with it's generative model. For example the agent will avoid ambiguous states, and will be attracted to following kind of habits for which it *knows* that they will have a certain effect. In this regard, planning becomes an inference problem: infer the actions that will yield the minimal Free Energy, hence *active* inference.


## What do you believe about yourself?    

Crucially, the generative model is not only made up by past experiences. It also constitutes a prior about what you believe you are, what your goal and preferences are. This means that a priori, your generative model assumes you will reach your goals and preferences, and consequently, you will infer actions that in the end realize these goals, by active inference. Therefore, by equipping an agent with a prior model about it's goals and engaging it in active inference, it will ultimately select the actions that guide it to this goal, much like a self-fulfilling prophecy. Of course, while doing so, the agent will keep reducing it's Free Energy by resolving uncertainty, avoiding ambiguity, and learning about it's environment.


## The Math

The beauty of the active inference framework is that you can actually right it down in math. For example Free Energy $$F$$ can be written down as the difference of the log probability of an approximate posterior distribution Q and the joint probability distribution of observations $$\tilde{\textbf{o}}$$, hidden states $$\tilde{\textbf{s}}$$ and the followed policy $$\pi$$ (i.e. sequence of actions). 

$$
\begin{equation} 
  \begin{split}
    F &= \mathbb{E}_{Q}[\log Q(\tilde{\textbf{s}}) - \log P(\tilde{\textbf{o}}, \tilde{\textbf{s}}, \pi)] \\
      &= \mathrm{D}_{KL}[Q(\tilde{\textbf{s}})||P(\tilde{\textbf{s}}, \pi | \tilde{\textbf{o}})] - \log P(\tilde{\textbf{o}})
  \end{split}
\label{eq:fe}
\end{equation}
$$

The second equality shows that minimizing Free Energy is actually maximizing the log evidence $$\log P(\tilde{\textbf{o}})$$, and that negative Free Energy is actually the evidence lower bound that is well known in the machine learning community, but more about that later.

The crucial part of all this is that active inference and the Free Energy principle offer us a tangible optimization objective for creating intelligent agents. However, three main challenges remain:

- How does one define and learn a generative model that can capture the causes and effects of a complex environment such as the real world?

- How does one define the prior distribution of an agent encoding its preferences that results in proper goal-directed behavior?

- How does one evaluate the potentially infinite amount of potential actions an agent can do in the world, to actually find those optimal actions that minimize the Free Energy?

These three questions are what drives our research, and you will read a lot more about that in the coming posts.


[^1]: [Karl Friston, Thomas FitzGerald, Francesco Rigoli, Philipp Schwartenbeck, John O'Doherty, Giovanni Pezzulo, Active inference and learning, Neuroscience & Biobehavioral Reviews, 2016](https://doi.org/10.1016/j.neubiorev.2016.06.022){:target='_blank'}.
