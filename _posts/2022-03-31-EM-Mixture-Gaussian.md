---
layout: post
title: An introduction to  Expectation-maximization (EM) algorithm for Gaussian mixture models and Factor Analysis
tags: [EM, R, simulations, GaussianMixture, Factor Analysis]
author: Tran Le
---

* TOC
{:toc}

# Goal of the project
The purpose of this project is to discover the Expectation-maximization (EM) algorithm, 
and explore how the EM algorithm works with the Gaussian mixture models and Factor Analysis models.
The project will introduce the EM algorithm and explore how EM clustering algorithm works for:
  - Mixture of two Gaussian distributions in 1D,
  - Mixture of k>2 Gaussian distributions in 1D,
  - Mixture of k>=2  Gaussian distribution in dimension d>=2. 

Those will be presented with detailed construction of the E and M step, pseudo-code, and R-code examples.
  - Then an introduction to Factor Analysis and how EM algorithm works for Factor analysis will be presented.
# Contents

Index | Desciption | Notes | Rcode
------------- | ------------- |---------------|------------
1 | Introduction to the EM algorithm | | 
2 | How EM clustering algorithm works for Mixture of two Gaussian distributions in 1D| [Note_2G_1D](https://htmlpreview.github.io/?https://github.com/tranktle/em-intro-mixture-gaussian/blob/main/Note_2G_1D.html)| [Rcode_2G_1D](https://htmlpreview.github.io/?https://github.com/tranktle/em-intro-mixture-gaussian/blob/main/01_Mixture_2Gaussian_1d.html)
3| How EM clustering algorithm works for Mixture of k>=2 Gaussian distributions in 1D| [Note_kG_1D](https://htmlpreview.github.io/?https://github.com/tranktle/em-intro-mixture-gaussian/blob/main/Note_3G_1D.html)| [Rcode_3G_1D](https://htmlpreview.github.io/?https://github.com/tranktle/em-intro-mixture-gaussian/blob/main/02_mixture_3Gaussian_1d.html) <br> [Rcode_3Gaussian_2D](https://htmlpreview.github.io/?https://github.com/tranktle/em-intro-mixture-gaussian/blob/main/03_Mixture_3Gaussian_2D.html)
4| Factor analysis introduction and how EM works for Factor Analysis| [Note_EM_Factor_Intro](https://htmlpreview.github.io/?https://github.com/tranktle/em-intro-mixture-gaussian/blob/main/Note_Factor_Intro.html)| [Rcode_Factor_intro](https://htmlpreview.github.io/?https://github.com/tranktle/em-intro-mixture-gaussian/blob/main/04_Factor_Analysis_Synthetic_Data.html)

In this project, we have explored the introduction of the EM algorithm in the problem of Mixture of Gaussian with $k=2$
 and $k>2$ distributions. Some examples with dimensions $d=1$
 and $d=2$ have been used to illustrate how the EM works. Through these examples, we have observed that the EM algorithm is sensitive to the initial values of parameters, and the error in higher dimension might be higher than in lower dimension. Another problem need to be considered is how well the EM algorithm can perform in clustering problems with overlapping clusters. The paper (Yang, Lai, and Lin 2012) can be a good source to explore how to improve the performance of the EM in this problem.

This project also has introduced how EM algorithm works with Factor Analysis, we have observed one example when the estimation for the linear transformation matrix $\Lambda$
 is smaller than the actual value and the estimation for the co-variance matrix $\Psi$
 is bigger than the actual value. The article (Zhao, Yu, and Jiang 2008) and Chapter 5 of the book "The EM Algorithm and Extensions" (McLachlan and Krishnan 2007) could be used to explore more about this problem.

I'm open to listening to your comments. All suggestions and corrections will be truly appreciated. 

# References
McLachlan, Geoffrey J, and Thriyambakam Krishnan. 2007. The EM Algorithm and Extensions. Vol. 382. John Wiley & Sons.

Ng, Andrew. 2000. “Cs229 Lecture Notes.” Cs229 Lecture Notes 1 (1): 1–3.

Yang, Miin-Shen, Chien-Yo Lai, and Chih-Ying Lin. 2012. “A Robust EM Clustering Algorithm for Gaussian Mixture Models.” Pattern Recognition 45 (11): 3950–61.

Zhao, J-H, Philip LH Yu, and Qibao Jiang. 2008. “ML Estimation for Factor Analysis: EM or Non-EM?” Statistics and Computing 18 (2): 109–23.



