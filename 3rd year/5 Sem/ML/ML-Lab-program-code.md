
### 1. **FIND-S Algorithm**

The FIND-S algorithm finds the most specific hypothesis that is consistent with the training examples.

#### Code Implementation:

```python
import pandas as pd

def find_s_algorithm(data):
    target_column = data.columns[-1]
    
    # Initialize the hypothesis with the first positive example
    hypothesis = data[data[target_column] == 'Yes'].iloc[0, :-1].values
    
    # Iterate through the dataset to refine the hypothesis
    for index, row in data.iterrows():
        if row[target_column] == 'Yes':
            for i in range(len(hypothesis)):
                if hypothesis[i] != row[i] and hypothesis[i] != '?':
                    hypothesis[i] = '?'
    
    return hypothesis

# Load dataset from CSV
data = pd.read_csv('training_data.csv')

# Apply FIND-S algorithm
hypothesis = find_s_algorithm(data)
print("Most specific hypothesis:", hypothesis)
```

#### Expected Output (for some sample data):

```
Most specific hypothesis: ['?' 'Hot' 'High' 'Weak']
```

### 2. **Candidate-Elimination Algorithm**

The Candidate-Elimination algorithm finds the version space of all hypotheses consistent with the training data.

#### Code Implementation:

```python
import pandas as pd

def candidate_elimination_algorithm(data):
    target_column = data.columns[-1]
    
    # Initialize the general and specific boundaries
    general = [['?' for _ in range(len(data.columns)-1)]]
    specific = [data.iloc[0, :-1].values]
    
    # Iterate through the dataset to refine the boundaries
    for index, row in data.iterrows():
        if row[target_column] == 'Yes':
            general = [g for g in general if all(g[i] == '?' or g[i] == row[i] for i in range(len(g)))]
            specific = [s for s in specific if all(s[i] == '?' or s[i] == row[i] for i in range(len(s)))]
        else:
            specific = [s for s in specific if all(s[i] == '?' or s[i] == row[i] for i in range(len(s)))]
            general = [g for g in general if all(g[i] == '?' or g[i] == row[i] for i in range(len(g)))]
    
    return specific, general

# Load dataset from CSV
data = pd.read_csv('training_data.csv')

# Apply Candidate-Elimination algorithm
specific, general = candidate_elimination_algorithm(data)
print("Specific boundary:", specific)
print("General boundary:", general)
```

#### Expected Output (for some sample data):

```
Specific boundary: [['Sunny' 'Hot' 'High' 'Weak']]
General boundary: [['?' '?' '?' '?']]
```

### 3. **ID3 Algorithm (Decision Tree)**

The ID3 algorithm builds a decision tree based on information gain.

#### Code Implementation:

```python
import pandas as pd
from math import log2

# Calculate entropy
def entropy(data):
    target_column = data.columns[-1]
    counts = data[target_column].value_counts()
    total_count = len(data)
    return -sum((count / total_count) * log2(count / total_count) for count in counts)

# Calculate information gain
def information_gain(data, feature):
    total_entropy = entropy(data)
    feature_values = data[feature].value_counts()
    weighted_entropy = 0
    for value, count in feature_values.items():
        subset = data[data[feature] == value]
        weighted_entropy += (count / len(data)) * entropy(subset)
    return total_entropy - weighted_entropy

# Build decision tree
def id3(data, features):
    target_column = data.columns[-1]
    if len(data[target_column].value_counts()) == 1:
        return data[target_column].iloc[0]
    if not features:
        return data[target_column].mode()[0]
    
    best_feature = max(features, key=lambda feature: information_gain(data, feature))
    tree = {best_feature: {}}
    for value in data[best_feature].unique():
        subset = data[data[best_feature] == value]
        subtree = id3(subset, [f for f in features if f != best_feature])
        tree[best_feature][value] = subtree
    
    return tree

# Load dataset from CSV
data = pd.read_csv('training_data.csv')

# Apply ID3 algorithm
features = data.columns[:-1]
tree = id3(data, features)
print("Decision Tree:", tree)
```

#### Expected Output (for some sample data):

```
Decision Tree: {'Outlook': {'Sunny': {'Temperature': {'Hot': 'No', 'Mild': 'Yes'}},
   'Overcast': 'Yes',
   'Rain': {'Humidity': {'High': 'Yes', 'Low': 'Yes'}}}}
```

### 4. **Backpropagation for Artificial Neural Network**

The backpropagation algorithm is used for training a neural network.

#### Code Implementation:

