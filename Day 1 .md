## Introduction to NLP :

* NLP Life cycle
* Reading text data
* Text processing
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

