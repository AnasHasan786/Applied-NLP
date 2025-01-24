# **Text Generation Using RNN**

<p align="justify">
  This project focuses on generating text using a Recurrent Neural Network (RNN) implemented in       TensorFlow/Keras. The model is trained on textual data, where it learns patterns and structures     in the text, enabling it to generate new coherent text sequences.
</p>

## **Table of Contents**

1. [Project Overview](project-overview)
2. [Dataset](dataset)
3. [Preprocessing](preprocessing)
4. [Model Architecture](model-architecture)
5. [Training](training)
6. [Text Generation](text-generation)
7. [Results](results)
8. [Conclusion](conclusion)

## **Project Overview**

<p align="justify">
  This project demonstrates how an RNN can be utilized to perform text generation by predicting   the next character in a sequence. Using an LSTM-based RNN architecture, the model captures      the dependencies and patterns in the dataset to generate realistic text sequences.
</p>

## **Dataset**

The dataset for this project consists of multiple CSV files containing text data. These files are combined into a single dataset for training. Key steps:

* Input Folder: All CSV files are stored in the folder dataset/.
* Column Name: The relevant text data is extracted from the column named Input Text.

## **Preprocessing**

Steps:

1. Combine Text: Text from all CSV files is concatenated into a single string.
2. Text Cleaning: Remove special characters and convert the text to lowercase.
3. Tokenization: The text is tokenized at the character level, assigning unique integers to each character.
4. Sequence Preparation: Sequences of fixed length (100 characters) are created along with their corresponding labels.
5. One-Hot Encoding: Labels are one-hot encoded to make them suitable for classification.

## **Model Architecture**

The model is built using the Sequential API in TensorFlow/Keras. Key components include:

1. Embedding Layer:
   * Converts tokenized sequences into dense vectors of fixed size.
   * Embedding Dimension: 50.
   
2. LSTM Layers:
   * Four stacked LSTM layers with 150 units each.
   * return_sequences=True for intermediate LSTM layers to maintain sequence outputs.

3. Dense Layer:
   * Fully connected layer with softmax activation to predict the next character.

**Loss Function**: Categorical Crossentropy
<br>
**Optimizer**: Adam
<br>
**Metrics**: Accuracy.

## **Training**

The model is trained for 100 epochs with a batch size of 32. The training process involves:

* Feeding input sequences (X) and their corresponding next characters (y) to the model.
* Optimizing the weights using backpropagation and the Adam optimizer.

## **Text Generation**

A custom text generation function generates new text based on a seed input string:

1. **Input**: A starting string (seed text).
2. **Prediction**: For each character in the desired length, the model predicts the next character.
3. **Output**: The generated text is appended character by character.

## **Results**

After training, the model is capable of generating text sequences based on the patterns learned from the input data. Example output:

**Input Seed**: the quick brown fox
<br>
**Generated Text**: the quick brown fox jumps over the lazy dog and runs away into the forest...

**Note: The quality of the generated text depends on the size and quality of the dataset.**

## **Model Performance and Data Quality**

The current model is trained on a dataset that was created by merging 10 CSV files together. While this approach allowed for a diverse set of examples, it may have led to inconsistencies or noise in the data that impacted the performance of the model. As a result, the text generation output might not be as accurate or coherent as expected.

We are currently working on refining the dataset and improving the model's performance. Future improvements will involve:

- Cleaning and preprocessing the merged dataset.
- Exploring other dataset combinations or more balanced sources.
- Fine-tuning the RNN model with optimized hyperparameters.

## **Conclusion**

This project showcases the potential of RNNs in generating coherent text sequences by learning patterns in character-level text data. The approach can be extended to larger datasets or fine-tuned for specific applications like story generation, chatbots, or automated text completion.
