---
layout: post
title:  "Implicit Regularization and Generalization Of Deep Neural Networks"
date:   2024-11-23 23:22:26 -0800
categories: expository
---

In this post I will reflect on what (little) I know about implicit generalization, and discuss future directions. Ultimately the goal is to show that the reason that deep networks generalize well, even without convergence, is that they are biased to learn simple functions, ultimately by their compute-limited nature. 

While it is difficult to show asymptotic results, it may be possible to show non-asymptotic results in a complexity-theoretic framework. For this reason, we will start by reviewing some complexity-theoretic concepts. '

## Kolmogorov Complexity 

Given a string $s$, the Kolmogorov complexity of a string is the length of the shortest program that outputs the string. We are being a bit sloppy here by not specifying the encoding of the program, but this is fine for our purposes. However, what is the shortest program that outputs $s$? Suppose we are given $s$. How difficult is it to find the shortest program that outputs $s$?

The intuition is that even if there exists a program that outputs $s$, if it is difficult to construct given $s$, then actually we would like to say that complexity of $s$ is still high. 

## Learning Theory

We would like to understand why deep networks generalize well. However, we fail to consider the complexity of the function that the network is trying to learn. We would like a theory that says something like the following:

1. We have a well defined notion of complexity of a function we wish to learn, and ways of showing upper bounds on it. 
2. We have a theory which says that the complexity of functions you can learn with a limited amount of compute steps is bounded in a stronger way than just by a description of the entire function class among which you are optimizing. 

Fortunately, we already something for the first point. That is precisely the notion of Rademacher complexity. Therefore, to implement the second point, what we need to do is estimate the Rademacher complexity of a compute-limited process. I have not seen any papers which do this directly (please let me know if you have seen something!). I am also not sure whether this is possible. 

The ideal scenario would be to prove something like the following. The class of functions which are obtained by performing operations on the weights of some neural network (backpropogation would be one such algorithm) has limited (Rademacher?) complexity, with high probability (since of course you could just randomly choose the weights, and get something which is the optimal predictor in the function class). Then apply some general theory to get a generalization guarantee.

Unfortunately, I would guess that the above could not work to prove a generalization guarantee using the classical generalization bound method, because we know that deep neural networks can perfectly fit the training data while simultaneously predicting new points very well. Recent works show that the learned function can be decomposed into an optimally predictive part, which helps generalization, and a noisy part, which perfectly fits the training data. 

## Where to Go From Here?

I honestly I have no idea. This isn't a research article nor a research proposal; it is just a reflection on my thoughts and hopes about generalization of deep neural networks. Check back soon for more (I hope concrete) ideas!

