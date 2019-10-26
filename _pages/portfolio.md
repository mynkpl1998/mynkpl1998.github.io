---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

*Note : Please follow the provided link(s) in each project for full details. Also, some of the projects title has hyperlink which navigates directly to the project page.*

| [Visualizing Deep Learning  Optimization Algorithms](https://github.com/mynkpl1998/Deep-Learning-Optimization-Algorithms) |
| :---- |
| **Description** : Gradient based algorithms is the key to optimize the deep neural networks. Apart from the vanilla gradient descent algorithm, there exists many variant of gradient based algorithms which can  improve the speed of convergence and can avoid local minima too. In this project, various Deep learning optimization algorithmswere studied and their speed of convergence were visualized using PyTorch. Visualization of various deep learning optimization algorithms implemented using PyTorch’s automatic differentiation tool and optimizers. It demonstrates how the iterative methods approaches to the minimum in the case of convex, non-convex surfaces and surfaces with saddle point. <br> **Source Code** : [https://github.com/mynkpl1998/Deep-Learning-Optimization-Algorithms](https://github.com/mynkpl1998/Deep-Learning-Optimization-Algorithms) <br> **Some visualizations** :  <br> ![alt-text-1](https://github.com/mynkpl1998/Deep-Learning-Optimization-Algorithms/raw/master/Images/convex_sgd.gif "SGD on convex-surface") ![alt-text-2](https://github.com/mynkpl1998/Deep-Learning-Optimization-Algorithms/raw/master/Images/non_convex_sgd.gif "SGD on non-convex surface")|


| Recurrent Deep-Q Learning |
| :---- |
| **Description** : Partially Observable Markov Decision Process (POMDP) is a generalization of Markov Decision Process where agent cannot directly observe the underlying state and only an observation is available. Earlier methods suggests to maintain a belief (a pmf) over all the possible states which encodes the probability of being in each state. This quickly limits the size of the problem to which we can use this method. However, the paper Playing Atari with Deep Reinforcement Learning presented an approach which uses last 4 observations as input to the learning algorithm, which can be seen as 4th order markov decision process. Many papers suggest that much performance can be obtained if we use more than last 4 frames but this is expensive from computational and storage point of view (experience replay). Recurrent networks can be used to summarize what agent has seen in past observations. In this project, I investgated this using a simple Partially Observable Environment and found that using a single recurrent layer able to achieve much better performance than using some last k-frames. <br> **Source Code** : [https://github.com/mynkpl1998/Recurrent-Deep-Q-Learning](https://github.com/mynkpl1998/Recurrent-Deep-Q-Learning) <br> **Results** : The figure given below compares the performance of different cases. MDP case is the best we can do as the underlying state is fully visible to the agent. However, the challenge is to perform better given an observation. The graph clearly shows the LSTM consistently performed better as the total reward per episode was much higher than using some last k-frames. <br> <br> ![alt-text-4](https://raw.githubusercontent.com/mynkpl1998/Recurrent-Deep-Q-Learning/master/data/GIFs/perf.png "Performance difference using LSTM network against past k-frames") |

| [A Deep Reinforcement Learning Framework](https://github.com/mynkpl1998/Deep-RL-Framework/blob/master/examples/1.%20Walk%20Through%20Demo%20-%20DQN%20-%20Fixed%20Epsilon.ipynb) |
| :---- |
| **Description** : This framework implements the various state of the art Value based Deep Reinforcement Learning algorithms, supports OpenAI gym environments out of the box. Implementation include Deep-Q learning, Deep-Q learning with target freezing, Prioritized experience replay, Double Q-learning. <br> **Source Code** : [https://github.com/mynkpl1998/Deep-RL-Framework](https://github.com/mynkpl1998/Deep-RL-Framework)|

| [Asynchronous Actor-Critic (A3C) - Policy Gradients Methods](https://github.com/mynkpl1998/A3C/tree/dev) |
| :---- |
| **Description** : High quality implementation of A3C algorithm with Generalized Advantage Estimation. Supports different neural network based policies out of the box. Performance of the algorithm scales linearly with the number of cores. <br> **Source Code** : [https://github.com/mynkpl1998/A3C/tree/dev](https://github.com/mynkpl1998/A3C/tree/dev) <br> **Trained Policies** : <br> <br> ![alt-text-5](https://raw.githubusercontent.com/mynkpl1998/mynkpl1998.github.io/master/images/cartpole.gif "Cartpole - keep the pole in vertical position" ) ![alt-text-6](https://raw.githubusercontent.com/mynkpl1998/mynkpl1998.github.io/master/images/lander.gif "Lunar Lander - land between flags")|

| Deep learning for Physical layer |
| :---- |
| **Description** : We present and discuss the application of Deep Learning (DL) for the physical layer.  By interpreting acommunication system as an AutoEncoder, we develop a fundamental new way to think about communications system design as end-to-end reconstruction task that seeks to jointly optimize transmitter and receivercomponents in a single process.  Simulations were done to illustrate the learning of the deep networks. Further, the results were compared with traditional methods. <br> **Report** : [https://drive.google.com/file/d/1q3Ba741gZxWAgv4t7ERwb5H93iajp2J-/view](https://drive.google.com/file/d/1q3Ba741gZxWAgv4t7ERwb5H93iajp2J-/view) <br> **Triand Policies** <br> <br> |


| Implemention of Convolutional and Recurrent neural networks inference for Heterogeneous Devices (GPU and FPGA) using OpenCL |
| :---- |
| **Description** : Many devices today have more than one processor other than CPUs to accelerate certain workloads. For example, an integrated graphics or DSPs in an embedded system. This creates an interesting opportunity for deep learning community to take advantage of it and use it to accelerate the inference/training process for edge devices. We attempted to implement the inference of some of the known architecture like Recurrent and Convolutional neural networks for FPGA and GPU in Open Compute Language trained on standard datasets. <br> **CNN Source Code** : [https://bitbucket.org/mynkpl1998/vgg_opencl/src/master/](https://bitbucket.org/mynkpl1998/vgg_opencl/src/master/) <br> **RNN Source Code** : [https://bitbucket.org/mynkpl1998/rnn_opencl/src/master/](https://bitbucket.org/mynkpl1998/rnn_opencl/src/master/) <br> **CNN Report** : [https://drive.google.com/file/d/1yDCyucwo6I5Z2bOd-tKOkEWo-ByrFHdc/view](https://drive.google.com/file/d/1yDCyucwo6I5Z2bOd-tKOkEWo-ByrFHdc/view) <br> **RNN Report** : [https://drive.google.com/file/d/1GzoLjMLM-rKMvbgFPtIJ7b3X_wivbxfw/view](https://drive.google.com/file/d/1GzoLjMLM-rKMvbgFPtIJ7b3X_wivbxfw/view)|


| [ATP-Predict](https://github.com/mynkpl1998/atppredict) |
| :---- |
| **Description** : We carried out a brief implementation of the paper Identification of ATP binding residues of aprotein from its primary sequence and attempted to improve on the existing methods by using different machinelearning techniques using an extended dataset and optimized parameters on the models.  We obtained maximumcross-validation accuracy of around 0.64 on a balanced data-set, with window size 17. <br> **Project Web Page** : [https://mynkpl1998.github.io/atppredict/](https://mynkpl1998.github.io/atppredict/)|

| Cancer Prediction using Deep Neural Networks |
| :---- |
| **Description** : This project investigates the opportunities of applying the deep convolutional networks fordeveloping prediction model for cancer prediction. We selected high quality image dataset containing both benign and malignant examples. We build a classifier which used SIFT to extract the features from the images. However, we found that this naive approach could not able to perform well on our dataset. We  then explored the space of Deep Learning techniques specifically Deep Convolutional Neural Networks. <br> **Report** : [https://drive.google.com/file/d/1W24dv9um3QGnfZsEoDO-jFaOmISeWiDF/view](https://drive.google.com/file/d/1W24dv9um3QGnfZsEoDO-jFaOmISeWiDF/view)|

| [Visualizing VGG16 feature maps in Keras](https://github.com/mynkpl1998/visualize-vgg16) |
| :---- |
| **Description** : This project impelements the code for visualizing the feature maps of VGG16 Convoutional Neural Network using Keras. Particular layer of the network can be visualized by defining it as an output layer. For brevity please check some examples given below. <br> **Source Code** : [https://github.com/mynkpl1998/visualize-vgg16](https://github.com/mynkpl1998/visualize-vgg16)|
