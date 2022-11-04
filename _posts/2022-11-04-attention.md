---
layout: post
title: /AI/ History of Attention and Transformer
description: 
tag: Tutorial
---

This post summarizes the historical milestones and evolution of the Attention and Transformer, which is one of the most important state-of-the-art machine learning model. It's also a review material of the Deep Learning for Data Science lecture given by the professor Ziwei Liu.

# Recurrent Neural Networks

The story of Transformer model begins with RNNs. In sequence-to-sequence learning, RNNs consist of an encoder and a decoder. In the encoder, the current hidden stat h_t is calculated from the previous hidden state h_t-1 and the current input x_t. After the encoder, two parameters are obtained to encapsulate the knowledge learned from the input sequence: an **initial decoder state** s_0 and a **context vector** c. In the decoder, each hidden state is calculated from the previous hidden state, the same context vector and the previous output token. Therefore, the calculation of output sequence is in series, depening on the previous output token.

![](http://siyue-zhang.github.io/images/attention/rnn.png)

The problem with this RNN architecture lies in the fixed-size context vector, which becomes the bottleneck for learning long sequences. One idea to solve this issue is to use a new context vector at each step of decoder.

# Recurrent Neural Networks and Attention

Attention introduces multiple context vectors into the decoder (one vector c per step). Each context vector attends to the relevent part in the input sequence. The context vector is computed as linear combination of hidden states with attention weights. The attion weights are obtained by the alignment (i.e., similarity) between the decoder state and each encoder hidden state through a softmax function. 

![](http://siyue-zhang.github.io/images/attention/rnn_att.png)

Use a different context vector in each timestep of decoder
* Input sequence not bottlenecked through single vector 
* At each timestep of decoder, context vector “looks at” different parts of the input sequence

The decoder doesn’t use the fact that h_i form an ordered sequence – it just treats them as an unordered set {h_i}.

# Image Captioning with RNNs and Attention




# Attention Layer

# Self-Attention Layer

# Masked Self-Attention Layer

# CNN with Self-Attention

# Transformer