# quora-question-pairs
A NLP project to find weather given 2 questions are same are not semantically speaking.

Dataset Link - https://www.kaggle.com/c/quora-question-pairs
Table of contents
Introduction
Business Objectives and Constraints
Data Overview
Business Metrics
Basic EDA
Data Cleaning
Feature Extraction
EDA with Features
Featurization with SentenceBERT
i. EDA on new features related to SentenceBERT
Data Pre-processing
Training Models
i. Support Vector Classifier
ii. Random Forest
iii. XGBoost
iv. Another XGBoost 🏆
Final Thoughts
References

Data Overview
Available Columns: id, qid1, qid2, question1, question2, is_duplicate
Class labels: 0, 1
Total training data / No. of rows: 404290
No. of columns: 6
is_duplicate is the dependent variable.
No. of non-duplicate data points is 255027
No. of duplicate data points is 149263

We have 404290 training data points. And only 36.92% are positive. That means it is an imbalanced dataset.

**Data Cleaning**
We have converted everything to lower case.
We have removed contractions.
We have replaced currency symbols with currency names.
We have also removed hyperlinks.
We have removed non-alphanumeric characters.
We have removed inflections with word lemmatizer.
We have also removed HTML tags.
**Feature Extraction**
We have created 23 features from the questions.

We have created features q1_char_num, q2_char_num with count of characters for both questions.
We have created features q1_word_num, q2_word_num with count of characters for both questions.
We have created total_word_num feature which is equal to sum of q1_word_num and q2_word_num.
We have created differ_word_num feature which is absolute difference between q1_word_num and q2_word_num.
We have created same_first_word feature which is 1 if both questions have same first word otherwise 0.
We have created same_last_word feature which is 1 if both questions have same last word otherwise 0.
We have created total_unique_word_num feature which is equal to total number of unique words in both questions.
We have created total_unique_word_withoutstopword_num feature which is equal to total number of unique words in both questions without the stop words.
The total_unique_word_num_ratio is equal to total_unique_word_num divided by total_word_num.
We have created common_word_num feature which is count of total common words in both questions.
The common_word_ratio feature is equal to common_word_num divided by total_unique_word_num.
The common_word_ratio_min is equal to common_word_num divided by minimum number of words between question 1 and question 2.
The common_word_ratio_max is equal to common_word_num divided by maximum number of words between question 1 and question 2.
We have created common_word_withoutstopword_num feature which is count of total common words in both questions excluding the stopwords.
The common_word_withoutstopword_ratio feature is equal to common_word_withoutstopword_num divided by total_unique_word_withoutstopword_num.
The common_word_withoutstopword_ratio_min is equal to common_word_withoutstopword_num divided by minimum number of words between question 1 and question 2 excluding the stopwords.
The common_word_withoutstopword_ratio_max is equal to common_word_withoutstopword_num divided by maximum number of words between question 1 and question 2 excluding the stopwords.
Then we have extracted fuzz_ratio, fuzz_partial_ratio, fuzz_token_set_ratio and fuzz_token_sort_ratio features with fuzzywuzzy string matching tool. Reference: https://github.com/seatgeek/fuzzywuzzy



