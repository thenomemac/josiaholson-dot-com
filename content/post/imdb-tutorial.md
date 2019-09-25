---
title: "IMDB: deep sentiment analysis"
date: 2016-06-01
categories:
- programming
- projects
- data science
tags:
- data science
- python
- keras
- deep learning
- NLP
- LSTM
thumbnailImage: /images/imdb-notebook.png
thumbnailImagePosition: right
---

[This tutorial](https://github.com/thenomemac/IMDB-LSTM-Tutorial/blob/master/imdbLSTM.ipynb) walks users through an entire deep learning based NLP pipeline. The notebook demos a sentiment model for IMDB movie reviews using an LSTM and benchmarks the model against a linear model with tokenized TFIDF features.

The LSTM model is then introspected by looking at works most likely to flip a review from positive to negative and vice-versa. Then TSNE is used to visualize the the distribution of the most impactful words in movie reviews.

<img alt="" itemprop="image" src="/images/imdb-notebook.png">

