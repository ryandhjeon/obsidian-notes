# Sequence to Sequence Learning with Neural Networks
#### (2014) - Ilya Sutskever, Oriol Vinyals, Quoc V. Le
**Link**: http://arxiv.org/abs/1409.3215
**DOI**: 
**Code/Link**:
**Tags**: #paper #seq2seq
**Rating**:

### Abstract

```
Deep Neural Networks (DNNs) are powerful models that have achieved excellent performance on difficult learning tasks. Although DNNs work well whenever large labeled training sets are available, they cannot be used to map sequences to sequences. In this paper, we present a general end-to-end approach to sequence learning that makes minimal assumptions on the sequence structure. Our method uses a multilayered Long Short-Term Memory (LSTM) to map the input sequence to a vector of a fixed dimensionality, and then another deep LSTM to decode the target sequence from the vector. Our main result is that on an English to French translation task from the WMT'14 dataset, the translations produced by the LSTM achieve a BLEU score of 34.8 on the entire test set, where the LSTM's BLEU score was penalized on out-of-vocabulary words. Additionally, the LSTM did not have difficulty on long sentences. For comparison, a phrase-based SMT system achieves a BLEU score of 33.3 on the same dataset. When we used the LSTM to rerank the 1000 hypotheses produced by the aforementioned SMT system, its BLEU score increases to 36.5, which is close to the previous best result on this task. The LSTM also learned sensible phrase and sentence representations that are sensitive to word order and are relatively invariant to the active and the passive voice. Finally, we found that reversing the order of the words in all source sentences (but not target sentences) improved the LSTM's performance markedly, because doing so introduced many short term dependencies between the source and the target sentence which made the optimization problem easier.
```

### Introduction

*Background*
- NN are similar to conventional statistical models, but learn an [[intricate]] computation.
- [[Deep Neural Networks]] (DNN) uses gradient decent with backpropagation to learn a complicated computation well.

*Limitation*
- DNN's input and outputs encoded with vectors of fixed dimensionallity
- The length of input and output could be different in `sequential data` problem; `Speech recognition` or `Translation`

*Propose*
![[Pasted image 20230319153846.png]]
- [[Long Short-Term Memory]] (LSTM) can solve the issue, by using multiple LSTMs. Each LSTM can read the input sequence, one timestep at a time, and use another LSTM to extract the output sequence from that vector. 
- Map the entire input sentence to the context vector. Then, the decoder receives the information on the input and hidden state, outputs the translation

*Result*
- The `SOS` could be used and get better result
- Better result with input reversed `C - B - A`
- Better result with `Ensemble method` (Deep LSTM), which is better than traditional SMT methods
- Best result with LSTM + SMT 
- LSTM did not suffer on very long sentences

### The model

- [[Recurrent Neural Network]] (RNN) can easily map sequences to sequences whenever the alignment between the inputs the outputs is known ahead of time.
- However, when the input and output sequence have different lengths, it gets complicated

### Experiment

*Dataset*
- **WMT' 14** English to French translation task dataset
- 12M sentences (348M French words, 304M English words)
- Used fixed vocab for both languages, as typical language models rely on a representation for each word
- Used 160,000 of the most frequent words for the source language and 80,000 of the most frequent words for the target language
	- Meaning Only using the words within the 160,000 list

*Decoding *