---
title: "Data Engineering: The most important part of Data Science"
date: 2018-06-01
categories:
- programming
- data science
- data engineering
tags:
- data science
- data engineering
- ETL
- opinion
slug: data-engineering-why
thumbnailImage: /images/hadoop-logo.png
thumbnailImagePosition: right
---

## TLDR;

Data Engineering is the most important job title in your company that should have head count zero. Hint: just hire more Data Scientists.

## My thoughts on Data Engineering

Please take everything said here as an opinion piece meant to be thought provoking.

Definition: in this article "data engineer" is referring to the "ETL" consultant to the Data Science Team. **If you're a data engineer building data inrfastructure and reusable software components to empower the data science team, then please keep doing that.**

First, I want to start off by stating that "data engineering" is the most important role in any data driven company. Second, I don't think that a company needs any head count with that job role.

My assertion is that data engineering is a subset of data science (ML engineering or whatever you want to call it). In some theoretical corporate job description world, the data engineer should clean up the dataset, land the output as a "clean" CSV format, then deliver the artifact to the Data Science team. Data Scientists read the clean data with `pd.read_csv` and apply some ML magic. However, in reality the data "munging process" is much more complex than that. Many of the most important features for ML models are discovered in the data engineering (ETL) process. This means that your data engineers need to know what information in the source PROD data is (and isn't) useful in the modeling process. If the data ETL requires knowing about the ML pipeline than your companies data engineer is actually a data scientist.

## A concrete example

In many data sources, I've seen a categorical variable lazily stored in the DB as a string. The values in the table for column "lazycategory" are: `["NY", "AL", "", NULL]`. The enterprising data engineer would probably "clean" this data by assigning the empty string to `NULL`. However, more careful analysis with the response variable "the customer purchased" would have revealed that the empty string was one of the most predictive categories. Wait what? Further digging into the DBA's tribal knowledge uncovers that the empty string variables were customers ported into the Database from a third party API that interfaces with the companies internal purchasing system. Orders on this API have a low/high purchase rate, and in the enterprise systems the only pragmatic way to identify data side loaded from the API is the presence of the "quote on quote" bad data element the "empty string" in our data warehouse. 

Countless times I've observed that the most important features in my ML models are discovered by careful analysis of the data engineering pipeline. **Missing data or messy data can be a valuable model feature.** Data Engineers must understand how the final data product will be used, or the "cleaned" data will be a lossy product that's not optimal for the final algorithm being used to model. 

One more aside, logging input/output statistics from the model's PROD API is the most important way to ensure deployed models are actually working as expected. Data Scientists (ML engineers) must know how to instrument their models with the platforms metric and logging infrastructure. The line between data engineering and ML engineering becomes extremely fuzzy, considering, this feedback loop.

Closing points:

- Hire Data Engineers and provide training/mentoring so they know what features are useful in the modeling pipeline
- Provide a path for Data Engineers (Jr Data Scientists) to grow and move to Sr Roles
- Long live the data-scientist-data-engineer.
