# Jigsaw Unintended Bias in Toxicity Classification

> Detect toxicity across a diverse range of conversations



## Description

Can you help detect toxic comments ― *and* minimize unintended model bias? That's your challenge in this competition.



The Conversation AI team, a research initiative founded by [Jigsaw](https://jigsaw.google.com/) and Google (both part of Alphabet), builds technology to protect voices in conversation. A main area of focus is machine learning models that can identify toxicity in online conversations, where toxicity is defined as anything *rude, disrespectful or otherwise likely to make someone leave a discussion*.



Last year, in the [Toxic Comment Classification Challenge](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge#description), you built multi-headed models to recognize toxicity and several subtypes of toxicity. This year's competition is a related challenge: building toxicity models that operate fairly across a diverse range of conversations.



Here’s the background: When the Conversation AI team first built toxicity models, they found that the models [incorrectly learned to associate](https://medium.com/the-false-positive/unintended-bias-and-names-of-frequently-targeted-groups-8e0b81f80a23) the names of frequently attacked identities with toxicity. Models predicted a high likelihood of toxicity for comments containing those identities (e.g. "gay"), even when those comments were not actually toxic (such as "I am a gay woman"). This happens because training data was **pulled from** available sources where unfortunately, certain identities are overwhelmingly referred to in offensive(모욕적인) ways. Training a model from data with these imbalances risks simply mirroring those biases back to users.



cf) pull from : ~에서 끌어내다.



In this competition, you're challenged to build a model that recognizes toxicity and minimizes this type of unintended bias with respect to mentions of identities. You'll be using a dataset labeled for identity mentions and optimizing a metric designed to measure unintended bias. Develop strategies to reduce unintended bias in machine learning models, and you'll help the Conversation AI team, and the entire industry, build models that work well for a wide range of conversations.



*Disclaimer: The dataset for this competition contains text that may be considered profane, vulgar, or offensive.*



### Acknowledgements

The Conversation AI team would like to thank Civil Comments for making this dataset available publicly and the [Online Hate Index Research Project](http://dh.berkeley.edu/projects/online-hate-index-ohi-research-project?utm_source=BCNM+Subscribers&utm_campaign=d5d78bba5e-natasha-schull-oct12_COPY_01&utm_medium=email&utm_term=0_eb59bfff9e-d5d78bba5e-281420185) at [D-Lab](https://dlab.berkeley.edu/), University of California, Berkeley, whose labeling survey/instrument informed the dataset labeling. We'd also like to thank everyone who has contributed to Conversation AI's research, especially those who took part in our last competition, the success of which led to the creation of this challenge.