# MultiClass Sentiment Classification

This repository focuses on MultiClass Sentiment Classification using the GoEmotions dataset, which contains 58k curated comments from Reddit. The dataset is annotated with 27 emotion categories plus a neutral category. For this project, the emotions were broadly categorized into five groups: **happy**, **sad**, **anger**, **surprise**, and **fear**.

## Project Workflow

1. **GoEmotions Dataset**  
   - Number of examples: 58,009  
   - Number of labels: 27 + Neutral  
   - Maximum sequence length in training and evaluation datasets: 30

   Data Split:
   - Training: 43,410 examples
   - Test: 5,427 examples
   - Validation: 5,426 examples

2. **Broad Categorization into 5 Emotions**  
   - Happy  
   - Sad  
   - Anger  
   - Surprise  
   - Fear

3. **Data Preprocessing**  
   - Removing Stop Words  
   - Keeping Only Alphabetic Words  
   - Stemming

4. **Feature Extraction**  
   - Count Vectorizer  
   - TF-IDF  
   - TF-IDF with N-grams

5. **Modeling**  
   - Naive Bayes  
   - Logistic Regression  
   - Random Forest  
   - Artificial Neural Networks (ANNs)

6. **Model Evaluation**  
   - Hyperparameter Tuning  
   - Metrics Evaluation  
   - Confusion Matrix Analysis

## GoEmotions Dataset Details

The GoEmotions dataset is a corpus of 58k carefully curated comments extracted from Reddit, with human annotations to 27 emotion categories or Neutral. The data includes:

- **Emotion Categories**: admiration, amusement, anger, annoyance, approval, caring, confusion, curiosity, desire, disappointment, disapproval, disgust, embarrassment, excitement, fear, gratitude, grief, joy, love, nervousness, optimism, pride, realization, relief, remorse, sadness, surprise.
- **Broad Categorization**:
  - "anger": ["anger", "annoyance", "disapproval"]
  - "fear": ["fear", "nervousness"]
  - "joy": ["joy", "amusement", "approval", "excitement", "gratitude", "love", "optimism", "relief", "pride", "admiration", "desire", "caring"]
  - "sadness": ["sadness", "disappointment", "embarrassment", "grief", "remorse"]
  - "surprise": ["surprise", "realization", "confusion", "curiosity"]

### Dataset Download

The raw dataset, split into three CSV files, includes all annotations and metadata on the comments. Each row represents a single rater's annotation for a single example. The dataset can be downloaded using the following commands:

```sh
wget -P data/full_dataset/ https://storage.googleapis.com/gresearch/goemotions/data/full_dataset/goemotions_1.csv
wget -P data/full_dataset/ https://storage.googleapis.com/gresearch/goemotions/data/full_dataset/goemotions_2.csv
wget -P data/full_dataset/ https://storage.googleapis.com/gresearch/goemotions/data/full_dataset/goemotions_3.csv
```

### Data Format

The raw dataset includes the following columns:

- **text**: The text of the comment (with masked tokens, as described in the paper).
- **id**: The unique id of the comment.
- **author**: The Reddit username of the comment's author.
- **subreddit**: The subreddit that the comment belongs to.
- **link_id**: The link id of the comment.
- **parent_id**: The parent id of the comment.
- **created_utc**: The timestamp of the comment.
- **rater_id**: The unique id of the annotator.
- **example_very_unclear**: Whether the annotator marked the example as being very unclear or difficult to label (in this case they did not choose any emotion labels).
- Separate columns representing each of the emotion categories, with binary labels (0 or 1).

The data used for training the models includes examples where there is agreement between at least 2 raters. The training dataset (`train.tsv`), validation dataset (`dev.tsv`), and test dataset (`test.tsv`) have the following columns:

- **text**: The text of the comment
- **emotion ids**: Comma-separated list of emotion ids (indexed based on the order of emotions in `emotions.txt`)
- **id**: The unique id of the comment

---

This description provides an overview of your project and detailed information about the dataset and methodology.

