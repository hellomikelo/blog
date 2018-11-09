---
layout: post
title: Deciphering denoising convolutional neural network (DnCNN)
description: Breaking down Tensorflow syntax and CNN for image denoising
categories: 
- machine learning
---

## DnCNN

Last year a new development in image denoising technique using convolutional neural network attracted a lot of attention for its ability to beat state-of-the-art algorithms in general image denoising. The article by [Zhang et al. (2017)](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7839189), used the popular convolutional neural network (CNN) framework as the basis, and incorporated batch normalization (BN) and residual learning to speed up learning and enhance denoising quality. Unlike other conventional methods such as nonlocal self-similarity techniques (BM3D), the deep neural network approach does not require prior knowledge of noise statistics (although having it helps), and is independent of noise types. Moreover, in addition to denoising, DnCNN can be used for JPEG deblocking and single image super resolution (SISR). I'm curious to see how DnCNN is implemented so I downloaded crisb-DUT's Tensorflow implementation ([GitHub link](https://github.com/crisb-DUT/DnCNN-tensorflow)) to play around with it. Below I wll look under the hood and break down the codes into several big sections to try to understand what's going on. By doing so I hope to learn more about Tensorflow's functionality.

## Tensorflow implementation

### Tensorboard visualization

To visualize learning process (i.e. check cost function error vs iteration), you can activate Tensorboard via

`tensorboard --logdir='directory-containing-log-summaries'`

Once you point Tensorboard to the directory that contains the training logs, Tensorboard will open and display the information. 

### Start H2 Jupyter notebook from local computer

`python h2jupynb -u username`

To get help using the function: 

`python h2jupynb -h`

## Now what? 


