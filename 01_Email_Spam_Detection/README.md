# 📧 Email Spam Detection

A machine-learning project that classifies email messages as **Spam** or **Ham (Not Spam)** using **TF-IDF text features** and **Logistic Regression**.

> **Project 01** · AI/ML Projects Portfolio

## 📌 Project Overview

Email spam is a common problem that fills inboxes with unwanted or potentially harmful messages. This project builds a text-classification pipeline that learns patterns from labelled emails and predicts whether a new message is spam or legitimate.

The notebook downloads and processes the public SpamAssassin email corpus, prepares the text data, trains a classifier, and evaluates its predictions on a held-out test set.

## 🎯 Objectives

- Load and prepare a labelled email dataset.
- Convert email text into numerical features using TF-IDF.
- Train a Logistic Regression classifier.
- Evaluate performance using accuracy, precision, recall, F1-score, a classification report, and a confusion matrix.
- Demonstrate how to classify a new email and inspect the model's predicted class probabilities.

## 🧰 Technologies

- Python
- pandas and NumPy
- scikit-learn
- Matplotlib and Seaborn
- SpamAssassin public email corpus

## 🧠 Methodology

1. **Dataset acquisition:** Download and extract the public SpamAssassin corpus from the source configured in the notebook.
2. **Text preparation:** Read email files, clean the data, and remove duplicates where applicable.
3. **Label encoding:** Assign `0` to ham and `1` to spam.
4. **Train/test split:** Use an 80/20 stratified split with `random_state=42`.
5. **Feature extraction:** Use `TfidfVectorizer` with English stop words, a maximum of 50,000 features, and unigram/bigram features (`ngram_range=(1, 2)`).
6. **Model training:** Train `LogisticRegression` with `max_iter=1000` and `class_weight="balanced"`.
7. **Evaluation:** Review accuracy, precision, recall, F1-score, classification report, and confusion matrix.
8. **Prediction demo:** Use the fitted vectorizer and classifier to predict whether new email text is spam or ham.

## 📂 Repository Contents

```text
01_Email_Spam_Detection/
├── Email_Spam_Detection.ipynb   # Main notebook: data preparation, training, and evaluation
├── README.md                    # Project documentation
└── requirements.txt             # Python package dependencies
```

The dataset is downloaded by the notebook and is not included in this repository. The notebook may need internet access to obtain the data.

## ⚙️ Setup and Execution

### Option A — Run in Google Colab

1. Open `Email_Spam_Detection.ipynb` from this GitHub repository.
2. Choose **Open in Colab** if available, or upload the notebook to Google Colab.
3. Run the notebook cells in order.
4. Allow the dataset-download cell to finish before continuing.

### Option B — Run locally

Use Python 3.10 or newer where possible.

1. Clone or download this repository.
2. Open a terminal in the `01_Email_Spam_Detection` folder.
3. Install dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

4. Start Jupyter:

   ```bash
   jupyter notebook Email_Spam_Detection.ipynb
   ```

5. Run the cells from top to bottom. An internet connection is needed for dataset download.

> If the notebook uses a Colab-specific upload or display feature, adapt that cell when running outside Colab.

## 📊 Evaluation

The notebook reports the following metrics on the held-out test split:

- **Accuracy** — overall fraction of correct predictions.
- **Precision** — among messages predicted as spam, the fraction that are actually spam.
- **Recall** — among actual spam messages, the fraction detected by the model.
- **F1-score** — harmonic mean of precision and recall.
- **Confusion matrix** — counts of correct and incorrect ham/spam predictions.

Use the results printed by the notebook as the authoritative experiment results; performance can vary with data availability and library versions.

## 🔍 Understanding Predicted Probability

If the notebook displays a spam probability, it is the classifier's estimated probability for the input text—not a guarantee that the email is spam. Treat borderline scores carefully and do not use the model as the only safeguard against phishing or malicious email.

## ⚠️ Limitations

- Performance depends on the dataset and may not generalize to modern spam campaigns or every language.
- Email text alone may omit useful signals such as sender reputation, links, and attachments.
- Spam classification errors are possible; predictions should not be treated as a security guarantee.
- Dataset availability or source URLs may change over time.

## 🚀 Possible Improvements

- Compare Logistic Regression with Multinomial Naive Bayes and Linear SVM.
- Evaluate precision-recall trade-offs and tune the decision threshold.
- Add a reproducible model-saving/loading workflow.
- Test on a separate, newer email dataset.
- Add careful handling for HTML, URLs, and email headers.

## 📚 Dataset

This experiment uses the **SpamAssassin public email corpus**. The notebook contains the data acquisition steps. Follow the dataset source and any applicable terms or usage conditions shown there.

## 👤 Portfolio Note

This project demonstrates a classic supervised NLP workflow: text preprocessing → TF-IDF vectorization → classification → evaluation → prediction.

