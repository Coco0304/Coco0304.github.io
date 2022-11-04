---
layout: post
title: /AI/ History of Attention and Transformer
description: 
tag: Tutorial
---

This post summarizes the historical milestones and evolution of the Attention and Transformer, which is one of the most important state-of-the-art machine learning model. It's also a review material of the Deep Learning for Data Science lecture given by the professor Ziwei Liu.

# Recurrent Neural Networks

The story of Transformer model begins with RNNs. In sequence-to-sequence learning, RNNs consist of an encoder and a decoder. In the encoder, the current hidden state is calculated from the previous hidden state and the current input. After the encoder, two parameters are obtained to encapsulate the knowledge learned from the input sequence: an **initial decoder state** s_0 and a **context vector** c. In the decoder, each hidden state is calculated from the previous hidden state, the same context vector and the previous output token. Therefore, the calculation of output sequence is in series, depening on the previous output token.

![](http://siyue-zhang.github.io/images/attention/rnn.png)

The problem with this RNN architecture lies in the fixed-size context vector, which becomes the bottleneck for learning long sequences. One idea to solve this issue is to use a new context vector at each step of decoder.

# Recurrent Neural Networks and Attention

Attention introduces multiple context vectors into the decoder (one vector c per step). Each context vector attends to the relevent part in the input sequence. The context vector is computed as linear combination of hidden states with attention weights. The attion weights are obtained by the alignment (i.e., similarity) between the decoder state and each encoder hidden state through a softmax function. 

![](http://siyue-zhang.github.io/images/attention/rn_att_.png)


# Image Captioning with RNNs and Attention

# Attention Layer

# Self-Attention Layer

# Masked Self-Attention Layer

# CNN with Self-Attention

# Transformer