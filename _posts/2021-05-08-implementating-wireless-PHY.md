---
title: 'Implementing Wireless PHY (WiPHY)'
date: 2021-05-08
permalink: /posts/implement-wiphy
toc: true
tags:
  - Wireless Communication
  - RTL-SDR
  - Amplitude Shift Keying
---

> This blog is about 

I am writing this blog post in May 2021, at the time when people in India are going through the second wave of COVID-19. I hope all of you are fine and taking care of loved ones. If we try to observe the one thing which is keeping us connected during this pandemic is the communication. Without having the good internet infrastrcture we won't be able to get information from place to another and would have made it more difficult to combat this deadly disease. Hence, we can appreciate how important communications have been in our lives.

There are various ways to communicate information from one place to another. But In this blog, we will explore how the digital information is encoded to radio waves which can be then transmitted over the air and received by another radio which attempts to decode/re-construct the information which was sent from received signals.

# Notation Used


# Abbreviation Used

1. TX - Transmmitter
2. RX - Receiver
3. SDR - Software Defined Radio

# Introduction

In this blog, we will consider an information source which has digital information (sequence of zeros/ones) which it needs to communicate to other device which is at some distance from it. To transmit this information, at sending end we will need a transmitter (TX) which will encode this digital information over radio waves. The radio waves are then transmitted via antenna and is propogated through the air which reaches the receiver (RX). The job of receiver is then to decoded the information from these wireless signals. The figure shows the flow of information between the two devices.

<center><img src="images/blog_posts_media/implement_wiphy/wireles_comm.png"></center>
<center>This is an image</center>

> NOTE: In this post, the focus is to design a half-duplex wireless link. This implies, the TX and RX is fixed. Only one can transmit and other can receive. Not the other way around. We are particularly interested in building a device which can send unaddressed, unreliale(without ACK) short messages between the TX and RX. 

# Hardware Required

As discussed in the previous section, we will need a TX and RX to build such a  wireless link. 

### TX
  
  For TX, we will make use 315/433 MHZ ASK RF modules. These modules are very simple to use and very cheap as well. The module can be connected to Arduino and can be programmed from the same to modulate the baseband signal on to the 433/315MHz sine wave of carrier which is then transmiited through the on-board antenna.

  > NOTE: You can always attach a peace of short wire to the antenna port of the module to improve the signal reception and communication range. 

### RX

$$
\begin{equation}
\label{policy_update_rule}

\theta_{k+1} = \theta_{k} + \alpha \nabla_{\theta} J(\pi_{\theta_{k}})
 
\end{equation}
$$

<br>

# Deriving policy gradient, $$ \nabla_{\theta_{k}} J(\pi_{\theta_{k}}) $$

Let's derive some useful results which will be used in policy gradient derivation.

* Probability of a trajectory $$ \tau $$, $$ P(\tau \vert \theta_{k}) $$.

The trajectory $$ \tau = (s_{0}, a_{0}, s_{1}, ... a_{T-1}, s_{T})$$, is a sequence of the state and action pair which agent experiences, given that actions are sampled from $$ \pi_{\theta_{k}} $$. The probability of trajectory $$ \tau $$, gives the likelihood of seeing the trajectory $$ \tau $$ out of all the possible set of trajectories.

$$
\begin{equation}
\label{prob_of_a_trajectory}
P(\tau \vert \theta_{k}) = \mu(s_{0}) \pi_{\theta_{k}} (a_{0} \vert s_{0}) P(s_{1} \vert s_{0}, a_{0}), ... ,\pi_{\theta_{k}}({a_{T-1} \vert s_{T-1}}) P(s_{T} \vert s_{T-1}, a_{T-1}) 

\\

= \mu(s_{0}) \prod_{t=0}^{T} \pi_{\theta_{k}}(a_{t} \vert s_{t}) P(s_{t+1} \vert s_{t}, a_{t})
\end{equation}
$$

* Log gradient trick


$$
\begin{equation}
\label{log_grad_trick}
\frac{\nabla_{\theta_{k}} P(\tau \vert \theta_{k})}{P(\tau \vert \theta_{k})} = \nabla_{\theta_{k}} \log P(\tau \vert \theta_{k})
\end{equation}
$$

Equation ($$ \ref{policy_update_rule} $$), summarizes the update rule to update the parameters of the policy. In equation, all we need to do is to plug-in the policy gradient. Therefore, Let's derive it.

$$

\nabla_{\theta_{k}} J(\pi_{\theta_{k}}) = \nabla_{\theta_{k}} \mathbb{E} [R(\tau)]
\\
= \nabla_{\theta_{k}} \int_{\tau} P(\tau \vert \theta_{k}) R(\tau) d\tau
$$

Now, let's take the gradient inside the intergal. Since, $$ R(\tau) $$ is not a function of $$ \theta_{k} $$, it acts as a constant.

$$
\nabla_{\theta_{k}} J(\pi_{\theta_{k}}) =  \int_{\tau} \nabla_{\theta_{k}} P(\tau \vert \theta_{k}) R(\tau) d\tau
$$

$$
=  \int_{\tau} P(\tau \vert \theta_{k}) \nabla_{\theta_{k}} \log P(\tau \vert \theta_{k}) R(\tau) d\tau \;\;\;\; \text{From, (} \ref{log_grad_trick} \text{)}

\\
$$

$$
=  \int_{\tau} P(\tau \vert \theta_{k}) \nabla_{\theta_{k}}\left[ \log \mu(s_{0}) + \sum_{t=0}^{T} \log \pi_{\theta_{k}}(a_{t} \vert s_{t}) + \log P(s_{t+1} \vert s_{t}, a_{t})\right] R(\tau) d\tau \;\;\;\; \text{From, (} \ref{prob_of_a_trajectory} \text{)}

$$

Again, $$  \log \mu(s_{0}) $$ and $$ \log P(s_{t+1} \vert s_{t}, a_{t}) $$ are not the functions of $$ \theta_{k} $$. Therefore, $$ \nabla_{\theta_{k}} \log \mu(s_{0}) = 0 $$ and $$ \nabla_{\theta_{k}} \log P(s_{t+1} \vert s_{t}, a_{t}) = 0 $$.

$$
=  \int_{\tau} P(\tau \vert \theta_{k}) \sum_{t=0}^{T} \nabla_{\theta_{k}} \log \pi_{\theta_{k}}(a_{t} \vert s_{t}) R(\tau) d\tau
$$

$$
\label{policy_gradient_eqn}
\nabla_{\theta_{k}} J(\pi_{\theta_{k}}) =  \mathbb{E}_{\tau \sim P(\tau \vert \theta_{k})} \left [ \sum_{t=0}^{T} \nabla_{\theta_{k}} \log \pi_{\theta_{k}}(a_{t} \vert s_{t}) R(\tau) \right]
$$

Equation ($$ \ref{policy_gradient_eqn} $$), is the expression for the policy gradient. The expression is an expectation over the set of all possible trajectories. To calculate this expectation exactly, we need to know the set of all possible trajectories and their probablities which can be calculated using equation ($$ \ref{prob_of_a_trajectory} $$). However, the probability of a trajectory depends upon $$ \mu(s) $$ and $$ P(s_{t+1} \vert s_{t}, a_{t}) $$, which are typically unknown or difficult to obtain (like for complex environments). In practice, all we need is an good estimate of this gradient and 