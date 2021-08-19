# NLP Basics: Implementing a pipeline to clean text

### Pre-processing text data

Cleaning up the text data is necessary to highlight attributes that you're going to want your machine learning system to pick up on. Cleaning (or pre-processing) the data typically consists of a number of steps:
1. **Remove punctuation**
2. **Tokenization**
3. **Remove stopwords**
4. Lemmatize/Stem

The first three steps are covered in this chapter as they're implemented in pretty much any text cleaning pipeline. Lemmatizing and stemming are covered in the next chapter as they're helpful but not critical.


```python
import pandas as pd
pd.set_option('display.max_colwidth', 100)

data = pd.read_csv("SMSSpamCollection.tsv", sep='\t', header=None)
data.columns = ['label', 'body_text']

data.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>label</th>
      <th>body_text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ham</td>
      <td>I've been searching for the right words to thank you for this breather. I promise i wont take yo...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>spam</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive ...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>Nah I don't think he goes to usf, he lives around here though</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ham</td>
      <td>Even my brother is not like to speak with me. They treat me like aids patent.</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ham</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL!!</td>
    </tr>
  </tbody>
</table>
</div>




```python
# What does the cleaned version look like?
data_cleaned = pd.read_csv("SMSSpamCollection_cleaned.tsv", sep='\t')
data_cleaned.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>label</th>
      <th>body_text</th>
      <th>body_text_nostop</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ham</td>
      <td>I've been searching for the right words to thank you for this breather. I promise i wont take yo...</td>
      <td>['ive', 'searching', 'right', 'words', 'thank', 'breather', 'promise', 'wont', 'take', 'help', '...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>spam</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive ...</td>
      <td>['free', 'entry', '2', 'wkly', 'comp', 'win', 'fa', 'cup', 'final', 'tkts', '21st', 'may', '2005...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>Nah I don't think he goes to usf, he lives around here though</td>
      <td>['nah', 'dont', 'think', 'goes', 'usf', 'lives', 'around', 'though']</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ham</td>
      <td>Even my brother is not like to speak with me. They treat me like aids patent.</td>
      <td>['even', 'brother', 'like', 'speak', 'treat', 'like', 'aids', 'patent']</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ham</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL!!</td>
      <td>['date', 'sunday']</td>
    </tr>
  </tbody>
</table>
</div>



### Remove punctuation


```python
import string
string.punctuation
```




    '!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'




```python
"I like NLP." == "I like NLP"
```




    False




```python
def remove_punct(text):
    text_nopunct = "".join([char for char in text if char not in string.punctuation])
    return text_nopunct

data['body_text_clean'] = data['body_text'].apply(lambda x: remove_punct(x))

data.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>label</th>
      <th>body_text</th>
      <th>body_text_clean</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ham</td>
      <td>I've been searching for the right words to thank you for this breather. I promise i wont take yo...</td>
      <td>Ive been searching for the right words to thank you for this breather I promise i wont take your...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>spam</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive ...</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005 Text FA to 87121 to receive e...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>Nah I don't think he goes to usf, he lives around here though</td>
      <td>Nah I dont think he goes to usf he lives around here though</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ham</td>
      <td>Even my brother is not like to speak with me. They treat me like aids patent.</td>
      <td>Even my brother is not like to speak with me They treat me like aids patent</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ham</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL!!</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL</td>
    </tr>
  </tbody>
</table>
</div>



### Tokenization


```python
import re

def tokenize(text):
    tokens = re.split('\W+', text)
    return tokens

data['body_text_tokenized'] = data['body_text_clean'].apply(lambda x: tokenize(x.lower()))

data.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>label</th>
      <th>body_text</th>
      <th>body_text_clean</th>
      <th>body_text_tokenized</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ham</td>
      <td>I've been searching for the right words to thank you for this breather. I promise i wont take yo...</td>
      <td>Ive been searching for the right words to thank you for this breather I promise i wont take your...</td>
      <td>[ive, been, searching, for, the, right, words, to, thank, you, for, this, breather, i, promise, ...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>spam</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive ...</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005 Text FA to 87121 to receive e...</td>
      <td>[free, entry, in, 2, a, wkly, comp, to, win, fa, cup, final, tkts, 21st, may, 2005, text, fa, to...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>Nah I don't think he goes to usf, he lives around here though</td>
      <td>Nah I dont think he goes to usf he lives around here though</td>
      <td>[nah, i, dont, think, he, goes, to, usf, he, lives, around, here, though]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ham</td>
      <td>Even my brother is not like to speak with me. They treat me like aids patent.</td>
      <td>Even my brother is not like to speak with me They treat me like aids patent</td>
      <td>[even, my, brother, is, not, like, to, speak, with, me, they, treat, me, like, aids, patent]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ham</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL!!</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL</td>
      <td>[i, have, a, date, on, sunday, with, will]</td>
    </tr>
  </tbody>
</table>
</div>




```python
'NLP' == 'nlp'
```




    False



### Remove stopwords


```python
import nltk

stopword = nltk.corpus.stopwords.words('english')
```


```python
def remove_stopwords(tokenized_list):
    text = [word for word in tokenized_list if word not in stopword]
    return text

data['body_text_nostop'] = data['body_text_tokenized'].apply(lambda x: remove_stopwords(x))

data.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>label</th>
      <th>body_text</th>
      <th>body_text_clean</th>
      <th>body_text_tokenized</th>
      <th>body_text_nostop</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ham</td>
      <td>I've been searching for the right words to thank you for this breather. I promise i wont take yo...</td>
      <td>Ive been searching for the right words to thank you for this breather I promise i wont take your...</td>
      <td>[ive, been, searching, for, the, right, words, to, thank, you, for, this, breather, i, promise, ...</td>
      <td>[ive, searching, right, words, thank, breather, promise, wont, take, help, granted, fulfil, prom...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>spam</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive ...</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005 Text FA to 87121 to receive e...</td>
      <td>[free, entry, in, 2, a, wkly, comp, to, win, fa, cup, final, tkts, 21st, may, 2005, text, fa, to...</td>
      <td>[free, entry, 2, wkly, comp, win, fa, cup, final, tkts, 21st, may, 2005, text, fa, 87121, receiv...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>Nah I don't think he goes to usf, he lives around here though</td>
      <td>Nah I dont think he goes to usf he lives around here though</td>
      <td>[nah, i, dont, think, he, goes, to, usf, he, lives, around, here, though]</td>
      <td>[nah, dont, think, goes, usf, lives, around, though]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ham</td>
      <td>Even my brother is not like to speak with me. They treat me like aids patent.</td>
      <td>Even my brother is not like to speak with me They treat me like aids patent</td>
      <td>[even, my, brother, is, not, like, to, speak, with, me, they, treat, me, like, aids, patent]</td>
      <td>[even, brother, like, speak, treat, like, aids, patent]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ham</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL!!</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL</td>
      <td>[i, have, a, date, on, sunday, with, will]</td>
      <td>[date, sunday]</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
