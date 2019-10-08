---
layout: post
title: Friendly Introduction To Steganalysis
date:   2018-03-04 00:00:00
categories: [steganalysis]
tags: [steganalysis]
published: true
comments: true
---

<center><img src="/images/post2/Steganalysis_bg.png" alt="Drawing" style="max-width: 100%; height: auto;"/></center>
<br/>

In the previous post titled "[**Friendly Introduction To Steganography**](../Introduction-Steganography)", we have shown that steganography, in its most common modern digital form, conceals plain text or whole files in an image, audio or video file.

This type of communication with a very low risk of detection (for example by the naked eye for images) can be a virgin territory of misuse through:

1. Terrorism:  According to government officials, terrorists use to hide maps and photographs of terrorist targets and giving instructions for terrorist targets. As an example, the events of September 11th prompted significant discussion and speculation as to the use of Steganography by terrorists (<a href="https://en.wikipedia.org/wiki/Al-Qaeda" target="_blank">al-Qaeda</a>) for clandestine and secured communications.

2. Spying: Steganography has been a favored way to pass messages through public discussion sites and was used by <a href="https://en.wikipedia.org/wiki/Anna_Chapman" target="_blank">Anna Chapman</a> and her bumbling ring of Russian spies to pass messages online.

3. Hacking: The hacker hides a monitoring too, server behind any image or audio or text file and shares it with mail or chat which will get installed and executed which will help the hacker to do anything with the workstation. In a presentation at Hack In The Box in Amsterdam in 2011, <a href="http://net-square.com/" target="_blank">Net Square</a> security researcher <a href="https://twitter.com/therealsaumil" target="_blank">Saumil Shah</a> demonstrated an updated method of his digital steganography project, <a href="http://stegosploit.info/" target="_blank">Stegosploit</a>. Shah has discovered executable code can in fact be embedded within an image and executed in a web browser, evading detection of even the most scrupulous malware scanners.

## Questions ?

**Can we fight against the abuse of steganography? and how can we do that?**

## Brief Response

**Yes**, like the cryptanalysis that was created against cryptography, there is also what we call the **Steganalysis**.

## 1. What's Steganalysis ?

Briefly, Steganalysis can be defined as the set of techniques and methods used to detect the presence of information embedded in digital objects and to extract this information if it is possible.


## 2. Steganalysis approaches

The steganalysis algorithm may or may not depend on the steganographic algorithm (SA). Based on this, steganalysis is classified as follows:

### 2.1.Specific or Target steganalysis

The SA is known and the designing of detector (steganalysis algorithm) is based on SA. The steganalysis algorithm is dependent on the SA. This type of steganalysis is based on
analyzing the statistical properties of an image that change after embedding. The advantage of using specific steganalysis is the results are very accurate. The disadvantage of using this method is it is very limited to particular embedding algorithm as well as the image format.

### 2.2.Blind or Universal steganalysis

In universal steganalysis, the SA is not known by everyone. Hence, anyone can design a detector
to detect the presence of the secret message that will not depend on SA. Comparing with specific
steganalysis, universal is common and less efficient. Still universal steganalysis is widely used
than specific one because it is independent of the SA.
__Nowadays, scientific research focuses on universal steganalysis.__


<p align="center">
	<img src="/images/post2/steganalysis_system.png" />
</p>

## 3. Steganalysis Methods and tchniques

Based on the way of detecting the presence of hidden message, steganalysis methods are divided as follows:

### 3.1. Statistical steganalysis

In order to detect the existence of the hidden message, statistical analysis is done with the pixels. It is further classified as **spatial domain** steganalysis and **transform domain** steganalysis.


In spatial domain, the pair of pixels is considered and the difference between them is
calculated. The pair may be any 2 neighboring pixels. They may be selected within a block
otherwise across the two blocks. Finally the histogram is plotted that shows the existence of the
hidden message.

In transform domain, frequency counts of coefficients are calculated and then histogram analysis is performed. With the help of this, the cover and stego images can be differentiated. However, this method is not providing information about the embedding algorithms. To overcome this problem, we may choose feature based steganalysis.

