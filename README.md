# 📝✨ Text Summarization with Extractive & Abstractive Models

Welcome to the **Text Summarization** notebook! This project demonstrates both **extractive** and **abstractive** summarization techniques using state-of-the-art NLP libraries and models.  
It is designed for easy experimentation and evaluation of summarization methods on any English text.

---

## 📚 Table of Contents

- [Overview](#overview)
- [Setup & Requirements](#setup--requirements)
- [Module Explanations](#module-explanations)
- [How It Works](#how-it-works)
- [Performance Notes](#performance-notes)
- [Usage Example](#usage-example)
- [Evaluation](#evaluation)
- [License](#license)

---

## 🧐 Overview

This notebook covers:
- **Extractive Summarization** using the TextRank algorithm (via `sumy`)
- **Abstractive Summarization** using pre-trained transformer models (`T5-small` and `BART-large-cnn`)
- **Evaluation** of summaries using ROUGE metrics

---

## ⚡️ Setup & Requirements

Install all dependencies with:

```python
!pip install transformers torch sumy rouge-score nltk
```

---

## 🧩 Module Explanations

### 1. `nltk` 🦜

- **Why?**  
  Used for sentence tokenization and preprocessing.  
- **How?**  
  Downloads the `punkt` tokenizer for splitting text into sentences.
- **Performance:**  
  Fast and lightweight; essential for most NLP tasks.

### 2. `sumy` 📑

- **Why?**  
  Implements the **TextRank** algorithm for extractive summarization.
- **How?**  
  Parses text, tokenizes it, and selects the most important sentences.
- **Performance:**  
  Very fast, works well for short to medium texts, but does not generate new sentences—only selects from the original.

### 3. `transformers` 🤖

- **Why?**  
  Provides access to powerful pre-trained models for **abstractive summarization**.
- **How?**  
  Loads `T5-small` and `facebook/bart-large-cnn` models for generating concise summaries.
- **Performance:**  
  - `T5-small`: Fast, lightweight, good for quick summaries.
  - `BART-large-cnn`: Larger, more accurate, produces high-quality summaries but requires more memory and time.

### 4. `torch` 🔥

- **Why?**  
  Backend for running transformer models efficiently.
- **How?**  
  Handles tensor computations and GPU acceleration if available.
- **Performance:**  
  Essential for deep learning; enables fast inference on modern hardware.

### 5. `rouge-score` 📊

- **Why?**  
  Evaluates the quality of generated summaries by comparing them to reference texts.
- **How?**  
  Computes ROUGE-1 and ROUGE-L metrics (precision, recall, F1).
- **Performance:**  
  Fast and standard for summarization evaluation.

---

## ⚙️ How It Works

1. **Extractive Summarization:**  
   - Uses TextRank to select the most important sentences from the input.

2. **Abstractive Summarization:**  
   - Uses transformer models to generate new, concise summaries that may paraphrase or reword the input.

3. **Evaluation:**  
   - Compares the generated summary to the original text using ROUGE metrics.

---

## 🚀 Usage Example

```python
# 1. Set your input text
text = "Text summarization is one of the most interesting problems in NLP..."

# 2. Extractive summary
extractive = extractive_summary(text, num_sentences=2)

# 3. Abstractive summary (T5)
t5_sum = abstractive_summary(text, model="t5", min_len=15, max_len=60)

# 4. Abstractive summary (BART)
bart_sum = abstractive_summary(text, model="bart", min_len=15, max_len=60)

# 5. Evaluation
scores = evaluate_summary(text, bart_sum)
```

---

## 📈 Performance Notes

- **Extractive (TextRank):**  
  - 🟢 Fast, no GPU needed  
  - 🟡 Only selects sentences, does not paraphrase

- **Abstractive (T5-small):**  
  - 🟢 Fast, suitable for limited resources  
  - 🟡 May miss some context in longer texts

- **Abstractive (BART-large-cnn):**  
  - 🟢 High-quality, fluent summaries  
  - 🔴 Requires more memory and time

- **Evaluation (ROUGE):**  
  - 🟢 Standard, interpretable metrics  
  - 🟡 Only measures overlap, not semantic quality

---

## 🏁 Evaluation

The notebook prints ROUGE-1 and ROUGE-L scores for each summary, showing:
- **Precision:** How much of the summary is relevant
- **Recall:** How much of the original is covered
- **F1:** Harmonic mean of precision and recall

---

## 📄 License

This notebook is provided for educational and research purposes.  
Feel free to modify and use it in your own projects!

---

**✨ Happy Summarizing!
