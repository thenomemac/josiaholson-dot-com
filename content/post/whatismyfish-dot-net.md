---
title: "WhatIsMyFish.net: Machine Vision to save Fish"
date: 2018-04-01
categories:
- programming
- projects
- data science
tags:
- data science
- flask
- javascript
- golang
- tensorflow
- keras
- erie hack
- machine vision
slug: whatismyfish-dot-net
thumbnailImage: /images/whatismyfish.png
thumbnailImagePosition: right
---

## TLDR;

Train a neural net to identify midwestern fish specifes and create an interactive web app identify invasive specicies from user photos.

[whatismyfish.net](http://whatishmyfish.net) is currectly in a mid-refactor state as I'm re-writing the python/flask web app in golang for fun and profit.

## Project Summary:

The mobile web app [WhatIsMyFish.net](http://whatismyfish.net) has been awarded 3rd place in the semi-final round of Eriehack.io : a first of its kind regional, eco focused engineering challenge. Users of WhatIsMyFish.net snap photos of the fish they just caught and the app tags the species of the fish, returns the relevant fishing regulations for their location and warns them if they’ve caught an invasive species. The machine learning algorithms used continuously improve as more anglers use the app and submit data. Importantly, data collected is made freely available to marine researches to help control fish populations and improve the ecosystem of our fresh water resources.

## Press:

- [My Q&A with Cleveland.com](http://www.cleveland.com/metro/index.ssf/2017/05/a_computer_algorithm_to_identi_1.html)
- [Cleveland.com Contest Update](http://www.cleveland.com/metro/index.ssf/2017/04/saving_lake_erie_3_local_teams.html)
- [ErioHack.io Home](http://eriehack.io/)

## WhatIsMyFish.net Video Demo:

<iframe width="560" height="315" src="https://www.youtube.com/embed/XSroZJvoBbw" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


## Technical Details

The [source code](https://github.com/thenomemac/fish.io.ai) deployed at the time of the contest finally was a python/flask app. The images uploaded by the user where cached on the server's local filesytem. A seperate python process was triggered by filesystem events. This process would load the fine-tunned resnet50 model and score the image. SQLite3 was used as a "queue" between the processes to pass model results and image meta data. 

I'm currently in the process of refactoring the app to golang. [This implementation](https://github.com/thenomemac/gofish) will used embedded tensorflow and be deployed as a static binary, ensuring this app will work for years to come without worrying about dependencies. Additionally, this version of the app uses a custom no-sql DB built on top of S3 to buffer the user submitted images and store image meta-data.
