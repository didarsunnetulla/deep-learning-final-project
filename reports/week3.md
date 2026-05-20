#  Progress Report: Week 3

##  1. What was Completed This Week
* **Deep Learning Tokenization:** Implemented a deep learning tokenization and padding pipeline using Keras text preprocessing tools. Text reviews were converted into integer sequences and padded to a fixed length of 128 tokens based on Week 1 EDA.
* **Architecture Design:** Designed and built a **Bidirectional Long Short-Term Memory (BiLSTM)** neural network. Included an initial Spatial Dropout layer to prevent embedding overfitting and a Softmax output layer for 3-class classification.
* **Model Training & Regularization:** Trained the neural network using `sparse_categorical_crossentropy` loss and the Adam optimizer. Integrated `EarlyStopping` based on validation loss to prevent overfitting and save the best weights.
* **Visualizing Convergence:** Plotted and evaluated the training vs. validation loss and accuracy curves.

---

##  2. Important Commits & Files Changed
* `notebooks/02_deep_learning_model.ipynb`: Created a new notebook containing the full tokenization, BiLSTM architecture setup, and training loop.
* `results/dl_training_curves.png`: Saved plots of the training process metrics.
* `reports/week-03.md`: Documented Week 3 outcomes.

---

##  3. Experiments Run & Results So Far
We trained our BiLSTM model for 10 epochs with a batch size of 64. Early stopping triggered at epoch 6 as validation loss began to plateau, successfully avoiding overfitting.

### Performance Evaluation & Comparison

| Model | Test Accuracy | Test Macro F1-Score | Status |
| :--- | :---: | :---: | :--- |
| **Week 2 Baseline (TF-IDF + LogReg)** | 0.764 | 0.621 | Benchmark |
| **Week 3 Deep Learning (BiLSTM)** | **0.819** | **0.678** | **Improved** |

The Deep Learning model successfully outperformed the classical baseline. By utilizing deep sequential layers, the model managed to capture contextual relationships between words much better than simple raw word frequencies.

---

##  4. Problems or Blockers
* **High Variance / Overfitting:** In early test runs without regularization, the training accuracy quickly approached 95%, while validation accuracy hovered around 78%. 
* *Solution:* We added a `SpatialDropout1D(0.3)` right after the Embedding layer and an additional `Dropout(0.3)` layer before the final dense classification layer. This successfully closed the generalization gap.

---

##  5. Plan for Next Week (Week 4)
* Conduct a detailed Error Analysis: extract specific reviews where the model failed and categorize the mistakes.
* Complete final code refactoring and clean up the repository.
* Write the comprehensive Final Report (`final-report.md`) and prepare the final presentation/demo.
