---
library_name: transformers
pipeline_tag: token-classification
---

# Model Card for Model ID

L52-PosTag-XmlRoberta is a token classification model, trained in the Spanish language.

## Model Details

As the model is trained with the Ancora corpus, the tags used are listed as follows:

- NOUN
- PROPN
- VERB
- SCONJ
- SYM
- PUNCT
- INTJ
- X
- CCONJ
- AUX
- DET
- ADP
- PART
- NUM
- PRON
- ADV
- ADJ
- _

### Model Description

The task performed by the model works alongside the XLMRobertaTokenizerFast tokenizer, which is fitted with the xlm-Roberta base model to help us obtain the tokenized version of our corpus.
Once tokenization is done, the model will classify each word in our sentences into a specific part of speech (17 categories).
For further analysis and comprehension, a small algorithm is included at the end to obtain the classification with the original POS labels.

- **Developed by:** Daniel Bautista Hernández
- **Model type:** Token Clasificator
- **Language(s) (NLP):** Spanish
- **Finetuned from model [optional]:** xlm-roberta-base

### Model Sources [optional]

<!-- Provide the basic links for the model. -->

- **Repository:** [More Information Needed]
- **Paper [optional]:** [More Information Needed]
- **Demo [optional]:** [More Information Needed]

## Uses

POS tagging acts as an initial part of the process in multiple NLP tasks. It is crucial for:

- Text Preprocessing: Facilitating the preparation of text data for further analysis and model training.
- Named Entity Recognition (NER): Improving the accuracy of identifying proper nouns, dates, and other specific entities in text.
- Syntactic Parsing: Assisting in the understanding of sentence structure by providing part of speech information.
- Sentiment Analysis: Enhancing the classification of sentiment by understanding the role of each word in a sentence.
- Machine Translation: Improving translation quality by accurately identifying and translating parts of speech.
- By accurately tagging parts of speech, the model enhances the performance of these and other NLP applications.

## Training Details

The training is conducted in epochs, with the help of torch DataLoaders.
An early stopping process is also added, and the best model is saved.
The AdamW optimizer is used, and CrossEntropyLoss is employed as the loss function.

The hyperparameters used are:

- Epochs: 8
- Patience (Early Stopping): 2



### Training Data

For training purposes, the Ancora corpus was chosen. Given the format of the corpus, a few pre-processing tasks are needed.
All the sentences and words in Ancora have the necessary information, making it easy to create the lists of words that XLMRobertaTokenizerFast receives as input. Simultaneously, the list of tags is crafted.
Once we have tokenized the sentences, the tags need to be realigned according to the new dimensions of the lists.
The last steps related to processing the data are more related to optimization and good practices, which include obtaining Datasets and DataLoaders to achieve batch loading.


## Evaluation

After testing, an F1 score metric of 0.97 was obtained. 
This high score indicates that the model performs very well in accurately tagging parts of speech in the Spanish language. 
The F1 score combines both precision and recall, providing a balanced measure of the model's accuracy.
The dataset used for evaluation was pre-split, ensuring that the model's performance was thoroughly assessed on unseen data.
