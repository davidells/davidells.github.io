---
id: 345
title: 'Hacker Notes: Machine Learning'
date: 2011-12-18T05:52:13+00:00
author: dells
layout: post
guid: http://davidells.info/blog/?p=345
permalink: /2011/12/hacker-notes-learning-machine-learning-via-ml-class-org/
dsq_thread_id:
  - "508084982"
categories:
  - hacker-notes
tags:
  - machine learning
---
[<img src="http://davidells.info/blog/wp-content/uploads/2011/12/skynet.jpg" alt="" title="skynet" width="610" height="315" class="aligncenter size-full wp-image-367" />](http://davidells.info/blog/wp-content/uploads/2011/12/skynet.jpg)

I just finished the Machine Learning online course provided by Stanford University! This is [the official class page at Stanford](http://cs229.stanford.edu/) at the time of this writing. I took the course via enrollment at <ml-class.org> .

In the class, I studied Machine Learning. As the definition goes, a machine can be said to learn if it improves on a performance measure P for a given task T by an experience of E.

Machine learning works like this: in &#8220;supervised machine learning&#8221;, you &#8220;train&#8221; a learning algorithm with labeled examples. The trained algorithm (i.e. one that has &#8220;learned&#8221; a certain set of parameters) can then be used to predict or process new data.

An example of a supervised learning algorithm is recognizing hand writing. This is used extensively by the postal service to help automate the flow of mail. The implementation we worked on in the class was a neural network (beyond scope here) which recognized hand written digits. By providing the neural network with labeled input (an image of a handwritten number 9) and the correct output (the digit 9), it learned to identify new writing which it had not yet seen. 

What&#8217;s going on behind the scenes is that the labeled examples modify parameters on a statistical model. The way machine learning algorithms are written, they can be used to create really complex (and powerful) models. Then, new input is run through the parametrized statistical model (the &#8220;trained&#8221; neural network) and out pops, for each digit 0-9, the probability that the image is that digit.

Supervised learning includes linear regression, logistic regression, neural networks, and others. The other type is unsupervised learning. In this case, the algorithm just looks at unlabeled data, and attempts to find groups or patterns in the data. This might include market segmentation, anomaly detection, or other grouping operations.

An example there is anomaly detection in a production line. An airplane engine might be tested for its heat vs. its vibration as part of production. An anomaly detection system, given plenty of examples of normal engines, could read the test results on new engines and raise a red flag if a certain combination of heat and vibration come up that are statistically very improbable.

At a really high level, that&#8217;s about the whole of the class. Most of the time is spent constructing and understanding the implementation of these learning algorithms. At the end, you get a look at using individual learning algorithms as building blocks to create pipelines. 

An example pipeline covered is a program to recognize text in photos. This is a pipeline of three algorithms (all supervised, i.e. &#8220;trained&#8221; on labeled examples). The first detects what parts of the photo are text, the second breaks up the text into letters, and the last identifies those letters. 

It&#8217;s interesting to think about learning algorithms as building blocks. Since they&#8217;re just really complex statistical models, you can see they&#8217;re only giving rise to even more complex models when combined. And yet you can start breaking up &#8220;actions&#8221; like identifying and reading text present in photos by recognizing areas of text, breaking it up into letters, and reading those letters.

It&#8217;s interesting to think how algorithms and entire pipelines could be lined up to create complex processing on input. I imagine this is how researchers accomplish things like machine vision, or in attempts to model the human brain.

(For reference, I&#8217;ve added the exercises (and my solutions) from the class to my personal GitHub account [here](https://github.com/davidells/ml-class). If you&#8217;re planning on taking the class, please ignore.)