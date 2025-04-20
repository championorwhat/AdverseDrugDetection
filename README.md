# 🧠 Multilingual Adverse Drug Event Detection

This project focuses on detecting adverse drug events (ADEs) from social media posts across **multiple languages** (English, German, French, Russian). It integrates **machine translation**, **text preprocessing**, **TF-IDF & sentence embeddings**, **stacked ensemble models**, and a **fine-tuned BioBERT** model to improve detection accuracy in a multilingual setting. The system has been developed and evaluated as part of the **SMM4H 2025 Shared Task**.

---

## 📌 Project Highlights

- ✅ Handles multilingual data via **translation** using `facebook/nllb-200-distilled-600M`
- ✅ Supports **language-independent sentence embeddings**
- ✅ Fixes class imbalance using **SMOTE oversampling**
- ✅ Uses **stacked ensemble** of XGBoost, CatBoost, and Logistic Regression
- ✅ Fine-tuned **BioBERT** model for biomedical contextual understanding
- ✅ Final prediction selection based on **validation F1-score**
- ✅ Packaged results into ZIP for submission (e.g., SMM4H format)

---

## ⚙️ Methodology Summary

| Step                           | Details                                                                                 |
|--------------------------------|-----------------------------------------------------------------------------------------|
| **Translation**                | Used `facebook/nllb-200-distilled-600M` to convert German, French, and Russian to English |
| **Text Preprocessing**         | Lowercase, remove URLs/mentions/special chars, tokenize, stopword removal              |
| **Vectorization**             | Applied **TF-IDF** and **Sentence-BERT embeddings** (`paraphrase-MiniLM-L6-v2`)        |
| **Class Imbalance Handling**   | Used **SMOTE** to balance classes                                                      |
| **Model 1 - Stacked Ensemble** | XGBoost, CatBoost, and Logistic Regression stacked with **Random Forest** as meta-learner |
| **Model 2 - SVM**              | Trained on sentence embeddings; selected if dev F1 is higher                           |
| **Model 3 - BioBERT**          | Fine-tuned on translated and cleaned biomedical text data                              |
| **Test Prediction**            | Sentence embeddings → best model (based on dev) → output predictions (0/1)             |
| **Submission**                 | Predictions zipped in required CSV format                                              |

---
