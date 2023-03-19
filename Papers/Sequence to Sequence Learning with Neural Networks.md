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

*Decoding & Rescoring*
**Training**
Basic training objective of [[Neural Network]]
$$1/|S| \sum_{(T,S)\in{S}}\log{p}(T|S)$$
- `S`: Source
- `T`: Target
- For input `S`, the target`T` should be outputed as 1:1. With the log, the probability goes up

**Testing**
- Once training is complete, we product translations by finding the <u>most likely translation </u>according to the LSTM.
- 매번 S가 주어질때마다 가장 높은 확률을 가진 Target sentence를 return할 수 있는 T를 갖게 되는것
$$ \hat{T} = \arg \max_{T}p(T|S) $$
- [[Beam search]] decoder was also used. Not just using the best probabilistically high sentences, but goes in deeper for the higher probability

*Limitation*
- More <u>confident predictions</u> in the <u>early parts</u> of the target sentence and to <u>less confident</u> predictions in the <u>later parts</u>.

*Training Details*
- Deep LSTMs with 4 layers
- Initialized all ofthe LSTM's parameters with the uniform distribution between -0.08 and 0.08
- Used [[stochastic gradient descent]] without momentum, with a fixed learning rate of 0.7. After 5 epochs, we <u>begun halving the learning rate every half epoch</u>. We trained our models for a total of 7.5 epochs.
- We used batches of 128 sequences for the gradient and divided it the size of the batch (namely, 128).
	- 학습과정에서 Model forwarding 할때 사용하는 문장의 개수가 128개
- Minibatch of 128 randomly chosen training sentences will have many short sentences and few long sentences
	- Minibatch에 있는 sentence들의 길이가 비슷하도록 조절해서, 학습속도 Up.

*Experimental Results*
- While the decoded translations of the LSTM ensemble do not outperform the best WMT’14 system, it is the first time that a pure neural translation system outperforms a phrase-based SMT baseline on a large scale MT task by a sizeable margin, despite its inability to handle out-of-vocabulary words.
	- 가장 좋지는 않지만 DNN 기반 Method의 가능성을 잘 보여준다

*Model Analysis*
![[Pasted image 20230319172326.png]]
- 2-dimensional PCA projection of the LSTM hidden states
- Phrases are clustered by meaning

### Conclusion

- Deep LSTM can outperform a standard SMT-based system
- Reversing the words in the source sentences made result better