---
completed: false
next: 
prev: 
---
# Tokenization in NLP
The process of breaking down text into smaller units called tokens.

# Open-Vocabulary Modeling
A method where models handle a variety of words beyond a fixed vocabulary.
- Open-vocabulary modeling can process new or rare words that do not appear in training data.

# Subword-Based Approaches
Techniques that break words into smaller subunits to create tokens.
- Allows for a smaller vocabulary while preserving the ability to represent unseen words.
- Examples include Byte-Pair Encoding (BPE) and Unigram LM.

# Byte-Pair Encoding (BPE)
A compression-based subword tokenization method.
- Iteratively replaces the most frequent pair of adjacent symbols with a new symbol.
- Commonly used to avoid out-of-vocabulary (OOV) issues.

# Unigram LM
A probabilistic approach that constructs subword units using a simple language model.
- Starts with an extensive set of subword units and prunes the least probable ones.
- Supports subword regularization to enhance performance.

# Pre-Tokenization
An initial process that segments text into word-like units before further splitting.
- Tools like Moses’ tokenizer and the Hugging Face Tokenizers package are examples.
- Modern pre-tokenization might involve normalization or other transformations.

# Character-Level Models
Models that use individual characters as tokens.
- Useful for languages with high type-token ratios and productive morphology.
- Can handle novel words but lead to longer sequences and higher computational costs.

## Character-Based Augmentation
Approaches that augment word models with character-level information.
- Helps models learn about word structure and deal with rare words.
- Example: fastText uses character n-grams for embeddings.

# Hybrid Tokenization Models
Models that combine word-level and character-level approaches.
- Examples include ELMo, which improves handling of out-of-vocabulary words.

# Neural Language Models (NLMs)
AI models that predict the probability of sequences of words or characters.
- Evolved from simpler n-gram models.
- Use architectures like RNNs, LSTMs, and Transformers.

# Hierarchical or Segmental Models
Advanced models that learn to group characters or subwords into larger units.
- Example: Segmental Neural Language Models (SNLM) use dynamic programming to predict segmentations.
- Useful for tasks like unsupervised word segmentation.

# Bayesian Nonparametric Approaches
Statistical models that do not assume a fixed number of parameters.
- Allow for flexible modeling of word and subword distributions.
- Examples include Dirichlet Processes and the Pitman-Yor Process.

## Unsupervised Word Segmentation
A task that finds word boundaries without labeled data.
- Common in languages without clear word delimiters like Chinese or Japanese.
- Approaches include Bayesian models and mutual information-based methods.

# Tokenization in Multilingual NLP
The challenge of handling text in multiple languages within a single model.
- Shared vocabularies can help with cross-lingual transfer but may introduce biases.
- Solutions include oversampling low-resource languages and adding new subword units.

# Character-Level and Byte-Level Processing
Models that bypass traditional tokenization.
- Byte-level models use raw bytes, allowing for comprehensive language coverage.
- Example: ByT5 and CANINE use character and byte-level modeling for robustness.

# Visual Featurization
Tokenization-free models that represent text visually.
- Sentences are rendered as images and processed directly from pixel data.
- Improves robustness to noise and handles non-standard text variations.

# Comparison of Tokenization Methods
Studies show mixed results on which methods perform best.
- Morphologically driven tokenization can improve results in some languages.
- Simpler methods like BPE are often chosen for their balance of speed and performance.

# Conclusion on Tokenization
No single tokenization method fits all scenarios.
- Character-level and byte-level models provide robustness but increase sequence length.
- Subword-based models like BPE and Unigram LM are prevalent for their efficiency and effectiveness.

