# Multi_Class_sentiment classification using nlp
This Repo is about MultiClass SentimentClassification .GoEmotions is a dataset containing 58k curated comments from Reddit, annotated with 27 emotion categories plus a neutral category. Using this dataset, I broadly categorized the emotions into five groups: happy, sad, anger, surprise, and fear. I then preprocessed the data using the spaCy library, which involved removing stop words, keeping only alphabetic words, and applying stemming. For feature extraction, I employed techniques like Count Vectorizer, TF-IDF, and TF-IDF with n-grams. I experimented with various machine learning models, including Naive Bayes, Logistic Regression, Random Forest, and Artificial Neural Networks (ANNs). This was followed by hyperparameter tuning, evaluating the models using metrics, and analyzing the confusion matrix.

============================================================================================
GoEmotions Dataset
       ↓
Broad Categorization into 5 Emotions (Happy, Sad, Anger, Surprise, Fear)
       ↓
Data Preprocessing
  - Removing Stop Words
  - Keeping Only Alphabetic Words
  - Stemming
       ↓
Feature Extraction
  - Count Vectorizer
  - TF-IDF
  - TF-IDF with N-grams
       ↓
Modeling
  - Naive Bayes
  - Logistic Regression
  - Random Forest
  - Artificial Neural Networks (ANNs)
       ↓
Model Evaluation
  - Hyperparameter Tuning
  - Metrics Evaluation
  - Confusion Matrix Analysis
========================================================================================
GoEmotions
GoEmotions is a corpus of 58k carefully curated comments extracted from Reddit, with human annotations to 27 emotion categories or Neutral.

Number of examples: 58,009.
Number of labels: 27 + Neutral.
Maximum sequence length in training and evaluation datasets: 30.

which contains a train/test/validation split:

Size of training dataset: 43,410.
Size of test dataset: 5,427.
Size of validation dataset: 5,426.
The emotion categories are: admiration, amusement, anger, annoyance, approval, caring, confusion, curiosity, desire, disappointment, disapproval, disgust, embarrassment, excitement, fear, gratitude, grief, joy, love, nervousness, optimism, pride, realization, relief, remorse, sadness, surprise.

wget -P data/full_dataset/ https://storage.googleapis.com/gresearch/goemotions/data/full_dataset/goemotions_1.csv
wget -P data/full_dataset/ https://storage.googleapis.com/gresearch/goemotions/data/full_dataset/goemotions_2.csv
wget -P data/full_dataset/ https://storage.googleapis.com/gresearch/goemotions/data/full_dataset/goemotions_3.csv



Data Format
Raw dataset, split into three csv files, includes all annotations as well as metadata on the comments. Each row represents a single rater's annotation for a single example. This file includes the following columns:

text: The text of the comment (with masked tokens, as described in the paper).
id: The unique id of the comment.
author: The Reddit username of the comment's author.
subreddit: The subreddit that the comment belongs to.
link_id: The link id of the comment.
parent_id: The parent id of the comment.
created_utc: The timestamp of the comment.
rater_id: The unique id of the annotator.
example_very_unclear: Whether the annotator marked the example as being very unclear or difficult to label (in this case they did not choose any emotion labels).
separate columns representing each of the emotion categories, with binary labels (0 or 1)
The data we used for training the models includes examples where there is agreement between at least 2 raters. Our data includes 43,410 training examples (train.tsv), 5426 dev examples (dev.tsv) and 5427 test examples (test.tsv). These files have no header row and have the following columns:

text
comma-separated list of emotion ids (the ids are indexed based on the order of emotions in emotions.txt)
id of the comment

Broadly Emotions are categorized like Below:
"anger": ["anger", "annoyance", "disapproval"] 
"fear": ["fear", "nervousness"]
"joy": ["joy", "amusement", "approval", "excitement", "gratitude",  "love", "optimism", "relief", "pride", "admiration", "desire", "caring"]
"sadness": ["sadness", "disappointment", "embarrassment", "grief",  "remorse"]
"surprise": ["surprise", "realization", "confusion", "curiosity"]




