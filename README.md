# Japanese_Emotion_Classifier
### Training Emotion Classification Models Using Emotion Intensity Lists

This script is designed to train emotion classification models leveraging the WRIME dataset(https://github.com/ids-cv/wrime/blob/master/README.en.md). 

#### **Dataset Overview**

The WRIME dataset utilized in this script is for analyzing emotion intensities in Japanese social media posts.  This dataset consists of Japanese tweets. Each tweet is annotated for eight emotions (e.g., Joy, Sadness, Anger) using a scale from 0 (no emotion) to 3 (strong emotion), as well as an overall sentiment score. 

#### **Data Exploration and Preprocessing**

Data analysis in the script includes computing and visualizing a correlation matrix of the emotion intensities. This step is crucial to understand the relationships between different emotions within the dataset.

The script calculates weighted average sentiment scores for each emotion by multiplying individual emotion intensities by the corresponding sentiment scores and averaging the results. This reveals positivity or negativity of each emotion. It helps in grouping emotions into broad categories.

#### **Data Cleaning and Preparation**

The preprocessing stage also involves cleaning the dataset by removing tweets that lack significant emotional content (where all emotion intensities are zero). For tweets where multiple emotions exhibit the highest intensity (ties), the script adjusts these scores by applying a tie breaking rule to prioritize the emotion whose average sentiment score is the closest to the overall sentiment score, thereby resolving ambiguities in emotion dominance.

#### **Model Training Setup**

The training employs the `AutoTokenizer` and `AutoModelForSequenceClassification` from the Hugging Face’s transformers library, utilizing the 'cl-tohoku/bert-base-japanese-whole-word-masking` architecture (https://huggingface.co/tohoku-nlp/bert-base-japanese-whole-word-masking). These tools are crucial for converting raw text into a format suitable for the BERT model.


#### **Tokenization and Normalization**

A custom tokenization process is applied, which not only splits the text into tokens but also normalizes the emotion intensity lists. 

#### **Training Execution**

Training is conducted using the Hugging Face `Trainer` API.

#### **Metrics Computation**

The script defines custom metrics—accuracy, precision, recall, and F1 score—to comprehensively evaluate the performance of the emotion classification model.
