# K-Nearest Neighbors (KNN) Algorithm – 2024
![image](https://github.com/user-attachments/assets/9737be91-89f7-4d86-aad4-01804f843765)



- In the first diagram, I have plotted dog and horse classes based on weight and height.
 Given this plot, if asked to predict the class of + points, would you be able to classify them correctly? And if yes, what approach will you use to do so?
- The most naive approach to do so will be to see some of the nearest points and make a prediction based on that.
- This is called the K-Nearest Neighbors algorithm. Based on the K-nearest data points, we predict the class of the data point under test.
- In the training phase, KNN does not make any type of discriminator function or anything else. It just stores all the data points.
- In the testing phase, it just calculates the euclidean distance of all points from the test point and sorts them in increasing order. Then it takes the first k-nearest points and sees which class is the majority class. And this majority class is allotted to the test point.



![image](https://github.com/user-attachments/assets/61670457-4228-4fa4-9fd7-84761cedddd8)


- This diagram shows how the KNN classification algorithm works.
- For different k’s, it will give different answers.
- Pros:
- Very Simple.
- Training is trivial.
- Easy to add more data.
- Works with any no. of classes.
- Very few parameters (k and distance metric).
- Cons:
- Worse for large datasets.
- Not good for high-dimensional data.
- Categorical features don’t work well.





![image](https://github.com/user-attachments/assets/38194714-b096-43dc-a78a-2c1446ab973c)


- One thing to note while using KNN is that it is a distance-based algorithm and it expects everything to be on the same scale.
- That’s why we need to use Standard Scaler or Min-Max Normalization in this case.

















___
____
___
____
____
[refrance](https://machinelearningprojects.net/k-nearest-neighbors/)


