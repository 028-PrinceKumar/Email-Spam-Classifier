# 📧 Spam Mail Classifier

A Machine Learning-based **Spam Mail Classifier** that automatically classifies emails/messages as **Spam** or **Ham (Not Spam)** using Natural Language Processing (NLP) and machine learning techniques.

The project performs text preprocessing, feature extraction, model training, and prediction through a simple application interface.

---
## 🚀 Live Demo

Try the **Email Spam Classifier** here:

👉 **Live Demo:** https://email-spam-classifiergit-g7wxd8bcjfebyjkukuizaq.streamlit.app/

Enter an email message and the application will predict whether it is **Spam** or **Not Spam**.

##  Project Overview

Spam emails are unwanted messages that may contain advertisements, scams, phishing links, or other malicious content.

This project uses **Natural Language Processing (NLP)** to analyze the content of an email and predict whether it is:

*  **Spam** — Unwanted or potentially harmful email
*  **Ham** — Legitimate/non-spam email

The trained model achieved:

| Metric        |           Score |
| ------------- | --------------: |
| **Accuracy**  |       **97.8%** |
| **Precision** | **1.00 (100%)** |

> **Note:** These results are based on the test/evaluation split used during development. Performance can vary on unseen real-world emails.

---

##  Features

*  Spam/Ham email classification
*  Text preprocessing using NLP
* Removal of unnecessary characters and tokens
*  Lowercase conversion
*  Tokenization
*  Removal of stopwords
*  Stemming
*  TF-IDF feature extraction
*  Machine Learning classification
*  Model evaluation using accuracy and precision
*  Streamlit web interface
*  Real-time prediction for user-provided email text

---

## 🛠️ Technologies Used

### Programming Language

* Python

### Libraries

* Pandas
* NumPy
* NLTK
* Scikit-learn
* Matplotlib
* Seaborn
* WordCloud
* Streamlit

### Tools

* Jupyter Notebook
* VS Code
* Git
* GitHub

---

## 🔄 Machine Learning Workflow

```text
                 Email Dataset
                      │
                      ▼
              Data Cleaning
                      │
                      ▼
             Text Preprocessing
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
     Tokenization            Stopword Removal
          │                       │
          └───────────┬───────────┘
                      ▼
                   Stemming
                      │
                      ▼
              TF-IDF Vectorization
                      │
                      ▼
              Machine Learning Model
                      │
                      ▼
                 Model Training
                      │
                      ▼
                 Model Testing
                      │
                      ▼
                Spam / Ham
                  Prediction
```

---

## 📂 Project Structure

```text
Spam-Mail-Classifier/
│
├── app.py                    # Streamlit application
├── model.ipynb     # Model development notebook
├── model.pkl                 # Trained ML model
├── vectorizer.pkl            # TF-IDF vectorizer
├── README.md                 # Project documentation
│
└── dataset/
    └── spam.csv              # Dataset
```
---

## 📊 Dataset

The dataset contains email/message text along with its corresponding classification label.

Example:

| Message                                  | Label     |
| ---------------------------------------- | -----     |
| "Congratulations! You won a free prize!" | Spam      |
| "Can we meet tomorrow at 10 AM?"         | Not Spam  |
| "Claim your free reward now!"            | Spam      |
| "Please send me the project report."     | Not Spam  |

The target classes are:

* `spam`
* `Not Spam`

---

##  Text Preprocessing

Raw email text cannot be directly given to most traditional machine learning models.

Therefore, the following preprocessing steps are applied:

### 1. Lowercase Conversion

```python
text = text.lower()
```

Converts all text to lowercase.

### 2. Tokenization

The text is divided into individual words/tokens.

```python
text = nltk.word_tokenize(text)
```

### 3. Removing Special Characters

Only alphanumeric tokens are retained.

```python
if i.isalnum():
    y.append(i)
```

### 4. Stopword Removal

Common words that provide little classification information are removed.

Examples:

```text
the
is
a
an
and
to
of
```

### 5. Stemming

Words are converted to their root-like form.

Example:

```text
playing → play
played  → play
plays   → play
```

---

## 🔢 Feature Extraction

Machine Learning models work with numerical features rather than raw text.

This project uses **TF-IDF (Term Frequency-Inverse Document Frequency)** to convert email text into numerical vectors.

