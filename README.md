# OSM: One-Shot Multi-speaker

## Problem Statement
One-Shot Multi-Speaker Text-to-Speech (OS MS TTS) systems are aimed to transform text into speech with voice determined by small single sample. The main problem here is to reproduce the new unseen voice without retraining the network. There is an approach with three main stages which is used to solve this problem.
The unique for each voice speaker embeddings, which reveal the voice characteristics, are generated at the first stage (Speaker Encoder).
At the second stage (Synthesizer) the text is transformed to mel-spectrogram using previously obtained embeddings. 
Finally, the speech is reproduced from the mel-spectrogram with the Vocoder. But there is lack of implementations with these three parts together. So, the goal of our project is to create a flexible framework to combine this parts and produce a functionality to replace methods in each part.

## Main Challenges
By now we see the following main challenges:
- The solution to our problem consists of three subtasks, which already have a great solutions. Therefore, the existing solutions for OS MS TTS are essentially a compilation of solutions for these individual problems, for which there are many ready-made and well-implemented solutions. The main challenge is to made the framework flexible and ensure the compatibility of individual parts.
- The methods used in each subtask differ in the set of parameters and the nature of the algorithm. Therefore, it will be quite difficult to provide them with a single API.

## Baseline Solution
We choose solution proposed by the instructors as a baseline, which can be found [here](https://github.com/CorentinJ/Real-Time-Voice-Cloning "here"). It is the implementation of \cite{Jia2018TransferLF} made in Google in 2018. Here authors use the speaker encoder, presented in \cite{speaker}, which generates a fixed-dimensional embedding vector, known as d-vector. As Synthesizer they use model based on Tacotron 2 \cite{Shen2018NaturalTS}. And an auto-regressive WaveNet-based as Vocoder \cite{Oord2016WaveNetAG}.
## Pros And Cons
The [Real-Time-Voice-Cloning](https://github.com/CorentinJ/Real-Time-Voice-Cloning "Real-Time-Voice-Cloning") contains the realizations of encoder, Tacotron 2 and WaveRNN. The whole pipeline described in \cite{Jia2018TransferLF}, including preprocessing steps, is also implemented in this repository. However, the project is not flexible enough. More specifically, in the current state it cannot be used as the framework for One-Shot Multi-Speaker Text-to-Speech system as there are no convenient mechanisms for manipulating with the three main modules. For example, the proposed multi-speaker TTS system in \cite{cooper2020} cannot be easily implemented with the help of [Real-Time-Voice-Cloning](https://github.com/CorentinJ/Real-Time-Voice-Cloning "Real-Time-Voice-Cloning") as there are no extensibility points which allow to adjust the pipeline for the new method. 
## Our Improvement 
Our plan is to use the [Real-Time-Voice-Cloning](https://github.com/CorentinJ/Real-Time-Voice-Cloning "Real-Time-Voice-Cloning") as starting point with implemented baseline. We will introduce the flexible modular design of the framework. Such approach will help us to create the convenient API for external users who will be able to use our framework for incorporating the Multi-Speaker TTS system in their products. The API will also let the users customize modules and pipeline steps without changing the source code of the framework if needed. We will implement several Speaker Encoders (LDE, TDNN) and add them to our framework as well.
## Roles of the Participants
Nikolay will design the modular architecture, API for external usage and training pipeline.
Gleb will implement working stack of models, write documentations and usage examples.


## Overview


## Setup
