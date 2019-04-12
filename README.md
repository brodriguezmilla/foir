# Freedom of Information Requests in the Region of Waterloo
One of the Region of Waterloo initiatives is Open Data. With it, the Region strives to be open, transparent and accountable to citizens. It shares its data for everyone to use and republish with few restrictions. The data is provided in machine-readable format  (https://rowopendata-rmw.opendata.arcgis.com/).

Searching the Region's Open Data Portal, one can find the Freedom of Information Requests (FOIR) data set. This data set spans 18 years (1999 and 2016).

In this repository, you will find a jupyter notebook that does a thorough job at describing the FOIR set. Specially from the side of descriptive statistics, visualization, natural langauge processing (NLP), and topic modelling (LSA, LDA, LSI).

You will also find the file foir_all_figures.pdf that emcompases the figures and images produced in the notebook, a.k.a., all the neat results.

Towards the end we test and compare some machine learning (ML) models, including the use of pipelines and gridsearch, albeit we don't do a deep analysis. My collegue Scott Jones has already looked at this set and found it is too small to provide reliable ML results. He opted to adding the FOIR datasets from Toronto and nearby regions. https://towardsdatascience.com/text-classification-of-freedom-of-information-requests-part-i-8a75d1e7ea02

So let's find what this dataset holds as there is always value in data! And as a bonus, let's see if we have better "luck" using machine learning to predict the outcome of a request based on the previously made decisions.



