---
layout: post
title:  Friendly Introduction to Speech Recognition
date:   2019-10-16 00:00:00
categories: [Artificial Intelligence]
tags: [Artificial Intelligence, speech recognition]
published: true
comments: true
toc: true
---


<center><img src="/images/post6/Speech-Recognition-Intro.png" alt="Introduction to NDK for mobile apps" style="max-width: 100%; height: auto; margin:2%;"/></center>


- **Alexa**! Turn on the Lights.
- **OK Google**! call Mom.
- **Hey Siri**! Take a picture.
- **. . .**

<style>
.lettrine {
	color: #292929;
	float: left;
  font-size:60px;
	font-weight:bold;
	line-height:40px;
	padding-top:4px;
  padding-right:4px;
	font-family: arial;
}
</style>
<span class="lettrine">M</span>ost likely, you use one of these wizards to perform an action or just to have fun with it. These wizards go through several steps to perform an action from your request. In this post, we will discuss the evolution of speech recognition throw time. We will then detail the model and the recent speech recognition applications.


### A run back to history

Speech recognition is the ability of a machine or program to identify words and phrases in spoken language and convert them to a machine-readable format. Rudimentary speech recognition software has a limited vocabulary of words and phrases, and it may only identify these if they are spoken very clearly.

The summary of the evolution of the speech recognition carrier is presented in the figure down below.

<center><img src="/images/post6/timeline.png" alt="Introduction to NDK for mobile apps" style="max-width: 70%; height: auto; margin:2%;"/></center>

<center>
Voice recognition timeline (<a href="https://www.knowles.com/about-knowles/blog/speech-recognition">Source</a>)
</center>
<br/>

1- The first speech recognition system, Audrey, was developed back in 1952 by three Bell Labs researchers. Audrey was designed to recognize only digits

2- Just after 10 years, IBM introduced its first speech recognition system IBM Shoebox, which was capable of recognizing 16 words including digits. It could identify commands like “Five plus three plus eight plus six plus four minus nine, total,” and would print out the correct answer, i.e., 17

3- The Defense Advanced Research Projects Agency (DARPA) contributed a lot to speech recognition technology during the 1970s. DARPA funded for around 5 years from 1971–76 to a program called Speech Understanding Research and finally, Harpy was developed which was able to recognize 1011 words. It was quite a big achievement at that time.

4- In the 1980s, the Hidden Markov Model (HMM) was applied to the speech recognition system. HMM is a statistical model which is used to model the problems that involve sequential information. It has a pretty good track record in many real-world applications including speech recognition.

5- In 2001, Google introduced the Voice Search application that allowed users to search for queries by speaking to the machine. This was the first voice-enabled application which was very popular among the people. It made the conversation between the people and machines a lot easier.

6- By 2011, Apple launched Siri that offered a real-time, faster, and easier way to interact with the Apple devices by just using your voice. As of now, Amazon’s Alexa and Google’s Home are the most popular voice command based virtual assistants that are being widely used by consumers across the globe.

### What's Speech ?

Speech is a complex phenomenon. People rarely understand how is it produced and perceived. The naive perception is often that speech is built with words and each word consists of phones. The reality is unfortunately very different. Speech is a dynamic process without clearly distinguished parts. It’s always useful to get a sound editor and look into the recording of the speech and listen to it. Here is for example the speech recording in an audio editor.

<center><img src="/images/post6/waveform.png" alt="Introduction to NDK for mobile apps" style="max-width: 70%; height: auto; margin:2%;"/></center>

<center>
Voice recognition timeline (<a href="https://cmusphinx.github.io/wiki/tutorialconcepts/">Source</a>)
</center>
<br/>

All modern descriptions of speech are to some degree probabilistic. That means that there are no certain boundaries between units, or between words.

### Recognition process

According to the speech structure, three models are used in speech recognition to do the match:

1- An acoustic model contains acoustic properties for each senone. There are context-independent models that contain properties (the most probable feature vectors for each phone) and context-dependent ones (built from senones with context).

2- A phonetic dictionary contains a mapping from words to phones. This mapping is not very effective. For example, only two to three pronunciation variants are noted in it. However, it’s practical enough most of the time. The dictionary is not the only method for mapping words to phones. You could also use some complex function learned with a machine learning algorithm.

3- A language model is used to restrict word search. It defines which word could follow previously recognized words (remember that matching is a sequential process) and helps to significantly restrict the matching process by stripping words that are not probable. The most common language models are n-gram language models–these contain statistics of word sequences–and finite state language models–these define speech sequences by finite state automation, sometimes with weights. To reach a good accuracy rate, your language model must be very successful in search space restriction. This means it should be very good at predicting the next word. A language model usually restricts the vocabulary that is considered to the words it contains. That’s an issue for name recognition. To deal with this, a language model can contain smaller chunks like subwords or even phones. Please note that the search space restriction in this case is usually worse and the corresponding recognition accuracies are lower than with a word-based language model.

Those three entities are combined together in an engine to recognize speech. If you are going to apply your engine for some other language, you need to get such structures in place. For many languages there are acoustic models, phonetic dictionaries and even large vocabulary language models available for download.



### References

1- [Speech Recognition - wikipedia](https://en.wikipedia.org/wiki/Speech_recognition)

2- [Learn how to Build your own Speech-to-Text Model (using Python)](https://medium.com/analytics-vidhya/learn-how-to-build-your-own-speech-to-text-model-using-python-cd8a6564e720)

3- [Knowles - speech-recognition](https://www.knowles.com/about-knowles/blog/speech-recognition)

4- [Basic concepts of speech recognition](https://cmusphinx.github.io/wiki/tutorialconcepts/)
