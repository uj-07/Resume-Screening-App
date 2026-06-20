# 📄 Resume Screening App

An intelligent resume screening web application built with **Python**, **Streamlit**, and **Machine Learning** that automatically classifies uploaded resumes into job categories — helping recruiters and HR teams filter candidates faster.

---

## 🚀 Features

- **Multi-format Support** — Upload resumes as PDF, DOCX, or TXT files
- **AI-Powered Classification** — Uses a trained Support Vector Classifier (SVC) to predict the job category
- **Text Cleaning Pipeline** — Strips URLs, hashtags, mentions, punctuation, and special characters before processing
- **TF-IDF Vectorization** — Converts resume text into meaningful numerical features
- **Label Encoding** — Maps predicted class indices back to human-readable job category names
- **Interactive UI** — Built with Streamlit for a clean, browser-based experience
- **Optional Text Preview** — Toggle to view the raw extracted text from the uploaded file

---

## 🖥️ Demo

Upload any resume → the app extracts text, cleans it, runs it through the ML model, and displays the predicted job category instantly.

```
📂 Upload Resume (PDF / DOCX / TXT)
         │
         ▼
   Text Extraction
         │
         ▼
   Text Cleaning (regex-based)
         │
         ▼
   TF-IDF Vectorization
         │
         ▼
   SVC Model Prediction
         │
         ▼
   🎯 Predicted Job Category
```

---

## 🗂️ Repository Structure

```
Resume-Screening-App/
├── app.py                              # Main Streamlit application
├── Resume Screening with Python.ipynb  # Jupyter notebook for model training & EDA
├── clf.pkl                             # Trained SVC classifier (pickled)
├── tfidf.pkl                           # Fitted TF-IDF vectorizer (pickled)
├── encoder.pkl                         # Label encoder for category names (pickled)
└── reqiurements.txt                    # Python dependencies
```

---

## 🧠 How It Works

### 1. Text Extraction
The app supports three file formats:
- **PDF** — Extracted page by page using `PyPDF2`
- **DOCX** — Paragraph-wise extraction using `python-docx`
- **TXT** — Read with UTF-8 encoding, falling back to Latin-1

### 2. Text Cleaning
A regex-based `cleanResume()` function removes noise:
- URLs and web links
- Twitter-style mentions (`@user`) and hashtags (`#tag`)
- Retweet tokens (`RT`, `cc`)
- Punctuation and special characters
- Non-ASCII characters
- Excess whitespace

### 3. Vectorization
The cleaned text is transformed into a numeric feature vector using the pre-fitted **TF-IDF vectorizer** (`tfidf.pkl`) — the same one used during model training to ensure consistent feature representation.

### 4. Prediction
The feature vector is passed to the trained **Support Vector Classifier** (`clf.pkl`), which outputs a predicted class label. The **Label Encoder** (`encoder.pkl`) converts the class index back into the human-readable job category name.

---


## 📦 Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| `streamlit` | — | Web UI framework |
| `scikit-learn` | 1.5.2 | ML model & TF-IDF vectorizer |
| `PyPDF2` | — | PDF text extraction |
| `python-docx` | — | DOCX text extraction |
| `numpy` | 2.1.3 | Numerical operations |
| `pandas` | 2.2.3 | Data handling (training) |
| `scipy` | 1.14.1 | Sparse matrix support |
| `joblib` | 1.4.2 | Model serialization |

---

## 🏋️ Model Training

The model was trained and evaluated in the `Resume Screening with Python.ipynb` notebook. The pipeline includes:

- **Dataset** — Resume dataset with labeled job categories
- **Preprocessing** — Text cleaning + TF-IDF feature extraction
- **Model** — Support Vector Classifier (SVC)
- **Artifacts saved** — `clf.pkl`, `tfidf.pkl`, `encoder.pkl`

---




> ⭐ If this project helped you, please consider starring the repository!
