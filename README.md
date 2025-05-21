
# 📚 Arabic Text Classification

This project aims to develop and evaluate a supervised text classification system for Arabic language documents. Three classical algorithms were tested: **Naive Bayes**, **SVM (Support Vector Machine)**, and **Logistic Regression**. The project explores the impact of feature selection (different values of *k*) on model performance.

---

## 🧠 Methodology

### 1. Data Preprocessing
- Cleaning of texts (removal of symbols, digits, punctuation)
- Removal of Arabic-specific stop words
- Tokenization (splitting into words)
- **Stemming/lemmatization was not applied** to preserve the original rich forms of the Arabic lexicon

### 2. Vector Representation
- TF-IDF was used to represent the documents as vectors
- Feature selection was performed using the chi-squared (χ²) test with different values of *k*: 50, 200, 400, and *all* (no reduction)

### 3. Classification
The following models were applied:
- Naive Bayes  
- SVM (with linear kernel)  
- Logistic Regression  

Each model was evaluated using 10-fold cross-validation for all *k* values.

---

## 📊 Experimental Results

### 🎯 Overall Accuracy for Each Model

| Model               | k=50   | k=200  | k=400  | k=all  |
|---------------------|--------|--------|--------|--------|
| Naive Bayes         | 0.8429 | 0.9178 | 0.9297 | 0.9428 |
| SVM                 | 0.9106 | 0.9454 | 0.9671 | 0.9822 |
| Logistic Regression | 0.8665 | 0.9198 | 0.9467 | 0.9816 |

✅ **SVM achieved the best overall performance with k=all**, closely followed by Logistic Regression.

---

## 📈 Model Performance Details

### Naive Bayes (k=all, accuracy = 0.9428)
- Macro average: **precision = 0.96**, **recall = 0.95**, **F1-score = 0.95**
- Notable weaknesses in some classes, especially **label 2** with a recall of **0.66**
- Likely affected by violated conditional independence assumption due to semantic overlap

### SVM (k=all, accuracy = 0.9822)
- Macro average: **precision = 0.98**, **recall = 0.98**, **F1-score = 0.98**
- Best-performing model overall
- Moderate challenges with lexically similar classes (labels 2, 3, 8)

### Logistic Regression (k=all, accuracy = 0.9816)
- Macro average: **precision = 0.98**, **recall = 0.98**, **F1-score = 0.98**
- Excellent performance, comparable to SVM
- Similar confusion patterns to SVM in lexically ambiguous classes

---

## 🧐 Critical Analysis

### 🔍 Feature Selection
- Models perform best with **k=all**
- The TF-IDF representation acts as a noise filter, making chi-squared selection less beneficial
- In Arabic, **rich morphology and lexical variability** make dimensionality reduction sometimes counterproductive

### 📌 Class-wise Behavior
- Models like Naive Bayes show strong sensitivity to inter-class confusion
- Lexically similar classes (e.g., family, religion, society) are often poorly separated, even with high-performing models
- **Illustrated in Figure 3.4**: class overlap in vector space

### ⚙️ Robustness and Scalability
- **SVM scales well** with increasing feature size
- **Naive Bayes reaches its limits** quickly in high dimensions
- **Logistic Regression** shows a good balance between accuracy and stability

---

## 📌 Conclusion

The results of this project highlight:
- The effectiveness of **SVM and Logistic Regression** for Arabic text classification
- The importance of a rich representation tailored to the specifics of the language
- The **limitations of classical feature selection techniques** for Arabic text
- The promising potential of exploring **contextual representations** (e.g., Word Embeddings, BERT) for future improvements

