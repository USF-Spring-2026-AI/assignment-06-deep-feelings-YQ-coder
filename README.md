[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/mW4WPbr-)

# A06 - Deep Feelings

## Setup

Install dependencies:

```bash
uv sync
```

## Analysis

### Enhancements that improved performance

- **WordNet lemmatization (alone): +0.36 pp** The gain may not be from morphological collapse itself. Lemmatization also shrinks the vocabulary, which acts as mild regularization for logistic regression.

### Enhancements that did not improve performance

- **Stopword removal (alone): −1.03 pp.** NLTK's list strips `not`, `no`, `n't`, the main negation cues a unigram BOW has. We can fix it by using a custom stopword list that keeps negations, or by adding bigrams / negation marking.
- **Stopwords + lemmatization: −0.89 pp.** Inherits the negation-cue problem above and would benefit from the same fixes.
- **spaCy mean embeddings: −7.43 pp.** Averaging dilutes polarity-bearing tokens and static vectors place "good"/"bad" close together. We can improve it by using contextual embeddings (e.g. BERT `[CLS]`) or TF–IDF-weighted averaging instead of a plain mean.

For reference, a domain-tuned transformer (`cardiffnlp/twitter-roberta-base-sentiment-latest`) scored **0.7448** zero-shot on the same test set (+8.80 pp over baseline), confirming the remaining headroom is reachable but requires a model that captures word order and context.

## LLM use disclosure

### LLM used
Claude

### Series of prompt
How can I load the input csv files for training?

What classifiers do scikit learn have?

How can I create a Logistic Regression classifier?

How to use CountVectorizer?

How to use NLTK for lemmatization?

How to use various embeddings with spaCy?

How can I improve the embedding approach?

### Was it helpful?
Yes.

### What I learned from its use
I learned how to create classification models with sklearn, NLP feature engineering with NLTK, embeddings with spaCy.

I got to learn more advanced features of these libraries even I did not use most of them in the assignment.
