##  1. What was Completed This Week
* **Environment & Setup:** Created the dedicated project repository with a clean, modular structure. Added basic environment configuration requirements.
* **Data Ingestion:** Downloaded the *Women's E-Commerce Clothing Reviews* dataset from Kaggle and integrated a secure download pipeline instructions into the data directory README.
* **Initial EDA:** Conducted exploratory data analysis inside a Jupyter Notebook (`notebooks/01_eda.ipynb`). Inspecting text length distributions, checking for missing text values, and analyzing the distribution of target star ratings.

---

##  2. Important Commits & Files Changed
* `src/data_loader.py`: Created initial script to load and filter rows containing null values in the text columns.
* `notebooks/01_eda.ipynb`: Initialized the main visualization notebook containing distribution charts.
* `reports/week-01.md`: Documented the milestones achieved during this sprint.

---

##  3. Experiments Run & Results So Far
No formal deep learning models were trained this week. However, exploratory data distribution tests yielded important structural insights:
* Total clean text samples available: 22,641 (after dropping records missing the `Review Text` field).
* Target Imbalance Found: Over 70% of the dataset consists of ratings 4 and 5 (Positive). This strongly confirms our need to rely on the **F1-Score** rather than pure Accuracy as our primary evaluation metric.
* Average token length per review is roughly 60 words, indicating that a max sequence length padding parameter of $100$ or $128$ will be sufficient without losing critical information.

---

##  4. Problems or Blockers
* **Class Imbalance:** The distribution of sentiment classes is highly skewed toward positive scores. Standard training loops might result in high accuracy but poor recall on negative reviews. 
* *Solution:* We plan to use class weights in the loss function or perform downsampling during Week 2 data prep.

---

##  5. Plan for Next Week (Week 2)
* Apply text cleaning techniques (lowercasing, punctuation removal, stopword filtering or special tokenization depending on the chosen model).
* Execute the train/validation/test split.
* Establish a solid Machine Learning baseline using a TF-IDF vectorizer + Logistic Regression model to set our minimum performance threshold.