```python
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf = TfidfVectorizer()
X = tfidf.fit_transform(text)
```

TF-IDF gives higher importance to words that are useful for distinguishing between spam and legitimate messages.

---

## 🤖 Model

The processed text is converted into TF-IDF vectors and passed to the trained machine learning classifier.

The final pipeline can be represented as:

```text
Email Text
    ↓
Text Preprocessing
    ↓
TF-IDF Vectorization
    ↓
ML Classifier
    ↓
Prediction
    ↓
Spam / Not Spam
```

---

##  Model Performance

The model was evaluated using a separate test dataset.

### Accuracy

**97.8%**

Accuracy represents the proportion of total predictions that were correct.

```text
Accuracy = Correct Predictions / Total Predictions
```

### Precision

**1.00 (100%)**

Precision measures how many emails predicted as spam were actually spam.

```text
Precision = True Positives / (True Positives + False Positives)
```

A precision of **1.00** means that, on the evaluated test set, the model did not produce false-positive spam predictions.

### Results

```text
Accuracy  : 97.8%
Precision : 100%
```

> Accuracy and precision alone do not provide a complete evaluation of a spam classifier. Recall, F1-score, and the confusion matrix can provide additional information about missed spam and overall classification performance.

---

##  Streamlit Web Application

The project includes a Streamlit interface where users can enter an email/message and receive a prediction.

Example:

```text
Enter your email/message:

"Congratulations! You have won a free iPhone.
Click here to claim your prize."

Prediction:

🚨 Spam
```

For a legitimate message:

```text
"Hey, please send me the assignment before tomorrow."

Prediction:

✅ Not Spam
```

---

## ▶️ How to Run the Project Locally

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

### 2. Navigate to the Project

```bash
cd Spam-Mail-Classifier
```

### 3. Create a Virtual Environment

```bash
python -m venv .venv
```

### 4. Activate the Environment

#### Windows

```bash
.venv\Scripts\activate
```

#### Linux / macOS

```bash
source .venv/bin/activate
```

### 5. Install Dependencies

```bash
pip install -r requirements.txt
```

### 6. Run the Streamlit Application

```bash
python -m streamlit run app.py
```

The application will open in your browser.

---

## 📦 Requirements

Example `requirements.txt`:

```text
pandas
numpy
scikit-learn
nltk
matplotlib
seaborn
wordcloud
streamlit
```

---

##  Example Predictions

### Spam

```text
Congratulations! You have won $1,000,000.
Click the link now to claim your prize!
```

**Prediction:**  Spam

### Ham

```text
Hi, please share the meeting details for tomorrow.
```

**Prediction:** Not Spam

---

## 🔮 Future Improvements

Possible improvements include:

* Improve recall and F1-score
* Test multiple ML algorithms
* Hyperparameter tuning
* Handle HTML emails
* Detect phishing URLs
* Add email header analysis
* Add probability/confidence scores
* Improve preprocessing for real-world emails
* Deploy the application publicly
* Add a larger and more diverse dataset
* Add support for multiple languages

---

## ⚠️ Limitations

Although the model performs well on the evaluation dataset, real-world email classification can be more challenging.

Potential issues include:

* New types of spam messages
* Obfuscated words
* HTML-based emails
* Images containing spam text
* Phishing URLs
* Very short messages
* Domain-specific terminology

Therefore, the reported metrics should not be interpreted as guaranteed performance on every real-world email.

---

## 📚 Concepts Learned

Through this project, the following concepts were practiced:

* Natural Language Processing
* Text preprocessing
* Tokenization
* Stopword removal
* Stemming
* TF-IDF
* Feature extraction
* Machine Learning classification
* Model evaluation
* Precision and accuracy
* Streamlit deployment
* Pickle/model serialization
* Git and GitHub

---

## 👨‍💻 Author

**Prince Gupta**

B.Tech CSE (Artificial Intelligence)

GitHub: https://github.com/028-PrinceKumar

LinkedIn: https://www.linkedin.com/in/prince-kumar-999794320/

---

## ⭐ Acknowledgement

This project was developed as a hands-on Machine Learning and NLP project to understand the complete workflow from **raw text data to a deployed ML application**.

If you found this project useful, consider giving the repository a ⭐ on GitHub.
