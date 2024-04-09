# Sequence 2 Sequence
Seq2Seq is a very versaitile technology, useful in summarization dialogue, parsing, and question answering. 

Vanilla seq2seq is very problematic because a single encoding vector must capture all of the information about its source sentence. Longer sentences will lead to vanishing gradients or overfitting. We can try to fix this by introducing attention

## Attention

**Attention** is the neural equivalent of alignment models. At each time step during decoding, we will focus on a certain part of the source sentence, depending on the decoder's current hidden state. This is usually implemented as a probability distribution over the hidden states of the encoder. 

We use the attention distribution to take the weighted sum of the encoder's hidden states (creating a pooling layer), and the attention output will mostly contain information about the hidden states with higher attention. Think of removing unnecessary parts of speech from a sentence. 

We have 3 types of attention:
- Dot-product
- Multiplicative
- Additive

## Rare Words

Having rare words means that we can have large amounts of vocabularies, leading to expensive calculations. We can combine chunks or pieces of words to build more complex words. 

**Byte-pair encoding** is the process of building a vocabulary using "byte-pairs" of words, or the chunks of words mentioned above. 

**Backtranslation** is the process of training a neural machine translator. We can either force the system to generate a corpus T to train our model, or we can generate synthetic sources using backtranslation. 

### RNN vs. Transformers

The main difference between RNNs and transformers is that transformers follow the structure of a traditional MLP layer with more backconnected weights, while RNNs follow more of a hidden markov model structure. 

