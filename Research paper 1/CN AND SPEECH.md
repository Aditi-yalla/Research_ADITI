
# SpeechStew :Simply Mix All Available Speech Recognition Data to Train One Large Neural Network

**Abstract:**

We present SpeechStew, a speech recognition model that is trained on a combination of various publicly available speech recognition datasets: AMI, Broadcast News, Common Voice, LibriSpeech, Switchboard/Fisher, Tedlium, and Wall Street Journal.
SpeechStew simply mixes all of these datasets together, without any special re-weighting or re-balancing of the datasets.
SpeechStew achieves SoTA or near SoTA results across a variety of tasks, without the use of an external language model.
Our results include 9.0% WER on AMI-IHM, 4.7% WER on Switchboard, 8.3% WER on CallHome, and 1.3% on WSJ, which significantly outperforms prior work with strong external language models.
We also demonstrate that SpeechStew learns powerful transfer learning representations. 
We fine-tune SpeechStew on a noisy low resource speech dataset, CHiME-6. We achieve 38.9% WER without a language model,which compares to 38.6% WER to a strong HMM baseline with a language model.
* Index Terms: end-to-end speech recognition, multi-domain speech recognition*

**Introduction:**

End-to-end speech recognition models have seen remarkable success in recent years. For instance, end-to-end speechrecognition models have achieved state-of-the-art (SoTA) results on LibriSpeech and large proprietary datasets.
Thesuccess of these methods have often been attributed to the abundance of training data and the use of large deep models.
However, on noisy, low resource speech recognition datasets, such as CHiME-6 , where overfitting is a significant problem, end-to-end methods tend to struggle relative to HMMbased baselines.
 For example, the best previously published end-to-end model achieved 49.0% WER on the CHiME-6 dev set, while the best HMM model achieves 36.9% WER.
Multi-lingual training, multi-domain training, unsupervised pre-training, semi-supervised learningand transfer learning are some techniques proposed in the literature to enhance generalization.
These methods optimize speech recognition models on data from related tasks (typically of high resource), to help the specific task of interest (typically of low resource).
* This paper presents SpeechStew. SpeechStew is a simple approach to end-to-end speech recognition, which leverages
both multi-domain training and transfer learning.*
SpeechStew follows the following simple recipe:
1. Combine all available speech recognition data without
any domain-dependent re-balancing or re-weighting.
2. Train a single large neural network (a 100M or 1B parameter model) on the combined data.
Our method does not utilize any domain labels, or introduce any additional hyperparameters for combining the data.

**Literature Review:**

SpeechStew uses the Conformer 
RNN-T  architecture. We experiment with both the 100M
parameter  and the 1B parameter configuration. We find
that wav2vec pre-training  is needed to train the 1B parameter model. We apply the default hyperparameters from prior work including the learning rate schedule. 
We do not incorporate an external language model and does Multi-domain Training.

**Model Architecture:**

In this implementation, SpeechStew uses the Conformer RNN-T architecture. We experiment with both the 100M
parameter and the 1B parameter configuration.
We find that wav2vec pre-training is needed to train the 1B parameter model. 
We apply the default hyperparameters from prior work including the learning rate schedule. We do not
incorporate an external language model.

**Methodology:**

#Multi-domain Training
We combine the following datasets without any form of reweighting or resampling to construct the training set for SpeechStew:
1.AMI is approximately 100 hours of meeting recordings.
2. Common Voice. Common Voice is a crowd-sourced open licensed speech dataset. We use the version 5.1 (June 22 2020) snapshot with approximately 1500 hours.
The data was collected at 48 KHz, and we resampled it to 16 KHz.
3. English Broadcast News (LDC97S44, LDC97T22, LDC98S71, LDC98T28). English Broadcast News is approximately 50 hours of television news.
4. LibriSpeech is approximately 960 hours of speech from audiobooks.
5. Switchboard/Fisher (LDC2004T19, LDC2005T19, LDC2004S13, LDC2005S13, LDC97S62). Switchboard/Fisher is approximately 2000 hours of telephone conversations. The data was collected at 8 KHz, and we upsampled it to 16 KHz.
6. TED-LIUM v3 [33, 34]. TED-LIUM is approximately 450 hours of TED talks.
7. Wall Street Journal (LDC93S6B, LDC94S13B). WSJ is approximately 80 hours of clean speech.

**Results:**

We make two observations regarding the effectiveness of SpeechStew on ChiME-6 in particular. The first is that the amount of training time spent on the low-resource CHiME-6 data is greatly reduced. 
This is a natural product of the finetuning process. 
However, SpeechStew’s construction allows us to skip to that stage of the training process, thus reducing the risk of overfitting. Secondly, SpeechStew appears to be robust enough to handle noisy data. SpeechStew spends more time learning the salient features from a larger pool of less noisy data, and less time working with the more noisy CHiME-6 data.

**Discussion:**

Deep learning models have made significant progress from two
simple principles:
1. Train on more data [22, 25].
2. Train larger and deeper neural networks [23, 13].
Supervised data is expensive to acquire. SpeechStew takles this problem by simply mixing all publicly available speech recognition data. 
Our approach leverages on currently available resources, labelled and unlabelled. We hope our work will encourage future research to leverage on all training data available, as opposed to training on only task specific datasets.
Training large models is expensive, and impractical to do frequently (especially when one regularly encounters new tasks or new data). 
Our work on transfer learning demonstrates that one can simply finetune a pretrained model for only a few thousand gradient steps and achieve strong results. 
This is inexpensive and very practical. We hope our work will encourage further research to leverage on transfer learning in speech recognition.

**Conclusion:**

Summarize the key findings of the research paper.
Emphasize the significance of audio-visual speech recognition in enhancing real-world applications.
Encourage further exploration of multimodal approaches in speech processing.
Remember that this is a general outline, and actual research papers on audio-visual speech recognition may vary in terms of their content and focus.

**References:**

[1] A. Graves and N. Jaitly, “Towards End-to-End Speech Recognition with Recurrent Neural Networks,” in ICML, 2014.
[2] W. Chan, N. Jaitly, Q. Le, and O. Vinyals, “Listen, Attend and Spell: A Neural Network for Large Vocabulary    Conversational Speech Recognition,” in ICASSP, 2016.
[3] D. Park, W. Chan, Y. Zhang, C.-C. Chiu, B. Zoph, E. Cubuk, and Q. Le, “SpecAugment: A Simple Data Augmentation Method for Automatic Speech Recognition,” in INTERSPEECH, 2019.
[4] Y. Zhang, J. Qin, D. S. Park, W. Han, C.-C. Chiu, R. Pang, Q. V. Le, and Y. Wu, “Pushing the Limits of Semi-Supervised Learning for Automatic Speech Recognition,” in arXiv:2010.10504, 2020.
[5] C.-C. Chiu, T. Sainath, Y. Wu, R. Prabhavalkar, P. Nguyen, Z. Chen, A. Kannan, R. J. Weiss, K. Rao, E. Gonina, N. Jaitly, B. Li, J. Chorowski, and M. Bacchiani, “State-of-the-art Speech Recognition With Sequence-to-Sequence Models,” in ICASSP, 2018.

