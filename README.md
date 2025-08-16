# jabs_article_classification
Group Project for CSC4792 - Classifying JABS journal articles using title and abstract.

## **1. Problem Statement**  
The University of Zambia *Journal of Agriculture and Biomedical Sciences* **(UNZA-JABS)** is a quarterly Journal open to journal article publication in the fields of **agriculture, medicine, veterinary medicine and biomedical sciences as well as such allied life sciences**. The Journal welcomes manuscripts submissions that meet the general criteria of significance and scientific excellence. Currently, the classification of submitted articles into these categories is performed manually by editors or reviewers, which introduces several challenges:  

- **Time-Consuming Process**: Manual categorization requires significant editorial effort, delaying publication timelines.  
- **Subjectivity and Human Error**: Different reviewers may classify the same article differently based on their expertise, leading to inconsistencies.  
- **Scalability Issues**: As the number of submissions grows, manual classification becomes unsustainable.  

To address these challenges, we propose developing an **automated machine learning (ML)-based classification system** that uses **article titles and abstracts** to predict the correct discipline. This system will improve efficiency, reduce bias, and enhance the journal’s ability to organize and index articles effectively.  

---
## **2. Business Objectives**
The primary goal is to automate and optimize the classification process while ensuring high accuracy. Success from a real-world perspective would mean:

**Key Objectives:**
- **Reduce Editorial Workload** - Minimize the time and effort required for manual categorization.
- **Improve Classification Accuracy** - Achieve higher consistency than human-based classification.
- **Enhance Article Discoverability** - Ensure researchers can easily find articles in their field.
- **Support Scalability** - Handle increasing submission volumes without additional staffing.

**Stakeholder Benefits:**
- **Editors & Reviewers:** Spend less time on administrative tasks and more on content evaluation.
- **Researchers & Readers**: Quickly locate relevant articles due to accurate tagging.
- **Journal Management**: Improve operational efficiency and reduce publication delays
## *3. Data Mining Goals*  
To achieve the business objectives, we will implement a *text classification model* using Natural Language Processing (NLP) and supervised learning. The key steps include:  

### *Step 1: Data Collection & Preprocessing*  
- *Dataset Acquisition*: Gather labeled journal articles (title + abstract + discipline) from past issues.  
- *Text Cleaning*:  
  - Remove special characters, numbers, and irrelevant formatting.  
  - Apply tokenization, stopword removal, and lemmatization (e.g., using NLTK or spaCy).  
- *Feature Extraction*:  
  - Bag-of-Words (BoW) / TF-IDF for traditional ML models.  
  - Word embeddings (Word2Vec, GloVe) or transformer-based embeddings (BERT, SciBERT) for deep learning models.  

### *Step 2: Model Development*  
We will experiment with multiple classification algorithms:  
- *Traditional ML Models*:  
  - Naïve Bayes (baseline for text classification)  
  - Support Vector Machines (SVM)  
  - Random Forest / XGBoost (with TF-IDF features)  
- *Deep Learning Models*:  
  - LSTM / BiLSTM for sequential text analysis  
  - Transformer-based models (e.g., BERT, DistilBERT for higher accuracy)  

### *Step 3: Model Evaluation & Optimization*  
- *Performance Metrics*:  
  - Accuracy, Precision, Recall, F1-Score (per class and macro-average).  
  - Confusion matrix to analyze misclassifications.  
- *Hyperparameter Tuning*:  
  - GridSearchCV / RandomSearch for traditional models.  
  - Learning rate scheduling for deep learning models.  
- *Explainability*:  
  - SHAP values / LIME to interpret model decisions.  
  - Key term extraction (e.g., most influential words for each category).  

### *Step 4: Deployment & Integration*  
- *API Development*: Wrap the best model in a REST API (Flask/FastAPI).  
- *Journal Submission System Integration*:  
  - Automatically suggest categories during manuscript submission.  
  - Allow editors to override predictions if needed.

4. **Success Criteria**
For the model to be considered successful, it must meet the following benchmarks:

**Performance Metrics**:
Accuracy ≥ 85% (to ensure reliable automated classification).
Precision & Recall ≥ 80% per class (to avoid bias toward any discipline).
Balanced F1-Score (to ensure fairness across categories).

**Practical Deployment Requirements**:
Low Latency - Predictions should take <1 second to avoid slowing submissions.
Scalability - Model should handle thousands of submissions without performance drops.
Explainability - Editors should understand why an article was classified a certain way.

## **5. Potential Challenges & Mitigation Strategies**

| **Challenge** | **Mitigation Strategy** |
|---|---|
| **Class Imbalance** | Use oversampling (e.g., SMOTE), undersampling, or apply class weights during training. |
| **Ambiguous / Interdisciplinary Articles** | Introduce a **"Hybrid / Interdisciplinary"** category and consider multi-label classification. |
| **Domain-Specific Terminology** | Use domain-tuned embeddings (e.g., **SciBERT**, **BioBERT**) instead of generic embeddings. |
| **Model Interpretability** | Apply **SHAP** or **LIME** to provide transparent, editor-friendly explanations of predictions. |


## **6. Future Enhancements**
- **Multi-Label Classification** — Support articles that legitimately belong to multiple fields.  
- **Active Learning** — Allow editors to correct misclassifications and feed corrections back into the training loop to iteratively improve model performance.  
- **Trend Analysis** — Use classification outputs over time to track and visualize research trends in UNZA-JABS.


## **Conclusion**

This project will produce an automated, accurate, and scalable classification system for the Journal of Agricultural and Biomedical Sciences. By reducing manual effort and improving consistency, the system will speed up the publication process and enhance discoverability of relevant research. Leveraging modern NLP and ML techniques ensures the solution is robust, explainable, and suitable for real-world deployment.

**Next Steps**:

Collect and preprocess a labeled dataset.
Train and compare multiple models.
Deploy the best-performing model into the journal’s workflow.
**Expected Impact**: Faster publication process, better-organized archives, and improved user experience for researchers!

