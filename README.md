Sentiment Analysis of Transportation App Reviews

This project performs sentiment analysis on transportation application user reviews using a fine-tuned Transformer model (IndoBERT). The goal is to classify reviews into sentiment categories: Positive, Negative, or Neutral.

Code Overview
This code is written in Google Colab and covers the following steps:

Library Installation and Imports: Ensures that all necessary libraries such as pandas, numpy, scikit-learn, transformers, nltk, and Sastrawi are installed.

NLTK Data Download: Downloads data required by NLTK (such as punkt and stopwords) for text pre-processing.

Load & Pre-process Dataset:

Uses a simulated review dataset as an example.

Performs text pre-processing, including:

Converting text to lowercase.

Removing punctuation and numbers.

Tokenization (breaking text into words).

Removal of stop words (common words that do not carry sentiment meaning, such as "the", "and", "in"). In the corrected version, Indonesian stop words from NLTK are used.

Sentiment Label Encoding: Converts sentiment labels (Positif, Negatif, Netral) into numerical representations (0, 1, 2) using LabelEncoder. This label mapping is also saved for reference.

Data Splitting: Divides the dataset into training, validation, and test sets to effectively train and evaluate the model.

Data Tokenization with Transformer:

Uses AutoTokenizer from the indobenchmark/indobert-base-p1 model to convert review text into a numerical format (token IDs) understandable by the Transformer model.

Data is padded and truncated to a uniform length.

The dataset is converted to the datasets library format, which is compatible with Hugging Face Trainer.

Fine-tuning Transformer Model (IndoBERT):

Loads the pre-trained indobenchmark/indobert-base-p1 model.

Sets training arguments (TrainingArguments) such as the number of epochs, batch size, evaluation strategy, and output directory.

Initializes the Hugging Face Trainer and starts the fine-tuning process on the training dataset.

Model Evaluation:

Evaluates the model's performance on the previously unseen test set.

Displays evaluation results (e.g., accuracy, F1-score).

Generates a classification report showing precision, recall, and F1-score for each sentiment class.

Visually displays a confusion matrix to understand how the model correctly or incorrectly classifies sentiments.

Model & Tokenizer Saving: Saves the fine-tuned model, tokenizer, and label mapping to a local directory so they can be reused later without retraining.

Simulated Dataset Structure
The dataset used in this example is simulated, with two main columns:

Ulasan: Contains the text of user reviews.

Sentimen: Contains the sentiment label (Positif, Negatif, Netral) for each review.

Example Data:

Ulasan

Sentimen

Aplikasi ini sangat membantu sekali, navigasinya akurat!

Positif

Driver sering nyasar, bikin telat terus. Payah!

Negatif

Fitur barunya lumayan, tapi loadingnya agak lambat.

Netral

Harga kadang naik terlalu tinggi saat jam sibuk.

Negatif

Mudah digunakan dan responsif, suka sekali!

Positif


Export to Sheets
Libraries Used
pandas

numpy

scikit-learn

matplotlib

seaborn

torch

transformers

accelerate

datasets

nltk

Sastrawi (used for stopword remover from NLTK)

How to Use (in Google Colab)
Open the sentiment_analysis_transportation.ipynb file in Google Colab.

Run each code cell in sequence.

Ensure you have an internet connection to download the pre-trained model and NLTK data.

The trained model and tokenizer will be saved in the ./model_sentimen_ulasan_aplikasi directory within your Colab session.
