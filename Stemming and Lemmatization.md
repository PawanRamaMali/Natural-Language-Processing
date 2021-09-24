

Stemming and Lemmatization in Python NLTK are text normalization techniques for Natural Language Processing. These techniques are widely used for text preprocessing. The difference between stemming and lemmatization is that stemming is faster as it cuts words without knowing the context, while lemmatization is slower as it knows the context of words before processing.

### What is Stemming?

Stemming is a method of normalization of words in Natural Language Processing. It is a technique in which a set of words in a sentence are converted into a sequence to shorten its lookup. In this method, the words having the same meaning but have some variations according to the context or sentence are normalized.

In another word, there is one root word, but there are many variations of the same words. For example, the root word is “eat” and it’s variations are “eats, eating, eaten and like so”. In the same way, with the help of Stemming in Python, we can find the root word of any variations.

For example
```
He was riding.	
He was taking the ride.
```

In the above two sentences, the meaning is the same, i.e., riding activity in the past. A human can easily understand that both meanings are the same. But for machines, both sentences are different. Thus it became hard to convert it into the same data row. In case we do not provide the same data-set, then machine fails to predict. So it is necessary to differentiate the meaning of each word to prepare the dataset for machine learning. And here stemming is used to categorize the same type of data by getting its root word.

Let’s implement this with a Python program.NLTK has an algorithm named as “PorterStemmer”. This algorithm accepts the list of tokenized word and stems it into root word.

### Program for understanding Stemming

```
from nltk.stem import PorterStemmer
e_words= ["wait", "waiting", "waited", "waits"]
ps =PorterStemmer()
for w in e_words:
    rootWord=ps.stem(w)
    print(rootWord)
```

Output
```
wait	
wait	
wait	
wait 
```
