## Introduction to NLP :

* NLP Life cycle
* Reading text data
* Text processing

  * There are two main phases to natural language processing: data preprocessing and algorithm development.
    *  Data preprocessing involves preparing and "cleaning" text data for machines to be able to analyze it. 
    *  Preprocessing puts data in workable form and highlights features in the text that an algorithm can work with.

  * Tokenization - This is when text is broken down into smaller units to work with.
  * Stop word removal - This is when common words are removed from text so unique words that offer the most information about the text remain.
  * Lemmatization and stemming - This is when words are reduced to their root forms to process.
  * Part-of-speech tagging - This is when words are marked based on the part-of speech they are -- such as nouns, verbs and adjectives.

Once the data has been preprocessed, an algorithm is developed to process it. There are many different natural language processing algorithms, but two main types are commonly used:

  * Rules-based system. 
   * This system uses carefully designed linguistic rules. 
   * This approach was used early on in the development of natural language processing, and is still used.

 * Machine learning-based system. 
   * Machine learning algorithms use statistical methods. 
   * They learn to perform tasks based on training data they are fed, and adjust their methods as more data is processed. 
   * Using a combination of machine learning, deep learning and neural networks, natural language processing algorithms hone their own rules through repeated processing and learning.


* Text to features
* Text exploration

## NLP applications:

* Noun Phrase extraction

```Python
import nltk

lines = 'lines is some string of words'
# function to test if something is a noun
is_noun = lambda pos: pos[:2] == 'NN'
# do the nlp stuff
tokenized = nltk.word_tokenize(lines)
nouns = [word for (word, pos) in nltk.pos_tag(tokenized) if is_noun(pos)] 

print nouns
>>> ['lines', 'string', 'words']

```

* Text similarity
* Parts of speech tagging
* Information extraction NER – Entity recognition
* Topic modelling
* Sentiment analysis
* Word sense disambiguation


