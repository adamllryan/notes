---
id: Machine Translation
aliases: []
tags: []
---

# Translation

Translation is one of the holy grail problems in machine learning. Because of the varying difficulty between translating difference groups of sentences, we encounter many struggles when trying to build a model for this.

# Machine Translation Basics

MISSING

Machine Translation is hard because: MISSING

### Vauquois Pyramid

MISSING

# Translation Quality

We use two metrics to evaluate the quality of a translation:

1. **Fluency**: How well the translation reads in the target language.
2. **Adequacy**: How well the translation captures the meaning of the source language.

# Evaluation Metrics

Manual evaluation is the most accurate, however it is the most expensive. As a result, we try to use automatic evaluation metrics. One metric we may use is **BiLingual Evaluation Understudy** (BLEU), which is:

$$
BLEU = \exp(\frac{1}{N}\sum_{n=1}^{N} \log p_n)
$$

where $BP$ is the brevity penalty, $w_n$ is the weight for $n$-grams, and $p_n$ is the precision for $n$-grams.

We also define $p_n$ as:

$$
p_n = \frac{\text{number of n-grams in reference and hypothesis translation}}{\text{number of n-grams in hypothesis translation}}
$$

When we use BLEU, we make two modifications:

1. We want to avoid $log(0)$, so we smooth $p_i$.
2. We only allow n-grams in reference to be used once.

After this, we can observe that BLEU performs relatively well compared to human evaluation.

An alternative to BLEU is **METEOR**, which is based on the harmonic mean of precision and recall. METEOR is more robust than BLEU, but it is also more expensive to compute.

# Data

Statistical machine translation requires parallel data, which is a set of sentences in one language and their translations in another language. This data is used to train the model, but it is difficult to get and does not work in every situation.

# Statistical Machine Translation (SMT)

We can drop a lot of the criteria for translation quality and still get a good translation. Using

$$
\psi(w^{(s)}, w^{(t)}) = \psi_A(w^{(s)}, w^{(t)})+ \psi_F(w^{(t)})
$$

where $\psi_A$ is from aligned corpora and $\psi_F$ is from monolingual corpora.

This allows us to disregard parallel corpora and estimate parameters of $\psi$ from monolingual corpora.

The noisy channel model is a generative model for translation. We have a source sentence $f$ and a target sentence $e$. We want to find the most likely translation $e$ given $f$:

$$
e = \arg\max_e P(e|f) = \arg\max_e P(f|e)P(e)
$$

where $P(f|e)$ is the translation model and $P(e)$ is the language model.

REDO THIS SECTION + noisy channel model, kinda skipped over these

# IBM Models

Something about the guys who made this made a hedge fund and got super rich and then won awards then they tried to take it back because of his politics.

But this model uses **alignments**. We have a source sentence $f$ and a target sentence $e$. To align these, we match the best words with matching words together (match names, verbs, nouns, etc. ).

Then, we incorporate these alignments using a joint probability model. We can make further assumptions by making two independence assumptions:

1. Alignment probability factors across tokens.
2. Translation probability factors across tokens.

We want to achieve translation by doing sum over all possible alignments' probabilities. However, this becomes very expensive very fast. This approach leads to **IBM Model 1**.

IBM Model 1 assumes that every alignment is equally likely. In this model, each source word is aligned to at most one target word. A goal for this is to use **MLE** to compute probabilities, but we need to have word-to-word alignments, which are not common.

A solution to this leads to **IBM Model 2**. This model uses a hidden variable to model the alignment. We can use the **Expectation-Maximization** algorithm to estimate the parameters of this model.

Model 3 makes each word have a probability of being related to 0,1, or 2 words.
4/5 are related and fix similar issues. (he spoke too fast). Model 6 is a combination of model 4 and a hidden markov model. Models 3 through 6 make weaker assumptions but are harder to optimize.
Overall, model 6 was when IBM models were considered "solved". It was at this time that Google and other companies were building technology based on this.

# Phrase-based Machine Translation

Certain phrases are unrelated to each other even though they have the same meaning. As a result, we can change our model to build alignments using whole **phrases** instead of words.

Now, instead of using words, we use _span_ to _span_ groups of words.

# Syntactic Machine Translation

Even further, we can replace phrases with syntactic structures. Instead of groups of words, we use parts of speech to conduct our translation. If we can use CFGs to perform our translation, that is our most accurate method to translate. And performance-wise, it is near the same as using Phrase-based translation.

# Neural Machine Translation (NMT)

Neural machine translation is one of the most striking methods where neural networks began to dominate. It went very quickly from being a wild idea to getting something done.

Traditional SMT systems, used by Google, Microsoft, and others, were based on IBM models. Within a few months, NMT systems could easily outperform these huge systems with less engineers.

A single neural network is used to translate from our source to target. We have a second one to convert our vectors into our output language. These are called **encoder** and **decoder** networks.

# Sequence to Sequence Models

Sequence to Squence models are different. Using an RNN, we encode an entire input sequence into a single vector. In a lossy way, the sequence is squashed into a "thought" vector, which encodes the value of the (so far) encoded sequence as it is fed in.

This can lead to vanishing or exploding gradients, though, so we need to use LSTM to prevent this.

SMT has a lot of structure and huge systems, and NMT has no internal structure and is fully determined by itself.

# Beam Serach

Beam search is a way to search for the best translation. We start with a single hypothesis, and then we expand it. We keep the best $k$ hypotheses, and then we expand those. We continue this until we reach the end of the sentence.

Beam search is a more efficient middle-ground between greedy search and exhaustive search. Greedy search will give us the first result, and exhaustive search requires the computation of every possible sequence.

Beam decoding requires tokens to start and stop sequences. We can use this to early terminate or stop when our hypothesis is done. Then, we select our top hypotheses using _normalized_ likelihood score. If we use raw likelihood score, we will get shorter hypotheses instead.

STOP 17
