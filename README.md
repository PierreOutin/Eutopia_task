## Why Bert Tokenizer :

- Bert : Bidirectional Encoder Representations with Transformers
- Bert predict a token by paying "attention" to every other token in the sequence.
- We used a pre-trained model with transfer learning, train with a large pool of documents
- Bert Tokenizer have good result on text classification

## Dataset :

 - crunchbase_ID : Id of each website
 - home_text : home page text 
 - aboutus_text : about us page text
 - overview_text : overview page text
 - whatwedo_text : what we do page text
 - company_text : company page text
 - whoweare_text : who we are page text
 - AI : 0 or 1, absence or presence of AI in website text
 
## Data Cleaning :

 - Fill with empty string all NA values from all text except home_text
 - Merge all text column into a single one

## Data preparation : 

 - Import stopwords and lemmatizer from nltk
 - Split text into list of words
 - Remove stopwords and punctuation from list of words
 - Remove digit
 - Lemmatize each word, reduce the different forms of a word to one single form
 - Remove all words who appears only one time

## Word Embedding :

 - Join all words from list
 - Tokenize all text with Bert Tokenizer
 - Convert tokens to ID
 - Creating list of lists with tokens ID , label and length of each text
 - Sort data by length of each text
 - Convert the sorted dataset into a TensorFlow input dataset shape
 - Pad our dataset for each Batch

## Splitting Data :

- We took 10% of data into test set

## Creating Model :

- We initialize some attributes with default values
- We initialize three convolutional neural network layers with filter values
- With call function, global max pooling is applied to the output of each of the convolutional neural network layer.
- The first densely connected neural network is concatenation of the three convolutional neural network layers
- The second densely connected neural network is used to predict if text contains AI.

## Fitting model :
- We pass the hyper parameters values that we defined in the last step to the constructor of the TEXT_MODEL class like embedding dimension of 200.
- We use fit method to train our model for 10 epoch 

## Results :
- Accuracy of 99.98% on the training set
- Accuracy of 86.04% on the training set

## Conclusion :

- We can use BERT Tokenizer to create word embeddings that can be used to perform text classification.
- In our case, we performed AI analysis of website text and achieved an accuracy of 86.04% on the test set.
- I think it's can have better results for small or medium text, but for website page, Bert Tokenizer will take only the 512 first words/tokens and will trim the rest of the text.
