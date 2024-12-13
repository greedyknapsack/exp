Sure, here is the updated content with LaTeX formatting for mathematical expressions:

### **Support Vector Machine (SVM)**

---

### **Definition**  
Support Vector Machine (SVM) is a supervised machine learning algorithm used for **classification** and **regression** tasks. It is effective for solving linear and non-linear problems by transforming data into higher dimensions where it is linearly separable.

---

### **Key Concepts in SVM**

| **Concept**               | **Description**                                                                                   |
|----------------------------|---------------------------------------------------------------------------------------------------|
| **Hyperplane**            | A decision boundary that separates different classes in the feature space.                       |
| **Support Vectors**       | Data points closest to the hyperplane, influencing its position and orientation.                  |
| **Margin**                | The distance between the hyperplane and the nearest data point of each class.                     |
| **Kernel Function**       | A function that maps data to a higher-dimensional space, enabling linear separation in complex cases. |

---

### **Key Features**

| **Feature**                  | **Description**                                                                                          |
|-------------------------------|----------------------------------------------------------------------------------------------------------|
| **Robustness to Outliers**   | Uses only support vectors, minimizing the influence of other data points.                               |
| **Effective in High Dimensions** | Performs well even when the number of dimensions is larger than the number of samples.                |
| **Versatility**              | Can be used for linear and non-linear problems using kernel tricks.                                      |

---

### **Types of SVM**
1. **Linear SVM**:  
   Used when the data is linearly separable.  
   Example: \( \mathbf{w}^T \mathbf{x} + b = 0 \) defines the hyperplane.

2. **Non-Linear SVM**:  
   Applies kernel functions to handle non-linearly separable data by transforming it into a higher-dimensional space.

---

### **Mathematical Formulation**

#### Objective Function (Hard Margin SVM):  
$$
\text{Minimize: } \frac{1}{2} \|\mathbf{w}\|^2
$$  
Subject to:  
$$
y_i (\mathbf{w}^T \mathbf{x}_i + b) \geq 1 \quad \forall i
$$

#### Soft Margin SVM (with Slack Variables \( \xi_i \)):  
Allows misclassification by introducing a penalty.  
$$
\text{Minimize: } \frac{1}{2} \|\mathbf{w}\|^2 + C \sum_{i=1}^{n} \xi_i
$$  
Subject to:  
$$
y_i (\mathbf{w}^T \mathbf{x}_i + b) \geq 1 - \xi_i, \quad \xi_i \geq 0
$$  

Where:
- \( \mathbf{w} \): Weight vector.  
- \( C \): Regularization parameter balancing margin width and classification error.

---

### **Kernel Functions**
| **Kernel**         | **Formula**                                                                                     | **Use Case**                                                                 |
|---------------------|-----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| **Linear**         | \( K(x, y) = x^T y \)                                                                          | For linearly separable data.                                               |
| **Polynomial**     | \( K(x, y) = (\gamma x^T y + r)^d \), \( \gamma > 0 \)                                         | For complex boundaries (non-linear problems).                              |
| **Radial Basis Function (RBF)** | \( K(x, y) = \exp(-\gamma \|x-y\|^2) \), \( \gamma > 0 \)                            | For non-linear problems with unknown patterns.                             |
| **Sigmoid**        | \( K(x, y) = \tanh(\gamma x^T y + r) \)                                                        | Used in neural networks (similarity measure).                              |

---

### **SVM Classification**

1. **Input**: Training dataset \( (x_i, y_i) \), where \( y_i \in \{-1, 1\} \).  
2. **Hyperplane Calculation**: Maximizes margin between classes.  
3. **Decision Function**:
   $$
   f(x) = \text{sign}(\mathbf{w}^T \mathbf{x} + b)
   $$

---

### **SVM Regression (SVR)**
- Predicts continuous values.  
- Uses a margin of tolerance \( \epsilon \) around the actual value.  
- Objective: Minimize the error outside this margin.

---

### **Advantages**
1. **Effective in High-Dimensional Spaces**: Works well with complex datasets.  
2. **Kernel Trick**: Handles non-linear relationships efficiently.  
3. **Robustness**: Less prone to overfitting due to regularization.

### **Disadvantages**
1. **Computationally Expensive**: High training time for large datasets.  
2. **Requires Parameter Tuning**: Selection of kernel and \( C \) values is critical.  
3. **Sensitive to Noise**: Outliers can significantly affect results.

---

### **Applications of SVM**
| **Application**          | **Use Case**                                                                                       |
|---------------------------|---------------------------------------------------------------------------------------------------|
| **Text Classification**  | Spam detection, sentiment analysis.                                                              |
| **Image Recognition**    | Facial recognition, object detection.                                                            |
| **Bioinformatics**       | Classifying proteins, genes, and diseases.                                                       |
| **Stock Market Analysis**| Predicting trends based on historical data.                                                      |
| **Anomaly Detection**    | Identifying fraud or unusual patterns in datasets.                                               |

---

### **SVM Implementation (Python)**

#### **1. Linear SVM**
```python
from sklearn.svm import SVC
from sklearn.datasets import make_classification
from sklearn.model_selection import train_test_split

# Generate sample data
X, y = make_classification(n_samples=100, n_features=2, n_classes=2, random_state=42)

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Train an SVM
svm = SVC(kernel='linear', C=1.0)
svm.fit(X_train, y_train)

# Predictions
y_pred = svm.predict(X_test)
```

#### **2. Non-Linear SVM (RBF Kernel)**
```python
svm = SVC(kernel='rbf', gamma=0.5, C=1.0)
svm.fit(X_train, y_train)

y_pred = svm.predict(X_test)
```

---

### **Tuning Parameters**

| **Parameter**        | **Description**                                                                                   |
|-----------------------|---------------------------------------------------------------------------------------------------|
| **C (Regularization)**| Controls trade-off between achieving a large margin and minimizing classification error.          |
| **Gamma (\( \gamma \))**| Defines the influence of a single training example (used in RBF and polynomial kernels).          |
| **Kernel**            | Specifies the type of kernel function (linear, polynomial, RBF, etc.).                           |

---

### **Performance Metrics**
| **Metric**            | **Description**                                                                                   |
|------------------------|---------------------------------------------------------------------------------------------------|
| **Accuracy**          | Proportion of correct predictions.                                                                |
| **Precision**         | Correctly predicted positives out of all predicted positives.                                      |
| **Recall**            | Correctly predicted positives out of all actual positives.                                         |
| **F1-Score**          | Harmonic mean of precision and recall.                                                            |

---

### **SVM Summary Table**
| **Aspect**           | **Details**                                                                                       |
|-----------------------|---------------------------------------------------------------------------------------------------|
| **Learning Type**    | Supervised.                                                                                       |
| **Goal**             | Maximize margin between classes (classification) or predict values with a margin of error (regression). |
| **Kernel Trick**     | Enables linear separability in higher-dimensional spaces.                                          |
| **Advantages**       | Effective in high dimensions, versatile with kernels.                                             |
| **Disadvantages**    | Computationally expensive, sensitive to parameter selection.                                       |
| **Key Parameters**   | Kernel, \( C \), \( \gamma \).                                                                     |
