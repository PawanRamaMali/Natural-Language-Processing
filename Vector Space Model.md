## Vector Space Model

Vector space model is a statistical model for representing text information for Information Retrieval, NLP, Text Mining

Representing documents in VSM is called "vectorizing text"
contains the following information: how many documents contain a term, and what are important terms each document has


### From Text to Vectors: NLP Pipeline

How do we represent a free text in terms of queries?

* to do we need some preprocessing steps, often called "NLP Pipeline"
* the pipeline may include the following:
* Tokenization - most important step, extracts individual words - "tokens"
* Stop Words Removal - removes functional words
* Stemming or Lemmatization - reduces words to some common form
* or other Text Normalization techniques
* building a VSM model is usually one of the lasts steps of the pipeline
* for IR we also usually build an Inverted Index to speed up querying

### Bag of Words Assumption

The main assumptions we're making about text data:

* word order is not important, only word counts
* Bag of Words = unordered list of terms
* good enough for topic similarity

### Independence Assumption

We treat all words as independent

i.e. the basis vector of the term space (see below) is orthogonal

