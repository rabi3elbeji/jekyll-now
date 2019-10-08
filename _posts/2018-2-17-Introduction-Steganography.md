---
layout: post
title:  Friendly Introduction To Steganography
date:   2018-02-17 00:00:00
categories: [steganography]
tags: [steganography]
published: true
comments: true
---

<center><img src="/images/post1/steganography_bg.png" alt="Drawing" style="width: 100%; height: auto;"/></center>

## Question ?

As a software developer or computer science, networks student or simply a web surfer, you may hear the word cryptography. The aim of using cryptography is to provide a secure communication while transmitting data throw network supports. Cryptography techniques modify the data to make them incomprehensible.

But here I have a simple question:

**Can we transmit secret data without applying cryptography techniques throw network supports and trusted their security at the same time?**

## Brief Response

**Yes**, the response is **Steganography**. Nowadays, steganography is defined as the art and science of hiding or embedding secret data through various multimedia containers or network supports such as videos, audio files, network packets and last but not least digital images.


### 1. A bit of history

Steganography is an old practice that has been around for a long time. People have desired to keep certain sensitive communications secret for thousands of years. The term steganography combines the Greek words **steganos**, meaning "covered, concealed, or protected" and graphein meaning "writing".
The first recorded uses of steganography can be traced back to 440 BC when ancient Greece, people  wrote messages on wood and covered it with wax that bore an innocent covering message. In 1499, <a href="https://en.wikipedia.org/wiki/Johannes_Trithemius" target="_blank">Johannes Trithemius</a>, introduce officially the concept of steganography in his book titled <a href="https://en.wikipedia.org/wiki/Steganographia" target="_blank">Steganographia</a>. In the last centuries, Steganography used during both world wars essentially in the espionage using secret inks in letters or photos. Recently, we have seen new generation of steganography called digital steganography used in many malware programs and cyber espionage tools. Four main trends of development of the so-called digital steganography can be distinguished:
- digital media steganography
- linguistic steganography
- file system steganography
- network steganography

The summary of the evolution of the steganographic data carrier is presented in the figure down below.

![alt text](/images/post1/steganography_timeline.png "Steganographic evolution")

### 2. What's a Stegosystem ?

A **Stegosystem** describes the process that is used in performing steganographic methods. Let's say that **Alice**, the expeditor, want to send a secret message to **Bob**, the receiver, using a stegosystem. Alice uses a steganographic method to embed the secret message (`M`) through a cover object (`C`). The embedding process generates a stego object (`S`). Alice sends the stego object to Bob clearly through the network without any encryption using a web or mobile application for example. In the other side, Bob must use the same steganographic method to extract the secret message (`M`) from the received stego object (`S`). Note that some steganographic methods use a stego key (`K`) in the embedding process to provide more security to the secret message. In this case, Bob must have the same stego key (`K`) used by Alice to extract the secret message (`M`).

![alt text](/images/post1/stego_system.png "A standard Stegosystem")

The main keywords used in the most stegosystems are:

- **Cover Object**:  The cover object is the carrier of the hidden message.  A cover is generally chosen in a manner that it appears most ordinary and innocuous and does not arouse suspicion as such. The cover object can be :
	* Text file (txt, pdf, word, ...)
	* Image file (jpeg, png, gif, ppm, ...)
	* Audio file (wav, mp3, aac, ...)
	* Video file (mp4, avi, mov, flv, ...)
	* Network protocol (tcp/ip, pop, smtp, http, ...)
- **Stego Object**: The cover object with a secret message concealed within it is known as the stego.
It is used on the recipient side for extracting the hidden message.
- **Stego Key**: Stego  key  is  a  key  to  embed  data  in  a cover and extract data from the stego medium.
- **Embedding Domain**: refers to the cover medium characteristics that are exploited in embedding message into it. It may be spatial domain when direct modification of the constituent elements of the cover is modified (e.g. pixels in an image) or it can be the frequency domain or transform domain if mathematical transformations are carried on the medium before embedding.


### 3. Steganographic methods

Steganographic methods can be classified mainly into five categories, although in some cases this classification is not possible:

- Spatial domain
- Transform domain
- Spread spectrum
- Statistical Methods
- Distortion Methods

#### 3.1. Spatial domain

Spatial domain steganographic techniques, also known as substitution techniques, are a group of
relatively simple techniques that create a covert channel in the parts of the cover image in which
changes are likely to be a bit scant when compared to the human's eyes.

One of the ways to do so is to hide information in the Least Significant Bit (LSB) of the image data.
This embedding method is basically based on the fact that the least significant bits in an image can
be thought of as random noise, and consequently they become not responsive to any changes on the image.

#### 3.2. Transform domain

Transform domain embedding can be defined as a domain of embedding techniques for which a number of algorithms have been suggested. The process of embedding data in the *frequency domain* of a
signal is much stronger than embedding principles that operate in the *time domain*.

