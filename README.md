# <div align='center' >SI630 Natural Language Processing Final Project </div><div align='center' > Text analysis of financial reports by Natural Language Processing </div>

> Author: Minghao Yang minghaoy@umich.edu     To see the blog post, click [here](https://minghaoy.medium.com/nlp-on-financial-reports-18805bd65fc3)

## Project Goal
The whole project is an experiment on performing NLP algorithms on financial reports, since traditionally analysts more focus on the structured data provided in the statements, and can only use their experience and knowledge to interpret what are contained in the unstructured text data in financial reports.

## Data Collection and process
The project focus on the technology sector of the stock market. I randomly choose 52 companies from this sector doing business in different areas including electrical equipment, computer peripherals, semiconductors, etc. From Factset database, I downloaded their 10-K reports, which is the annual financial report providing comprehensive overviews of a company’s business, in the recent 10 years, from 2011 to 2020. Since they are in the pdf files, with the aid of Python Tesseract, I transformed them into txt files. To sum up, there are more than 50,000 words within each document, and 420 fully transformed reports for model fitting.  I built my own corpus by the textual parts of 420 reports with the stock performance as the label, and the annotation work was completed manually.

## Data Exploration
After getting rid of all unrelated words and punctuations, I build a corpus for companies in the same industry. Then I used word clouds to visualize the data, and tried to find
the words with the largest frequencies. Moreover, since I’ve already labeled the reports, I plotted two word clouds. The first contains the words appearing in the reports that lead to a decrease stock performance, and the second is from the other class.
![Drop wordcloud]https://github.com/Minghaoy97/Text-analysis-of-financial-reports-by-Natural-Language-Processing/blob/main/images/wordcloud_drop.png