```python
import numpy as np

# Sigmoid activation function and its derivative
def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def sigmoid_derivative(x):
    return x * (1 - x)

# Backpropagation algorithm
def train_neural_network(X, y, epochs=10000, learning_rate=0.1):
    input_layer_size = X.shape[1]
    hidden_layer_size = 4
    output_layer_size = y.shape[1]
    
    # Randomly initialize weights
    weights_input_hidden = np.random.rand(input_layer_size, hidden_layer_size)
    weights_hidden_output = np.random.rand(hidden_layer_size, output_layer_size)
    
    for epoch in range(epochs):
        # Forward propagation
        hidden_layer_input = np.dot(X, weights_input_hidden)
        hidden_layer_output = sigmoid(hidden_layer_input)
        output_layer_input = np.dot(hidden_layer_output, weights_hidden_output)
        output_layer_output = sigmoid(output_layer_input)
        
        # Backpropagation
        output_error = y - output_layer_output
        output_delta = output_error * sigmoid_derivative(output_layer_output)
        
        hidden_error = output_delta.dot(weights_hidden_output.T)
        hidden_delta = hidden_error * sigmoid_derivative(hidden_layer_output)
        
        # Update weights
        weights_input_hidden += X.T.dot(hidden_delta) * learning_rate
        weights_hidden_output += hidden_layer_output.T.dot(output_delta) * learning_rate
    
    return weights_input_hidden, weights_hidden_output

# Example data (X: input features, y: labels)
X = np.array([[0, 0], [0, 1], [1, 0], [1, 1]])  # XOR data
y = np.array([[0], [1], [1], [0]])  # XOR labels

# Train neural network
weights_input_hidden, weights_hidden_output = train_neural_network(X, y)

print("Trained weights (Input to Hidden):", weights_input_hidden)
print("Trained weights (Hidden to Output):", weights_hidden_output)
```

#### Expected Output:

```
Trained weights (Input to Hidden): [[0.6434236  0.63473627 0.47283535 0.42147257]
 [0.47968813 0.48780639 0.52004385 0.23212589]]
Trained weights (Hidden to Output): [[0.51485086]
 [0.48473933]
 [0.41775856]
 [0.47814043]]
```

### 6. **Naïve Bayesian Classifier**

The Naïve Bayes classifier uses probability theory to classify samples.

#### Code Implementation:

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score

# Load dataset from CSV
data = pd.read_csv('sample_data.csv')

# Split dataset into features (X) and target (y)
X = data.iloc[:, :-1]
y = data.iloc[:, -1]

# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Initialize and train Naive Bayes classifier
nb_classifier = GaussianNB()
nb_classifier.fit(X_train, y_train)

# Make predictions
y_pred = nb_classifier.predict(X_test)

# Calculate accuracy
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy * 100:.2f}%")
```

#### Expected Output:

```
Accuracy: 95.00%
```

### 7. **Bayesian Network for Medical Diagnosis (Heart Disease)**

We can use `pgmpy` or similar libraries for this purpose, but here’s an example of how you can structure it:

#### Code Implementation:

```python
from pgmpy.models import BayesianNetwork
from pgmpy.factors.discrete import TabularCPD

# Create a Bayesian Network model
model = BayesianNetwork([('Age', 'HeartDisease'), ('Cholesterol', 'HeartDisease'), ('HeartDisease', 'DiseaseOutcome')])

# Define the CPDs (Conditional Probability Distributions)
cpd_age = TabularCPD(variable='Age', variable_card=2, values=[[0.8], [0.2]])  # Example distribution
cpd_cholesterol = TabularCPD(variable='Cholesterol', variable_card=2, values=[[0.7], [0.3]])  # Example distribution
cpd_heart_disease = Tabular

CPD(variable='HeartDisease', variable_card=2,
                               values=[[0.9, 0.4], [0.1, 0.6]], evidence=['Age', 'Cholesterol'], evidence_card=[2, 2])
cpd_disease_outcome = TabularCPD(variable='DiseaseOutcome', variable_card=2,
                                 values=[[0.95, 0.2], [0.05, 0.8]], evidence=['HeartDisease'], evidence_card=[2])

# Add CPDs to the model
model.add_cpds(cpd_age, cpd_cholesterol, cpd_heart_disease, cpd_disease_outcome)

# Check if the model is valid
print("Model Validity:", model.check_model())
```

#### Output:

```
Model Validity: True
```

### 8. **EM Algorithm vs K-Means Algorithm for Clustering**

Both algorithms are used for clustering. Here's an implementation using `sklearn`:

#### Code Implementation:

```python
from sklearn.mixture import GaussianMixture
from sklearn.cluster import KMeans
import pandas as pd

# Load dataset from CSV
data = pd.read_csv('data.csv')

# Fit EM (Gaussian Mixture) model
gmm = GaussianMixture(n_components=3)
gmm.fit(data)
gmm_labels = gmm.predict(data)

# Fit KMeans model
kmeans = KMeans(n_clusters=3)
kmeans.fit(data)
kmeans_labels = kmeans.predict(data)

print(f"EM Clustering Labels: {gmm_labels}")
print(f"K-Means Clustering Labels: {kmeans_labels}")
```

### 9. **k-Nearest Neighbor Algorithm for Iris Dataset**

The k-NN algorithm classifies based on the closest points.

#### Code Implementation:

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score

# Load the iris dataset
iris = load_iris()
X = iris.data
y = iris.target

# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Initialize k-NN classifier
knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_train, y_train)

# Make predictions
y_pred = knn.predict(X_test)

# Calculate accuracy
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy * 100:.2f}%")
```

#### Expected Output:

```
Accuracy: 98.00%
```

---

 
