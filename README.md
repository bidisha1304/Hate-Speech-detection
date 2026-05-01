# Hate-Speech-detection
Deep Learning Pipeline and Model Architecture

This project implements a comprehensive deep learning and machine learning framework for hate speech detection in textual data. The pipeline is designed to ensure robust text preprocessing, effective feature extraction, and reliable classification through a structured workflow.

🔹 Data Preprocessing and Text Cleaning

The raw textual dataset undergoes an extensive multi-stage preprocessing pipeline to improve data quality and enhance model performance. The steps include:

Conversion of text to lowercase for uniformity
Removal of HTML tags using parsing techniques
Elimination of URLs and hyperlinks
Expansion of chat abbreviations (e.g., LOL → laughing out loud)
Conversion of emojis into textual representations
Removal of punctuation and special characters
Spell correction using a fast spell-checking algorithm
Tokenization of sentences into individual words
Stopword removal with a customized list (retaining important negations like not, never)
Lemmatization to reduce words to their base verb forms

Finally, the cleaned tokens are reconstructed into processed sentences, forming the input for feature extraction.

🔹 Feature Extraction

To transform textual data into numerical representations, multiple feature extraction techniques are employed:

Bag of Words (BoW): Captures word frequency using unigram and bigram representations
TF-IDF (Term Frequency–Inverse Document Frequency): Assigns importance to words based on their relevance across documents
Word2Vec Embeddings: Learns dense vector representations of words using contextual relationships, and generates sentence vectors by averaging word embeddings

These diverse representations allow comparison between traditional and semantic approaches to text modeling.

🔹 Data Splitting

The dataset is divided into training and testing subsets using an 80:20 ratio. Stratified sampling is applied in some cases to maintain class balance across splits, ensuring fair model evaluation.

🔹 Machine Learning Models

Traditional classification is performed using the Bernoulli Naive Bayes algorithm, trained separately on:

Bag of Words features
TF-IDF features
Word2Vec embeddings

This allows performance comparison across different feature representations.

🔹 Deep Learning Model: LSTM-Based Text Classifier

The core deep learning component of this project is a Long Short-Term Memory (LSTM) network, designed to capture sequential dependencies and contextual meaning in text.

🔷 Text Vectorization and Sequencing

Before feeding text into the LSTM model:

A tokenizer is used to convert words into integer indices
Vocabulary size is limited to 10,000 words
Sentences are converted into sequences
Sequences are padded/truncated to a fixed length of 100 tokens

This ensures uniform input size for the neural network.

🔷 Model Architecture

The LSTM model follows a stacked architecture to progressively learn hierarchical language features:

Embedding Layer:
Transforms integer-encoded words into dense vector representations of dimension 128
Stacked LSTM Layers:
First LSTM layer (128 units): Captures long-term dependencies and complex patterns
Second LSTM layer (64 units): Refines contextual representations
Third LSTM layer (32 units): Produces a compact sequence representation
Dropout Layer:
A dropout rate of 0.3 is applied to reduce overfitting by randomly deactivating neurons during training
Fully Connected Output Layer:
A dense layer with sigmoid activation produces a probability score for binary classification
🔹 Training Strategy

The model is trained using the following configuration:

Optimizer: Adam
Loss Function: Binary Crossentropy
Batch Size: 32
Epochs: 5

The training process includes forward propagation, loss computation, backpropagation, and weight updates. Validation data is used during training to monitor performance and detect overfitting.

🔹 Evaluation Metrics

Model performance is evaluated using multiple metrics to provide a comprehensive assessment:

Accuracy
Precision, Recall, and F1-score
ROC Curve (Receiver Operating Characteristic)
AUC Score (Area Under Curve)

Additionally, the optimal classification threshold is determined using Youden’s Index, balancing true positive and false positive rates.

🔹 Testing and Prediction

After training, the model is evaluated on unseen test data to measure generalization performance. A prediction function is implemented to classify new input text:

Input text is tokenized and padded
Passed through the trained LSTM model
Output probability is thresholded to produce binary classification
🔹 Visualization and Analysis

To better understand model performance:

ROC curve is plotted to visualize classification capability
AUC score quantifies overall model effectiveness
Threshold tuning improves classification balance
🔹 Summary

This pipeline integrates advanced text preprocessing, multiple feature extraction strategies, and both traditional and deep learning models to effectively detect hate speech. The combination of semantic embeddings and sequential modeling enables improved understanding of contextual language patterns, making the system robust for real-world NLP applications.
