
# Email Spam Detection using Naive Bayes (Multinomial Naive Bayes)

## Project Overview

This project implements an email spam detection system using the Naive Bayes algorithm. The system classifies emails as either "SPAM" or "NOT SPAM" based on their content. It uses a dataset containing labeled messages, where each message is classified as either spam or non-spam (ham). The model is trained using the Multinomial Naive Bayes classifier, and its performance is evaluated using various metrics such as accuracy, precision, recall, and F1 score.

## Code Explanation

The code is structured to perform the following tasks:

### 1. Data Preprocessing

The project begins by importing the necessary libraries and loading the `spam.csv` dataset. The dataset consists of two columns: `Category` (spam/ham) and `Message` (the email content). The following steps are carried out during preprocessing:

- The `Unnamed: 2`, `Unnamed: 3`, and `Unnamed: 4` columns are dropped since they are not useful.
- The `Category` column is renamed to `Category`, and the `Message` column remains unchanged.
- A new column `spam` is created where the labels "spam" are assigned a value of 1 and "ham" a value of 0, making it suitable for machine learning.

### 2. Train-Test Split

The dataset is split into training and test sets, with 80% of the data used for training and 20% for testing. This is done using the `train_test_split` function from `sklearn.model_selection`.

### 3. Text Vectorization

The text data (email messages) is transformed into numerical data using the `CountVectorizer` from `sklearn.feature_extraction.text`. The `CountVectorizer` converts the email text into a matrix of word counts. This allows the machine learning models to work with the data, as they require numeric inputs.

### 4. Model Training and Evaluation

The following machine learning models are initialized and trained:

- Logistic Regression
- Decision Tree Classifier
- Gradient Boosting Classifier
- Multinomial Naive Bayes

Each model is trained using the training data and then evaluated using the test set. The evaluation metrics include:

- **Accuracy**: The proportion of correctly predicted instances.
- **Precision**: The ratio of correctly predicted positive observations to the total predicted positives.
- **Recall**: The ratio of correctly predicted positive observations to all actual positives.
- **F1-Score**: The weighted average of Precision and Recall.

The results of these metrics are compared and displayed in a table for easy evaluation. From the table, it was found that **Multinomial Naive Bayes** outperformed the other models, demonstrating the best balance of accuracy, precision, recall, and F1-score, making it the best-fit model for this task.

<img width="348" alt="image" src="https://github.com/user-attachments/assets/ff68e53c-5564-4207-b4c3-0e5e7c54c4f3" />


### 5. Email Spam Prediction

Once the models are trained, the system allows users to input an email text. The email is transformed into a word count matrix using the `CountVectorizer`, and the trained Naive Bayes model predicts whether the email is "SPAM" or "NOT SPAM". The result is displayed in color-coded output for easy interpretation.

### Key Functions

- `predict_spam(email_text)`: This function takes the input email text, transforms it using the `CountVectorizer`, and predicts whether it is spam or not using the trained Naive Bayes model.
  - If the prediction is "spam", it returns "SPAM" with a red color.
  - If the prediction is "ham", it returns "NOT SPAM" with a green color.

### Sample Output

```bash
Enter the email text: Congratulations! You've won a $1000 gift card. Click here to claim your prize!
SPAM (Red)
