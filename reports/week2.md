##  1. What was Completed This Week
* **Text Preprocessing Pipeline:** Implemented a standardized text cleaning function that handles lowercasing, removes HTML tags/punctuation, and strips unnecessary whitespace.
* **Stratified Data Splitting:** Executed a strict Train/Validation/Test split ($70\% / 15\% / 15\%$). Used stratified splitting to ensure that the severe class imbalance (discovered in Week 1) is proportionally preserved across all subsets.
* **Baseline Model Implementation:** Developed and evaluated our traditional Machine Learning benchmark using **TF-IDF Vectorization** and **Logistic Regression** with balanced class weights.

---

##  2. Important Commits & Files Changed
* `src/preprocessing.py`: Contains modular functions for text cleaning and dataset splitting.
* `src/baseline.py`: Code for training the TF-IDF + Logistic Regression model, evaluating it, and saving metrics.
* `results/baseline_confusion_matrix.png`: Generated evaluation matrix for visual inspection.

---

##  3. Experiments Run & Results So Far
The baseline model was successfully trained on the engineered 3-class target (`Negative`, `Neutral`, `Positive`). Because of the dataset's high class imbalance, we configured the logistic regression classifier with `class_weight='balanced'`.

### Baseline Performance Summary (Test Set)

| Metric | Score | Note |
| :--- | :--- | :--- |
| **Accuracy** | 0.764 | Good overall coverage, but heavily influenced by the majority class. |
| **Macro Precision** | 0.582 | Model sometimes struggles with false positives in minority classes. |
| **Macro Recall** | 0.691 | Solid recall; the balanced weights successfully forced the model to catch negative reviews. |
| **Primary Metric: Macro F1-Score** | **0.621** | **Our baseline threshold.** The Deep Learning model in Week 3 must beat this score. |

---

##  4. Problems or Blockers
* **Neutral Class Ambiguity:** The baseline model significantly struggles with the `Neutral` class (3 stars). Many neutral reviews use mixed emotional words (e.g., "The dress is beautiful but too small"), causing the linear TF-IDF model to misclassify them as either purely positive or purely negative.
* *Mitigation:* Linear word-frequency features lack contextual awareness. This confirms our hypothesis that a deep sequential network (BiLSTM) or context-aware Transformer (BERT) will be necessary to resolve these semantic nuances in Week 3.

---

##  5. Plan for Next Week (Week 3)
* Tokenize texts using deep learning tokenizers (Keras Tokenizer for BiLSTM or Hugging Face WordPiece for DistilBERT).
* Build the Deep Learning pipeline.
* Train the advanced model, plot training/validation loss curves, and initiate hyperparameter tuning.
