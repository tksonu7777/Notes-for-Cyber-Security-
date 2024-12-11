# Decision Trees Algorithm
![image](https://github.com/user-attachments/assets/c93b9c2b-dde6-45e9-9976-e526f4d79a76)



- In the shown Decision Tree, the outlook is the root node, humidity and windy are nodes, sunny, overcast, and rainy are the edges, and Yes’s and No’s are leaves or leaf nodes.
- At every level, we try to split our decision tree on that attribute which is giving the highest information gain or we can say that split on that attribute which is minimizing the entropy of the next level as compared to the current level.
- I have given the formula for Entropy. You will notice that this is something that we use while binary-cross-entropy loss function.
- And then there is the formula for Information Gain which is simply the Entropy of previous level-Current Entropy.





![image](https://github.com/user-attachments/assets/d7f0e416-3d2a-4762-8bb7-0a3be2362bc6)



- Due to high Variance, Decision Trees does not perform that much great and does not give high accuracy.
- Means different splits into training data could lead to very different splits.
- That’s where Random Forests come into play.
- Random Forests are the ensembles of Decision Trees using bootstrap samples of the training data. Bootstrap samples mean taking random rows and random columns from data with replacement. Usually, you would have seen that we just take random rows. But here we are also picking columns randomly.
- This is done to build different Decision Trees. Suppose there is a very strong feature in the dataset and every time while building various Decision Trees in Random Forests every DT will pick that feature as the root node and all the trees will be almost similar and will become somehow correlated. That’s why to remove this correlation, we pick columns/features randomly.
- In this way, we end up with different Decision Trees, and averaging them can now really reduce Variance.



![image](https://github.com/user-attachments/assets/6601b3aa-b748-4d10-bacc-9e7c7d09711a)


- We can train and make predictions from Decision Trees and Random Forests by simply importing them from the sklearn library.
- Decision Trees use the ID3 algorithm which uses the concept of Entropy and Information Gain. It uses the top-down greedy approach to build trees.
- Ther is one more CART algorithm which uses the Gini index to build trees.


__________
__________
__________
__________
__________
__________
__________
__________

[Ref](https://machinelearningprojects.net/decision-trees/)







