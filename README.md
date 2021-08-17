# DESIGNING A RECOMMENDATION SYSTEM BASED ON PURCHASE DATA
### Description
This project was done as a part of Hackathon 2 conducted by Univ.ai.
I build a recommendation system based on purchase data of users being shared in the form of a dataset. I used Baseline algorithm and Collaborative filtering based 
methods like Matrix Factorization, KNN to build a Recommendation system. I also tried hybrid Recommender systems. Given Purchase Data does not contain explicit liking of a certain product associated with a user so I had used the frequency(number of times a user brought from a product category) as a representative of the liking. 

### Dataset
Dataset is provided by the Hackathon organiser Univ.ai. Dataset contains past - purchase data of users.
The Datasets can be downloaded from https://hack.univ.ai/problem/data

Training Data:
This file contains the detailed purchasing history for every user. It has order value and the category of the product.

Training Data Target:
This file contains data for some users about the category of items they bought in future.

Test Data:
This file contains the detailed purchasing history for some users. It has the order value and the category of the product. You have to predict the top 3 categories that the users with these user_ids will purchase from in the future.

### Goal of the Project / Problem statement of the Hackathon
For each user, predict the top 3 probable product categories that they may purchase from, in the future.

### Precision for different approaches tried
| Algorithm used   | Precision on Validation Data|
| ---      | ---       |
| Baseline | 0.534        |
| Top 3 frequently bought item categories | 0.534       |
| ItemBased KNN | 0.27        |
| Matrix factorization - SVD with ALS | 0.3|
| Matrix factorization - SVD with SGD | 0.3|
| Hybrid of Matrix factorization and Top 3 frequently bought item categories | 0.534|
| Hybrid of Matrix factorization and Baseline | 0.534|

### Conclusion
The Best Precision of 0.534 is obtained from the naive Baseline approach or Top 3 frequently bought item categories approach or the Hybrid Recommendation system. <br/>
Initially the Matrix Factorization algorithm produced less precision, due to existence of some users who have brought very few items in total - which would not be a good representative of their likings. Later I removed those users who have brought very few items from the training data, and then fitted SVD over this data. I got the Recommendations as follows:
if user bought  more than 5 items:
  used SVD to get recommendations
else:
  used Top 3 frequently bought item categories algorithm to get recommendations

And this model gives good accuracy as I have taken users who have brought very few items in total also into account. 


