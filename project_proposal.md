# NLP Group 8 Project Proposal
## Group Members and Roles

* Tony Li (yl4649) - Theoretical Issues (Linguistics & Math), Programming

* Qian Chen (qc543) - Paper Writing, Programming

* Xinyu Xie (xx708) - Programming, Evaluation

## Problem Statement

As professors play a crucial part in college students’ academic experience, online platforms of rating and reviewing professors, such as RateMyProfessors.com (RMP), have become very popular. From sharing basic class information such as attendance policy and textbook requirements, to rating the quality and difficulty of a class and giving personal comments on teaching style and workload, students share their experience and influence the decisions of others, while also having their own decisions influenced. Given the large amount of data that cover the opinions of college students from all over the country, it is interesting to delve into the data and dig deeper into the sentiments behind students' comments.

A review on RateMyProfessors.com consists of several quantitative rating scores (quality, level of difficulty, etc), and also the student’s subjective comment in natural language. Such a design in nature facilitates the development and evaluation of a sentiment analysis system, as it makes it possible to have the system make its judgement on the sentiment of a review based on the natural language comment, and evaluate the result with regard to the quantitative scores already available on the website. Although this sentiment analysis system is built targeting analyzing student reviews for college faculty, it can also be generalized to analyze a wider range of online verbal comments, and help the entities being reviewed identify their potential strengths and weaknesses.

## Evaluation Plan

Our final system (or, application) will take comments of a random professor on RMP as input, run a sentiment analysis based on those comments, and provide basic sentiment weights (in percentage) and sentiment score (in scale of 5) as output, e.g. "sentiment weights: negative - 33%, neutral - 34%, positive - 33%; sentiment score: 3.0".

The dataset that will be used in our system include:

  * an unlabeled corpus of commentary on some randomly-chosen, presumably from NYU, professors that we request from RMP;
  * a pre-labeled corpus of commentary on any topics available online;
  * a pre-labeled corpus of random commentary from RMP labeled by ourselves.
  * an online-available general-purpose sentiment lexicon that classifies words as negative, neutral or positive.
  * a self-labeled context-based sentiment lexicon that classifies words as negative, neutral or positive.

We will divide the corpus into three subsets: development stage, training stage, and testing stage. The pre-labeled dataset of commentary will be divided into development and training stage randomly, and collectively used to build up our system. We will also incorporate a sentiment lexicon in this process. Then, the unlabeled commentary on professors from RMP will be used in testing stage and generate the outputs.

To test the performance of our system, we will compare the followings in terms of accuracy, precision, recall rate, and F-measure, if applicable:

  * the sentiment score generated by our system and the overall rating on RMP;
  * the sentiment weights generated by our system and the sentiment weights from a subjectivity dataset (which will most likely be labeled by ourselves too).

## Strategy

The designed workflow of our system is stated below. Notice that this workflow is only 	tentative and subject to change: 
  * __Minimal Viable Product__: 
    <p>
    A Unigram System of Sentiment Analysis
    </p>
    <br>
  * __Full Workflow__: 
    <p>
    We will incorporate the sentiment lexicon with our self-labeled context-based lexicon, and build up an unigram system that attributes each incoming token with a sentiment weight (e.g., "negative - 30%, neutral - 20%, positive - 50%"). Then, extend the unigram system to a N-gram system, presumably a phrase system which, instead of attributing to each individual token, attributes sentiment weights to Noun Phrase, Verb Phrase, Adjective/Adverb Phrase, etc.. Then, for every commentary of a professor, we input the commentary into the system and obtain an aggregation of sentiment weights of that commentary. At the end, we calculate the sentiment score for all the commentary of a professor based on a weighted average formula.
    </p>

## Academic Articles

* [_Context-Dependent Sentiment Analysis in User-Generated Videos_](https://www.aclweb.org/anthology/P17-1081.pdf)
    <p>
    The article is related to our project as it proposed an architecture that incorporates context-dependent extraction. Although our project will most likely not feature a multimodal framework, it is still important to consider context dependency in our sentiment analysis since oftentimes sentiment is expressed implicitly and requires the contextual knowledge about the mood of the speaker and his/her general opinion about the professor.
    </p><br>

* [_Learning Word Vectors for Sentiment Analysis_](https://www.aclweb.org/anthology/P11-1015.pdf)
    <p>
    The article proposes a model that captures both semantic and sentiment similarities among words. The sentiment component is capable of embracing social and attitudinal aspects of meaning by using the vector representation of words to predict the sentiment annotations on contexts in which the words appear. 
    </p><br>

* [_A Data-Driven Analysis of RateMyProfessors' Student Reviews on Universities_](https://dmc.tamuc.edu/digital/collection/p15778coll7/id/519/)
    <p>
    Besides basic sentiment analysis of verbal comments on RMP, the article focuses on more aspects: aspect-based sentiment analysis to extract the specific aspect of the verbal comments and clustering of institutes with respect to the sentiment analysis results. We can totally implement parts of its evaluation method and compare our findings with his (which only focuses on the universities in Texas). Noticeably, its data collection was achieved by using python script to extract comments from RMP and the data was saved in JSON format. 
    </p><br>

* [_Detecting Objectifying Language in Online Professor Reviews_](https://www.aclweb.org/anthology/2020.wnut-1.23.pdf)
    <p>
    The article also targets the same website as our project does—-RateMyProfessors.com, defines objectifying or attractiveness commentary as reviews that describe a professor’s physical appearance, demeanor, clothing style, or resemblance, and links them to the difficulty and quality ratings of the professor. For our project, we can implement taggers similar to the article’s application of chunk tagger and document classifier to unlabeled data, determine each tagger’s precision, accuracy, etc, and further reduce the error by discarding the data they disagree with.
    </p><br>


* [_Sentiment Classification on Polarity Reviews: An Empirical Study Using Rating-based Features_](https://www.aclweb.org/anthology/W14-2621.pdf)
    <p>
    The study with rating-based features seeks to investigate the relationship between the actual ratings and the sentiment classification performance, which is pretty much similar to what we plan to do. The article considers the rating associated to each review as a feature named RbF for learning classification model, in which the rating-based feature RbF’s value of each review in training and test sets is estimated based on a regression model learned from an external independent dataset of reviews along with their actual associated scores. In addition, it takes into account bigrams and trigrams since a combination of unigram, bigram and trigram features (N-grams) could outperform a baseline performance based on unigram features—-something we may be able to apply.
    </p><br>

## Collaboration Plan
* Designing Phase
    * Search for and analyze relevant papers – Tony Li
    * Search for and analyze relevant datasets – completed by all three group members collectively
    * Design the sentiment analysis model – completed by all three group members collectively
    <br>
* Data Retrieval & Processing
    * Retrieve data from RateMyProfessors.com - Qian Chen
    * Process data: data cleaning and transformation – Xinyu Xie
    <br>
* Model Implementation: 
  * develop and train the model – to be completed by all three group members collectively
    <br><br>
* Evaluation
    * Label the sentiment weights of random RMP comments – Tony Li
    * Label words as negative, neutral, or positive based on context – Qian Chen
    * Measure the accuracy, precision, recall rate, and F-measure of the system output – Xinyu Xie