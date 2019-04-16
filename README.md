# Freedom of Information Requests in the Region of Waterloo
One of the Region of Waterloo initiatives is [Open Data] (https://rowopendata-rmw.opendata.arcgis.com/). With it, the Region strives to be open, transparent, and accountable to citizens. It shares its data for everyone to use and republish with few restrictions. The data is provided in machine-readable format.

Searching the Region's Open Data Portal, one can find the Freedom of Information Requests (FOIR) data set. This data set spans 18 years (1999-2016).

In this repository, you will find a jupyter notebook that does a thorough job at describing the FOIR set. Specially from the side of descriptive statistics, visualization, natural language processing (NLP), and topic modeling (LSA, LDA, LSI).

You will also find a [file](https://github.com/brodriguezmilla/foir/blob/master/foir_all_figures.pdf) that encompasses the figures and images produced in the notebook, a.k.a., all the neat results.

Towards the end of the notebook, we test and compare some machine learning (ML) models, including the use of pipelines and GridSearchCV, albeit we don't do a deep analysis. My collegue Scott Jones has already looked at this set and found it is too small to provide reliable ML results. He opted to adding the FOIR datasets from Toronto and nearby regions. https://towardsdatascience.com/text-classification-of-freedom-of-information-requests-part-i-8a75d1e7ea02

So let's find what this dataset holds as there is always value in data! And as a bonus, let's see if we have better "luck" using machine learning to predict the outcome of a request based on the previously made decisions.

## Overview of Notebook 

There is a lot of material in the notebook. It is better is we give you a short summary of what is included.

- Get to know the data
    * We look at the files, we merge them, and clean them if necessary.
    * We have five main columns: one is the request ID, three columns have categorical data, and one has the summary of the request itself (plain text).
    * Of those with categorical data, decision made, source (a.k.a., requester), and request type, can we somehow reduce the number of categories (spoiler alert: yes).
- Descriptive Analysis
    * There are about 11 types of decisions for six different types of sources.
        * How many requests per type of decision?
        * How are the decisions split based on the source? Are some sources more "lucky" than others? Spoiler alert: yes, though we don't know the reason.
        * How is each decision split among the sources? 
        * For the main types of decisions (All information disclosed, Information disclosed in part, No information disclosed), how are they split among the sources?
- Natural Language Processing (NLP) - Analyzing the summary of request
    * Before analyzing any text with NLP, one needs to go over some steps, which can vary depending on the goal:
        * Parse text, tokenize it, remove symbols, remove stopwords, remove punctuation, convert tokens to lowercase, remove short words, and lemmatize the tokens. We use both NLTK and spaCy.
    * n-grams. We take a look at the most frequent unigrams, bigrams, trigrams, and n-grams (4-5).
    * WordClouds. They are not only pretty, they are also useful. Why is a word/phrase so important!?
    * Let's take six of these frequent phrases and find if there is any correlation with the decision taken.
    * Summary of request statistics. With how much text are we working? How long are the requests before and after tokenization? (Spoiler alert: seven tokens is the median per request. Ouch!)
    * Part-of-Speech (POS) tagging of the requests. Nouns, verbs?
    * Topic Modeling
        * Here with do LSA and LDA Analysis using Bokeh, scikit-learn, and t-SNE.
        * We also try LDA Analysis using Gensim and pyLDAvis.
- Machine Learning (ML)
    * Here we compare the accuracies of eight classifiers, RandomForest, LinearSVC, MultinomialNB, LogisticRegression, SVC, KNeighbors, SGDC, and DecisionTree, using pipelines, GridSearchCV, confusion matrices, and classification reports.
    * We compare two vectorizers, Count vectorizer and tf-idf vectorizer.
    * Given that some of our decisions have less than 15 instances and that we also have an unbalanced case, we look at other ways to optimize this. For example, a) we keep decisions with over 15 instances, b) we merge our 11 type of decisions into three main bins (full, partial, or no info released), and c) we remove cases where no decision was made (withdrawn or abandoned, which we name it as the independent case).
    * And with all of this, our best score goes up to... 51%
