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

### 4. Success Criteria

The success of the automated classification system will be measured using both technical performance metrics and practical outcomes:

#### Technical Metrics
1. **Accuracy**: Achieve at least **90% accuracy** on a held-out test set of labeled articles.
2. **F1-Score**: Attain a minimum **macro-averaged F1-score of 0.88** to ensure balanced performance across all categories.
3. **Per-Class Performance**: Ensure no category has an F1-score below **0.85** to prevent bias toward dominant classes.
4. **Processing Time**: Classify an article in **under 2 seconds** in the deployed system.

#### Practical/Business Metrics
1. **Reduction in Manual Categorization Time**: Decrease editorial classification workload by at least **50%** compared to the current manual process.
2. **Improved Consistency**: Maintain classification agreement of **90% or higher** with domain experts.
3. **Editor Satisfaction**: At least **80%** of editorial staff report improved efficiency and reduced workload during pilot testing.
4. **Scalability**: Handle **5x the current average submission volume** without performance loss.
