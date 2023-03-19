(RNN) can easily map sequences to sequences whenever the alignment between the inputs the outputs is known ahead of time.

*Limitation*
- It is not clear how to apply an RNN to problems whose input and the output sequences have different lengths with complicated and non-monotonic relationships.
- It would be difficult to train the RNNs due to the resulting long term dependencies. However, the Long Short-Term Memory (LSTM) is known to learn problems with long range temporal dependencies, so an LSTM may succeed in this setting.

##### Reference
[[Sequence to Sequence Learning with Neural Networks]]