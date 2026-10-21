# Phishing Email Detection System (Beginner Prototype)

## Project description
This project demonstrates text classification using TF-IDF and Logistic Regression. It classifies messages as `ham` (not spam) or `spam` based on a public labelled dataset.

**Dataset caveat:** The dataset used in this beginner prototype is the UCI SMS Spam Collection, which contains SMS messages rather than emails. Spam and phishing overlap but are not identical. This is therefore a message-classification prototype, not a validated phishing-email detector.

## Dataset
- Name: UCI SMS Spam Collection
- Dataset page: https://archive.ics.uci.edu/dataset/228/sms+spam+collection
- The notebook downloads the dataset from the UCI archive at runtime.
- Please follow the dataset's citation and usage terms on the UCI page.

## Technologies used
- Python
- Pandas
- Matplotlib
- Scikit-learn
- TF-IDF text features
- Logistic Regression
- Jupyter Notebook / Google Colab

## Files
- `Deepika_PhishingEmailDetection.ipynb` — notebook code and evaluation.
- `requirements.txt` — Python dependencies.
- `Deepika_ProjectReport_Updated.docx` — project report with the evaluation results.
- `README_Updated.md` — project setup and results information.

## Setup and run
### Option A: Google Colab
1. Upload `Deepika_PhishingEmailDetection.ipynb` to Google Colab.
2. Run the cells from top to bottom.
3. Allow the notebook to download the dataset when the code runs.

### Option B: Local Jupyter
1. Install Python 3.10 or later.
2. Put the notebook and `requirements.txt` in the same folder.
3. In a terminal, run:
   ```bash
   python -m pip install -r requirements.txt
   ```
4. Start Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
   If Jupyter is not installed, install it with `python -m pip install notebook`.
5. Open the notebook and run all cells in order.

## Evaluation results
The notebook was run in Google Colab and produced the following results on a held-out test set of **1,115 messages**:

- **Accuracy:** 97% (approximately 0.97)
- **Ham:** precision 0.96, recall 1.00, F1-score 0.98 (966 examples)
- **Spam:** precision 1.00, recall 0.75, F1-score 0.86 (149 examples)
- **Confusion matrix** (rows = actual class; columns = predicted class; order: ham, spam):

  |  | Predicted ham | Predicted spam |
  |---|---:|---:|
  | Actual ham | 966 | 0 |
  | Actual spam | 37 | 112 |

The model correctly classified 966 ham messages and 112 spam messages. It missed 37 spam messages by classifying them as ham. This shows why accuracy alone is not enough: the spam recall of 0.75 means some spam messages were missed.

## Responsible use and limitations
This model can make mistakes. A message classified as `ham` is not guaranteed to be safe. Do not click suspicious links, share passwords or OTPs, or use this prototype as the sole security control. The test results describe performance on this SMS dataset only and do not establish real-world phishing-email detection performance. For a dedicated phishing-email project, replace the SMS dataset with a properly labelled, documented phishing-email dataset and repeat the evaluation.

## References
1. UCI Machine Learning Repository, SMS Spam Collection: https://archive.ics.uci.edu/dataset/228/sms+spam+collection
2. Scikit-learn TF-IDF Vectorizer documentation: https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html
3. Scikit-learn Logistic Regression documentation: https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html
