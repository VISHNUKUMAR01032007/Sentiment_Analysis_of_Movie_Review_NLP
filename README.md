# 🎬 Movie Review Sentiment Analysis

Comparing Word2Vec and Sentence Transformer embeddings — paired with Random Forest and Neural Network classifiers — to predict whether a movie review is positive or negative.

### Problem Statement

The entertainment industry needs a fast, reliable way to gauge audience sentiment. Manually reading thousands of reviews is slow and misses subtle cues. This project builds an AI-based sentiment analyzer that automatically classifies movie reviews as positive or negative, giving quick, actionable insight into audience opinion.

### Dataset

~10,000 movie reviews with two columns:

### Approach

Two text embedding techniques were tested, each paired with two classifiers, for four models total:

Word2Vec (Gensim) — 300-dimension word vectors, averaged per review to produce a document-level embedding.

Sentence Transformers (all-MiniLM-L6-v2) — 384-dimension embeddings that capture full sentence context rather than averaged word meaning.

### Key observations:

Word2Vec + Random Forest underfits — both train and test accuracy are low and close together, meaning the model isn't learning strong patterns from averaged word vectors.

Switching to a Neural Network improves results with the same Word2Vec embeddings, but there's a ceiling since averaged word vectors lose full sentence context.

Sentence Transformer embeddings outperform Word2Vec across the board, since they encode full sentence meaning rather than an average of individual words.

Sentence Transformer + Neural Network reaches the highest test accuracy but shows clear overfitting (99.6% train vs. 79.2% test).

### Best Model

Sentence Transformer + Random Forest is selected as the best model. While the Sentence Transformer + Neural Network has a slightly higher raw test accuracy, it overfits heavily. The Random Forest variant offers the best balance of accuracy and generalization, with a much smaller train/test gap.