Transform domain techniques have an advantage over LSB techniques because they hide information in areas of the image that are less exposed to compression, cropping, and image processing.

#### 3.3. Spread Spectrum Technique

Spread spectrum transmission in radio communications transmits messages below the noise level for any given frequency. When employed with steganography, spread spectrum either deals with the cover image as noise or tries to add pseudo-noise to the cover image.

#### 3.4. Statistical Method

Also  known  as  model-based  techniques,  these  techniques  tend  to  modulate  or  modify  the
statistical properties of an image in addition to preserving them in the embedding process. This
modification is typically small, and it is thereby able to take advantage of the human weakness in
detecting luminance variation.

#### 3.5. Distortion Techniques

Distortion techniques require knowledge of the original cover image during the decoding process where
the decoder functions to check for differences between the original cover image and the
distorted cover image in order to restore the secret message. The encoder, on the other hand, adds a  sequence of changes to the cover image. So, information is described as being stored by signal distortion.


### 4. Characteristics of a Strong Steganography method

Though steganography's most obvious goal is to hide data, there are several other related goals used to judge a method's steganographic strength. These include:
- **Capacity** (how much data can be hidden)
- **Invisibility** (inability for humans to detect a distortion in the stego-object)
- **Undetectability** (inability for a computer to use statistics or other computational methods to differentiate between covers and stego-objects)
- **Robustness** (message's ability to persist despite compression or other common modifications)
- **Tamper resistance** (message's ability to persist despite active measures to destroy it)
- **Signal to noise ratio (SNR)** (how much data is encoded versus how much unrelated data is encoded).

The three main components, which work in opposition to one another, are *capacity*, *undetectability*, and *robustness*.

### 5. Perfermance measure

As a performance measure for image distortion due to embedding, the well-known peak-signal-to-noise ratio (`PSNR`), which is categorized under difference distortion metrics, can be applied to stego images.  It is defined as:

<p align="center">
	<img src="/images/post1/psnr_function.png" />
</p>

In the previous equation, `R` is the maximum fluctuation in the input image data type. For example, if the input image has a double-precision floating-point data type, then `R` is 1. If it has an 8-bit unsigned integer data type, `R` is 255, etc. `MSE` denotes the mean square error, which is given as

<p align="center">
	<img src="/images/post1/mse_function.png"/>
</p>

`M` and `N` are the number of rows and columns in the input image.


The `MSE` represents the cumulative squared error between the stego and the cover image, whereas PSNR represents a measure of the peak error. The lower the value of `MSE`, the lower the error.

The Structural Similarity (`SSIM`) Index quality assessment index is based on the computation of three terms, namely the luminance term, the contrast term and the structural term. The overall index is a multiplicative combination of the three terms.

<p align="center">
	<img src="/images/post1/ssim_function.png"/>
</p>

### 6. Scientific and commercial applications

Nowadays, there are many applications for Information Hiding:

- **Advanced data structures**: We can devise data structures to conceal unplanned information without breaking compatibility with old software. For instance, if we need extra information about photos, we can put it in the photos themselves. The information will travel with the photos, but it will not disturb old software that does not know of its existence. Furthermore, we can devise advanced data structures that enable us to use small pieces of our hard disks to secretly conceal important information.

- **Medical imagery**: Hospitals and clinical doctors can put together patient’s exams, imagery, and their information. When a doctor analyzes a radiological exam, the patient’s information is embedded in the image, reducing the possibility of wrong diagnosis and/or fraud. Medical-image steganography requires extreme care when embedding additional data within the medical images: the additional information must not affectthe image quality.

- **Strong watermarks**: Creators of digital content are always devising techniques to describe the restrictions they place on their content. These technique can be as simple as the message “Copyright year by Someone”, as complex as the digital rights management system (`DRM`) devised by `Apple Inc.`  in its `iTunes` store’s contents, or the watermarks in the contents of the Vatican Library.

- **Military agencies**:  Militaries’ actions can be based on hidden and protected communications.   Even with crypto-graphed content,  the detection of a signal in a modern battlefield can lead to the rapid identification and attack ofthe involved parties in thecommunication. For this reason, military-grade equipmentuses modulation and spreadspectrum techniques in its communications.

- **Intelligence agencies**: Justice and Intelligence agencies are interested in studying these technologies, and identifying their weaknesses to be able to detect and track hidden messages.

- **Document tracking tools**:  We can use hidden information to identify the legitimate owner of a document. If the document is leaked, or distributed to unauthorized parties, we can track it back to the rightful owner and perhaps discover which party has brokenthe license distribution agreement.

- **Document authentication**: Hidden information bundled into a document can contain a digital signature that certifies its authenticity.

- **General communication**: People are interested in these techniques to provide more security in their daily communications. Many governments continue to see the internet, corporations, and electronic conversationsas an opportunity for surveil-lance.

- **Digital elections and electronic money**: Digital elections and electronic money are based on secret and anonymous communications techniques.

- **Radar systems**: Modern transit radar systems can integrate information collected in a radar base station, avoiding the need to send separate text and pictures to the receiver’s base stations.

- **Remote sensing**: Remote sensing can put together vector maps and digital imagery of a site, further improving the analysis of cultivated areas, including urban and naturalsites, among others.

### 7. Scientific research

Steganography is an active theme in scientific research that follows the development of technology. Nowadays, several laboratories and scientific researchers around the world are doing intense work that leads to a significant evolution of digital steganography during this century.

I recommend this list for those who want to do scientific research in steganography

- **Laboratories**:
  * <a href="http://dde.binghamton.edu/" target="_blank">DDE - Digital Data Embedding Laboratory, SUNY Binghamton, Binghamton, NY, USA</a>
  * <a href="http://www.lirmm.fr/" target="_blank">LIRMM - Laboratoire d'Informatique de Robotique et de Microélectronique de Montpellier, France</a>
  * <a href="https://www.ece.uic.edu/" target="_blank">ECE - Department, University of Illinois at ChicagoChicago, IL, USA</a>

- **Scientific Researchers**:
  * <a href="http://www.ws.binghamton.edu/fridrich/" target="_blank">Dr. Jessica Fridrich</a>
  * <a href="http://dde.binghamton.edu/" target="_blank">DDE Lab members </a>
  * <a href="http://www.lirmm.fr/~chaumont/Resume.html" target="_blank">Dr. Marc Chaumont</a>

- **Source codes**:
  * <a href="http://dde.binghamton.edu/download/" target="_blank">DDE Lab download website</a>

- **Datasets**:
  * <a href="http://dde.binghamton.edu/download/ImageDB/BOSSbase_1.01.zip" target="_blank">BOSSbase_1.01 from DDE Lab</a>
  * <a href="http://www.lirmm.fr/~chaumont/SteganalysisWithDeepLearning/CroppedBossBase-1.0-256x256_cover.rar" target="_blank">Cropped BOSSBase from LIRMM Lab</a>
  * <a href="http://dde.binghamton.edu/download/ImageDB/BURST_sorted.zip" target="_blank">BURST_sorted from DDE Lab</a>


### 8. An overview to the next post

Steganography has undergone a significant evolution during the last two centuries through various
techniques and methods that serve to increase the undetectability of the stego object. The misuse of
steganography by hackers and terrorists requires the existence of an antidote. This antidote is steganalysis which aims to detect the existence of a stego object in a first step and to extract the secret message in a second step. A Brief introduction to steganalysis in the "[**next post**](../Introduction-Steganalysis)" .

## References

1. <a href="https://en.wikipedia.org/wiki/Steganography" target="_blank">https://en.wikipedia.org/wiki/Steganography</a>
2. <a href="https://www.hindawi.com/journals/scn/2017/5397082/#B22" target="_blank">https://www.hindawi.com/journals/scn/2017/5397082/#B22</a>
3. <a href="https://securelist.com/steganography-in-contemporary-cyberattacks/79276/" target="_blank">https://securelist.com/steganography-in-contemporary-cyberattacks/79276/</a>
4. <a href="http://www.cse.wustl.edu/~jain/cse571-09/ftp/stegano/index.html" target="_blank">http://www.cse.wustl.edu/~jain/cse571-09/ftp/stegano/index.html</a>
5. <a href="http://www.ijarcs.info/index.php/Ijarcs/article/viewFile/2483/2471" target="_blank">http://www.ijarcs.info/index.php/Ijarcs/article/viewFile/2483/2471</a>
6. <a href="https://www.researchgate.net/profile/Osamah_Al-qershi/publication/292310394_Image_Steganography_Techniques_An_Overview/links/57f642ac08ae8da3ce574080/Image-Steganography-Techniques-An-Overview.pdf" target="_blank">Image Steganography Techniques: An Overview</a>
7. <a href="https://www.mathworks.com/help/vision/ref/psnr.html" target="_blank">https://www.mathworks.com/help/vision/ref/psnr.html</a>
8. <a href="https://www.mathworks.com/help/images/ref/ssim.html?s_tid=doc_ta" target="_blank">https://www.mathworks.com/help/images/ref/ssim.html?s_tid=doc_ta</a>
9. <a href="https://en.wikipedia.org/wiki/Structural_similarity" target="_blank">https://en.wikipedia.org/wiki/Structural_similarity</a>
10. <a href="https://arxiv.org/ftp/arxiv/papers/1202/1202.5289.pdf" target="_blank">Development Trends in Steganography</a>
11. <a href="https://pdfs.semanticscholar.org/f60e/d5f0f609956d0715659c823506feea036a31.pdf" target="_blank">Steganography and Steganalysis in Digital Multimedia: Hype or Hallelujah?</a>


<a href="https://twitter.com/share" class="twitter-share-button" data-show-count="false">Tweet</a><script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-115439306-1', 'auto');
  ga('send', 'pageview');
</script>
