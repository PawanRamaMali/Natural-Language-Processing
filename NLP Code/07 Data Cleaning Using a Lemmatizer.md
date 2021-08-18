# Supplemental Data Cleaning: Using a Lemmatizer

### Test out WordNet lemmatizer (read more about WordNet [here](https://wordnet.princeton.edu/))


```python
import nltk

wn = nltk.WordNetLemmatizer()
ps = nltk.PorterStemmer()
```


```python
dir(wn)
```




    ['__class__',
     '__delattr__',
     '__dict__',
     '__dir__',
     '__doc__',
     '__eq__',
     '__format__',
     '__ge__',
     '__getattribute__',
     '__gt__',
     '__hash__',
     '__init__',
     '__init_subclass__',
     '__le__',
     '__lt__',
     '__module__',
     '__ne__',
     '__new__',
     '__reduce__',
     '__reduce_ex__',
     '__repr__',
     '__setattr__',
     '__sizeof__',
     '__str__',
     '__subclasshook__',
     '__unicode__',
     '__weakref__',
     'lemmatize',
     'unicode_repr']




```python
print(ps.stem('meanness'))
print(ps.stem('meaning'))
```

    mean
    mean
    


```python
print(wn.lemmatize('meanness'))
print(wn.lemmatize('meaning'))
```

    meanness
    meaning
    


```python
print(ps.stem('goose'))
print(ps.stem('geese'))
```

    goos
    gees
    


```python
print(wn.lemmatize('goose'))
print(wn.lemmatize('geese'))
```

    goose
    goose
    

### Read in raw text


```python
import pandas as pd
import re
import string
pd.set_option('display.max_colwidth', 100)

stopwords = nltk.corpus.stopwords.words('english')

data = pd.read_csv("SMSSpamCollection.tsv", sep='\t')
data.columns = ['label', 'body_text']

data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
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
      <td>spam</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive ...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ham</td>
      <td>Nah I don't think he goes to usf, he lives around here though</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>Even my brother is not like to speak with me. They treat me like aids patent.</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ham</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL!!</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ham</td>
      <td>As per your request 'Melle Melle (Oru Minnaminunginte Nurungu Vettam)' has been set as your call...</td>
    </tr>
  </tbody>
</table>
</div>



### Clean up text


```python
def clean_text(text):
    text = "".join([word for word in text if word not in string.punctuation])
    tokens = re.split('\W+', text)
    text = [word for word in tokens if word not in stopwords]
    return text

data['body_text_nostop'] = data['body_text'].apply(lambda x: clean_text(x.lower()))

data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
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
      <td>spam</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive ...</td>
      <td>[free, entry, 2, wkly, comp, win, fa, cup, final, tkts, 21st, may, 2005, text, fa, 87121, receiv...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ham</td>
      <td>Nah I don't think he goes to usf, he lives around here though</td>
      <td>[nah, dont, think, goes, usf, lives, around, though]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>Even my brother is not like to speak with me. They treat me like aids patent.</td>
      <td>[even, brother, like, speak, treat, like, aids, patent]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ham</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL!!</td>
      <td>[date, sunday]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ham</td>
      <td>As per your request 'Melle Melle (Oru Minnaminunginte Nurungu Vettam)' has been set as your call...</td>
      <td>[per, request, melle, melle, oru, minnaminunginte, nurungu, vettam, set, callertune, callers, pr...</td>
    </tr>
  </tbody>
</table>
</div>



### Lemmatize text


```python
def lemmatizing(tokenized_text):
    text = [wn.lemmatize(word) for word in tokenized_text]
    return text

data['body_text_lemmatized'] = data['body_text_nostop'].apply(lambda x: lemmatizing(x))

data.head(10)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>label</th>
      <th>body_text</th>
      <th>body_text_nostop</th>
      <th>body_text_lemmatized</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>spam</td>
      <td>Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive ...</td>
      <td>[free, entry, 2, wkly, comp, win, fa, cup, final, tkts, 21st, may, 2005, text, fa, 87121, receiv...</td>
      <td>[free, entry, 2, wkly, comp, win, fa, cup, final, tkts, 21st, may, 2005, text, fa, 87121, receiv...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ham</td>
      <td>Nah I don't think he goes to usf, he lives around here though</td>
      <td>[nah, dont, think, goes, usf, lives, around, though]</td>
      <td>[nah, dont, think, go, usf, life, around, though]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>Even my brother is not like to speak with me. They treat me like aids patent.</td>
      <td>[even, brother, like, speak, treat, like, aids, patent]</td>
      <td>[even, brother, like, speak, treat, like, aid, patent]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ham</td>
      <td>I HAVE A DATE ON SUNDAY WITH WILL!!</td>
      <td>[date, sunday]</td>
      <td>[date, sunday]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ham</td>
      <td>As per your request 'Melle Melle (Oru Minnaminunginte Nurungu Vettam)' has been set as your call...</td>
      <td>[per, request, melle, melle, oru, minnaminunginte, nurungu, vettam, set, callertune, callers, pr...</td>
      <td>[per, request, melle, melle, oru, minnaminunginte, nurungu, vettam, set, callertune, caller, pre...</td>
    </tr>
    <tr>
      <th>5</th>
      <td>spam</td>
      <td>WINNER!! As a valued network customer you have been selected to receivea £900 prize reward! To c...</td>
      <td>[winner, valued, network, customer, selected, receivea, 900, prize, reward, claim, call, 0906170...</td>
      <td>[winner, valued, network, customer, selected, receivea, 900, prize, reward, claim, call, 0906170...</td>
    </tr>
    <tr>
      <th>6</th>
      <td>spam</td>
      <td>Had your mobile 11 months or more? U R entitled to Update to the latest colour mobiles with came...</td>
      <td>[mobile, 11, months, u, r, entitled, update, latest, colour, mobiles, camera, free, call, mobile...</td>
      <td>[mobile, 11, month, u, r, entitled, update, latest, colour, mobile, camera, free, call, mobile, ...</td>
    </tr>
    <tr>
      <th>7</th>
      <td>ham</td>
      <td>I'm gonna be home soon and i don't want to talk about this stuff anymore tonight, k? I've cried ...</td>
      <td>[im, gonna, home, soon, dont, want, talk, stuff, anymore, tonight, k, ive, cried, enough, today]</td>
      <td>[im, gonna, home, soon, dont, want, talk, stuff, anymore, tonight, k, ive, cried, enough, today]</td>
    </tr>
    <tr>
      <th>8</th>
      <td>spam</td>
      <td>SIX chances to win CASH! From 100 to 20,000 pounds txt&gt; CSH11 and send to 87575. Cost 150p/day, ...</td>
      <td>[six, chances, win, cash, 100, 20000, pounds, txt, csh11, send, 87575, cost, 150pday, 6days, 16,...</td>
      <td>[six, chance, win, cash, 100, 20000, pound, txt, csh11, send, 87575, cost, 150pday, 6days, 16, t...</td>
    </tr>
    <tr>
      <th>9</th>
      <td>spam</td>
      <td>URGENT! You have won a 1 week FREE membership in our £100,000 Prize Jackpot! Txt the word: CLAIM...</td>
      <td>[urgent, 1, week, free, membership, 100000, prize, jackpot, txt, word, claim, 81010, tc, wwwdbuk...</td>
      <td>[urgent, 1, week, free, membership, 100000, prize, jackpot, txt, word, claim, 81010, tc, wwwdbuk...</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
