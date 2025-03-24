# Machine Learning

## 1. **Fundamentals of ML**
### Key Points:
- **Definition**: ML enables systems to learn patterns from data *without explicit programming*.
- **Types of ML**:
  - **Supervised**: Labeled data (e.g., regression, classification).
  - **Unsupervised**: Unlabeled data (e.g., clustering, dimensionality reduction).
  - **Reinforcement**: Learn via rewards/punishments (e.g., game-playing AI).
- **Semi-supervised/Self-supervised**: Mix of labeled and unlabeled data.

### Action Items:
- Memorize the ML workflow: **Data → Model → Training → Evaluation → Deployment**.

---

## 2. **Data is King**
### Key Points:
- **Feature Engineering**: Transform raw data into meaningful inputs (e.g., scaling, one-hot encoding).
- **Train/Test Split**: Always reserve 20–30% of data for testing.
- **Data Quality**: Garbage in = garbage out. Handle missing values, outliers, and imbalances.

### Action Items:
- Use libraries like `pandas` (Python) for data cleaning.
- Practice splitting data with `train_test_split` (scikit-learn).

---

## 3. **Core Algorithms**
### Key Points:
- **Supervised**:
  - **Linear Regression**: Predict continuous values.
  - **Logistic Regression**: Binary classification.
  - **Decision Trees/Random Forest**: Interpretable, handles non-linear data.
  - **SVMs**: Effective for high-dimensional data.
- **Unsupervised**:
  - **K-Means Clustering**: Group similar data points.
  - **PCA**: Reduce dimensionality while preserving variance.
- **Neural Networks**: Basis for deep learning (e.g., CNNs, RNNs).

### Action Items:
- Implement at least 1 algorithm from each category using scikit-learn.

---

## 4. **Model Evaluation**
### Key Points:
- **Metrics**:
  - **Classification**: Accuracy, Precision, Recall, F1-Score, ROC-AUC.
  - **Regression**: MSE, RMSE, R².
- **Cross-Validation**: Use k-fold (e.g., 5-fold) to avoid overfitting.
- **Confusion Matrix**: Visualize true/false positives/negatives.

### Action Items:
- Practice evaluating models with `classification_report` and `confusion_matrix` (scikit-learn).

---

## 5. **Bias-Variance Tradeoff**
### Key Points:
- **Bias**: Underfitting (oversimplified model).
- **Variance**: Overfitting (model memorizes noise in training data).
- **Balance**: Regularization (L1/L2), dropout (neural nets), and ensemble methods.

### Action Items:
- Use `GridSearchCV` (scikit-learn) to tune hyperparameters like regularization strength.

---

## 6. **Feature Selection & Engineering**
### Key Points:
- **Relevance**: Remove redundant features (e.g., correlation analysis).
- **Techniques**:
  - **Wrapper Methods**: Recursive Feature Elimination (RFE).
  - **Embedded Methods**: Lasso regression.
  - **Domain Knowledge**: Create new features (e.g., day/month from timestamp).

### Action Items:
- Apply feature selection to a dataset using `SelectKBest` (scikit-learn).

---

## 7. **Neural Networks Basics**
### Key Points:
- **Layers**: Input → Hidden → Output.
- **Activation Functions**: ReLU, Sigmoid, Softmax.
- **Loss Functions**: MSE (regression), Cross-Entropy (classification).
- **Optimizers**: SGD, Adam.

### Action Items:
- Build a simple neural network with `TensorFlow` or `PyTorch`.

---

## 8. **Overfitting Solutions**
### Key Points:
- **Regularization**: Add penalties (L1/L2) to loss function.
- **Dropout**: Randomly disable neurons during training.
- **Early Stopping**: Halt training when validation performance plateaus.
- **Data Augmentation**: Artificially expand dataset (e.g., image rotations).

### Action Items:
- Implement dropout in a neural network using `keras.layers.Dropout`.

---

## 9. **Tools & Frameworks**
### Key Points:
- **Python**: Primary language for ML (libraries: NumPy, pandas, matplotlib).
- **scikit-learn**: For classical ML algorithms.
- **TensorFlow/PyTorch**: For deep learning.
- **Jupyter Notebooks**: Interactive prototyping.

### Action Items:
- Install Anaconda and run a "Hello World" ML script.

---

## 10. **Practical Workflow**
### Key Points:
- **Start Simple**: Begin with linear regression, not deep learning.
- **Iterate**: Experiment → Evaluate → Improve.
- **Deploy**: Use tools like Flask, FastAPI, or cloud platforms (AWS SageMaker).

### Action Items:
- Complete an end-to-end project (e.g., predict house prices on Kaggle).

---

## 11. **Ethics & Limitations**
### Key Points:
- **Bias in Data**: Models can amplify societal biases (e.g., gender/racial bias).
- **Explainability**: "Black-box" models (e.g., deep learning) lack transparency.
- **Privacy**: Ensure compliance with GDPR/CCPA when handling user data.

### Action Items:
- Audit datasets for bias using tools like IBM’s AI Fairness 360.

---

## 12. **Future Trends**
### Key Points:
- **AutoML**: Automate model selection/hyperparameter tuning (e.g., Google AutoML).
- **Transfer Learning**: Reuse pre-trained models (e.g., BERT, GPT-3).
- **Edge ML**: Deploy models on devices (e.g., smartphones, IoT).

### Action Items:
- Experiment with Hugging Face’s pre-trained NLP models.

---
