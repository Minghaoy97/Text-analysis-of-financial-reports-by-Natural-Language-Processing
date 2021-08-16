# <div align='center' >SI630 Natural Language Processing Final Project </div><div align='center' > Text analysis of financial reports by Natural Language Processing </div>

> Author: Minghao Yang minghaoy@umich.edu     To see the blog post, click [here](https://minghaoy.medium.com/nlp-on-financial-reports-18805bd65fc3)

## Project Goal
The whole project is an experiment on performing NLP algorithms on financial reports, since traditionally analysts more focus on the structured data provided in the statements, and can only use their experience and knowledge to interpret what are contained in the unstructured text data in financial reports.

## Data Collection and process
The project focus on the technology sector of the stock market. I randomly choose 52 companies from this sector doing business in different areas including electrical equipment, computer peripherals, semiconductors, etc. From Factset database, I downloaded their 10-K reports, which is the annual financial report providing comprehensive overviews of a company’s business, in the recent 10 years, from 2011 to 2020. Since they are in the pdf files, with the aid of Python Tesseract, I transformed them into txt files. To sum up, there are more than 50,000 words within each document, and 420 fully transformed reports for model fitting.  I built my own corpus by the textual parts of 420 reports with the stock performance as the label, and the annotation work was completed manually.

## Data Exploration
After getting rid of all unrelated words and punctuations, I build a corpus for companies in the same industry. Then I used word clouds to visualize the data, and tried to find
the words with the largest frequencies. Moreover, since I’ve already labeled the reports, I plotted two word clouds. The first contains the words appearing in the reports that lead to a decrease stock performance, and the second is from the other class.
<p align="center">
  <img src="https://github.com/Minghaoy97/Text-analysis-of-financial-reports-by-Natural-Language-Processing/blob/main/images/wordcloud_drop.png" width="350" title="Word cloud for stocks with negative price move">
  <img src="./images/wordcloud_raise.png" width="350" alt="Word cloud for stocks with positive price move">
</p>

Furthermore, I used topic selection model LDA to further investigate the data. The main reason to use this model is to find if there are some unique topics for reports with good or bad stock performance. The following plot shows the topics for reports with bad stock performance.
<p align="center">
  <img src="./images/lda_drop.png" width="900" title="LDA on bad performance financial reports">
</p>

## Fitting Models
Firstly I retrained the GPT2 to do the sentimental classification better based on a huge pre-trained corpus and fine-tuned model. I managed to divide the report into small sentence and predict if each sentence is positive or negtive. Then I determined the class of the whole report by comparing between the total numbers of the positive sentenses and the negative sentenses. The GPT2 model worked here after I transformed sentences into ”sentence +(special char) + Postive/Negative” form, and train the model to generate the following word after the special char. 

<p align="center">
  <img src="./images/loss_gpt2.png" width="900" title="Loss curve for GPT2 model">
</p>

Then I tried Naive Bayesian model and Logistic Regression model to make simple classification. And compared between them to see they works and if the classification is effective. For naive bayesian model, the features are frequencies of each word, and in logistic regression model, I use onehot encoding method to
transform texts into vectors. And the training set and the test set are all set as 9:1 for above models.

<p align="center">
  <img src="./images/loss_logit.png" width="900" title="Negative Loss curve for logit model">
</p>

# Evaluating

I calculated the F-1 scores to compare the effectiveness of different models

|                             | Baseline accounting analysis | GPT-2 model | Naive Bayesian | Logistic Regression |
| F-1 Scores of the test sets |  0.94  |  0.63  |  0.78  |  0.97  | 

# Conclusion