### 3.2. Steganalysis machine learning techniques

In this method, the features of the image will be extracted for selecting and retaining relevant
information. These extracted features are used to detect hidden message in an image. They can
also be used to train classifiers.

It includes the following 2 phases:

a. **Feature Extraction**: It is a process of creating a set of distinct statistical attributes of an image. These attributes are known as feature. Feature Extraction is nothing but a dimensionality reduction. The extracted features must be sensitive to the embedding artifacts. Image quality metrics, wavelet decompositions, moment of image statistic histograms, Markov empirical transition matrix, moment of image statistic from spatial and frequency domain, co-occurrence matrix are some of the feature extraction methods.

b. **Classification**: It is a way of categorizing the images into classes depending on their feature values. Supervised learning is one of the primary classifications in steganalysis. Supervised learning allows learning under some supervision. In this learning, a set of training inputs
that includes input features is given as input to train the classifier. After the training, class label is predicted based on the features that are given.

steganalysis use the following classifiers:

- **Multivariate regression**: It consists of regression co-efficient. In the training phase, regression coefficients are predicted using minimum mean square error.

- **FLD**: It is a linear combination of features which maximizes the separations. In the classification method, multi dimensional features are projected into a linear space.

- **SVM**: This classification method learns from the given sample. It is trained to recognize and assign class labels based on a given set of features.

### 3.3. Steganalysis deep learning models

In recent years, Deep Learning models such as the Convolutional Neural Networks (CNN or ConvNet) have been introduced and applied within image steganalysis context. Deep learning combines the two phases in machine learning techniques(Feature extraction and classification) as a single compact model.

## 4. Steganalysis tools

Various steganalysis tools are available to detect the presence of hidden information with the stego image. Some of the steganalysis tools are mentioned below:

1. <a href="https://github.com/abeluck/stegdetect" target="_blank">StegDetect</a>.
2. <a href="http://www.petitcolas.net/watermarking/stirmark/" target="_blank">Stirmark</a>.
3. <a href="http://cyborg.ztrela.com/steg-toolkit.php/" target="_blank">StegBreak</a>.
4. <a href="https://www.aldeid.com/wiki/StegSecret" target="_blank">StegSecret</a>.
5. <a href="https://github.com/h3xx/jphs" target="_blank">JPSeek</a>.
6. <a href="http://cyborg.ztrela.com/steg-toolkit.php/" target="_blank">StegBreak</a>.
7. <a href="http://www.petitcolas.net/watermarking/2mosaic/" target="_blank">2Mosaic</a>.

## 5. Good application of steganalysis in other fields

- **Medical safety**: Current image formats such as DICOM separate image data from the text (such as patients name, date and physician), with the result that the link between image and patient
occasionally gets mangled by protocol converters. Thus embedding the patients name in the image could be a useful safety measure.

- **Intellectual property offenses**: Intellectual property, defined as the formulas, prototypes, copyrights and customer lists maintained by a company, can be far more valuable than the actual items they sell.

- **Watermarking**: Special inks to write hidden messages on bank notes and also the entertainment industry using digital watermarking and fingerprinting of audio and video for copyright protection.



## References

1. <a href="http://shodhganga.inflibnet.ac.in/bitstream/10603/8912/13/11_chapter%202.pdf" target="_blank">Chapter 2: Steganography and Steganalysis methods</a>

2. <a href="https://arstechnica.com/information-technology/2012/05/steganography-how-al-qaeda-hid-secret-documents-in-a-porn-video/" target="_blank">Steganography: how al-Qaeda hid secret documents in a porn video</a>

3. <a href="http://www.player.one/hacking-pictures-new-stegosploit-tool-hides-malware-inside-internet-images-instant-444768" target="_blank">Hacking With Pictures; New Stegosploit Tool Hides Malware Inside Internet Images For Instant Drive-by Pwning</a>

<a href="https://twitter.com/share" class="twitter-share-button" data-show-count="false">Tweet</a><script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-115439306-1', 'auto');
  ga('send', 'pageview');
</script>
