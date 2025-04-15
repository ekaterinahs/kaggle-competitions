# 👗 H&M Personalized Fashion Recommendations

This repository hosts the notebooks and scripts developed for the Kaggle competition ["H&M Personalized Fashion Recommendations"](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/overview). The aim is to create a recommendation system using previous transaction data, customer profiles, and product metadata. The competition challenges participants to generate tailored product suggestions to improve online shopping experiences.

***

## 📊 Data

For this challenge we are given the purchase history of customers across time, along with supporting metadata. The aim is to predict what articles each customer will purchase in the 7-day period immediately after the training data ends. Customers who did not make any purchase during that time are excluded from the scoring.

### 📁 Files
- images/ - a folder of images corresponding to each `article_id`; images are placed in subfolders starting with the first three digits of the `article_id`; note, not all `article_id` values have a corresponding image.
- articles.csv - detailed metadata for each `article_id` available for purchase.
- customers.csv - metadata for each `customer_id` in dataset.
- transactions_train.csv - the training data, consisting of the purchases each customer for each date, as well as additional information. Duplicate rows correspond to multiple purchases of the same item. The task is to predict the `article_id`s each customer will purchase during the 7-day period immediately after the training data period.

Download the competition dataset from [Kaggle](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data).

***

## 🥇 Evaluation

The recommendations are evaluated according to the Mean Average Precision @ 12 (MAP@12):

$$ MAP@12 = \frac{1}{U} \sum_{u=1}^{U} \frac{1}{min(m,12)}  \sum_{k=1}^{min(n,12)} P(k) \times rel(k) $$

where $U$ is the number of customers, $P(k)$ is the precision at cutoff $k$, $n$ is the number predictions per customer, $m$ is the number of ground truth values per customer, and $rel(k)$ is an indicator function equaling 1 if the item at rank $k$ is a relevant (correct) label, zero otherwise.
