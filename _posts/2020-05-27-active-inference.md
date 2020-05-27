---
layout: post
title: "Active inference explained"
subtitle: "A self-fulfilling prophecy"
author: "Tim Verbelen"
background: '/img/bg-franka.png'
paper: https://arxiv.org/abs/1904.08149
---


An introductory blog post on active inference

$$
\begin{equation} 
  \begin{split}
    F &= \mathbb{E}_{Q}[\log Q(\tilde{\textbf{s}}) - \log P(\tilde{\textbf{o}}, \tilde{\textbf{s}}, \pi)] \\
      &= \mathrm{D}_{KL}[Q(\tilde{\textbf{s}})||P(\tilde{\textbf{s}}, \pi)] - \mathbb{E}_{Q}[\log P(\tilde{\textbf{o}} | \tilde{\textbf{s}}, \pi)],
  \end{split}
\label{eq:fe}
\end{equation}
$$