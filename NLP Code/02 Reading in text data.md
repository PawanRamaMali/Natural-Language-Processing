# NLP Basics: Reading in text data & why do we need to clean the text?

### Read in semi-structured text data


```python
# Read in the raw text
rawData = open("SMSSpamCollection.tsv").read()

# Print the raw data
rawData[0:500]
```




    "ham\tI've been searching for the right words to thank you for this breather. I promise i wont take your help for granted and will fulfil my promise. You have been wonderful and a blessing at all times.\nspam\tFree entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive entry question(std txt rate)T&C's apply 08452810075over18's\nham\tNah I don't think he goes to usf, he lives around here though\nham\tEven my brother is not like to speak with me. They treat me like aid"




```python
parsedData = rawData.replace('\t', '\n').split('\n')
```


```python
parsedData[0:5]
```




    ['ham',
     "I've been searching for the right words to thank you for this breather. I promise i wont take your help for granted and will fulfil my promise. You have been wonderful and a blessing at all times.",
     'spam',
     "Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive entry question(std txt rate)T&C's apply 08452810075over18's",
     'ham']




```python
labelList = parsedData[0::2]
textList = parsedData[1::2]
```


```python
print(labelList[0:5])
print(textList[0:5])
```

    ['ham', 'spam', 'ham', 'ham', 'ham']
    ["I've been searching for the right words to thank you for this breather. I promise i wont take your help for granted and will fulfil my promise. You have been wonderful and a blessing at all times.", "Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive entry question(std txt rate)T&C's apply 08452810075over18's", "Nah I don't think he goes to usf, he lives around here though", 'Even my brother is not like to speak with me. They treat me like aids patent.', 'I HAVE A DATE ON SUNDAY WITH WILL!!']
    


```python
import pandas as pd

fullCorpus = pd.DataFrame({
    'label': labelList,
    'body_list': textList
})

fullCorpus.head()
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-27-25797b4f5cf0> in <module>()
          3 fullCorpus = pd.DataFrame({
          4     'label': labelList,
    ----> 5     'body_list': textList
          6 })
          7 
    

    ~/anaconda3/lib/python3.6/site-packages/pandas/core/frame.py in __init__(self, data, index, columns, dtype, copy)
        273                                  dtype=dtype, copy=copy)
        274         elif isinstance(data, dict):
    --> 275             mgr = self._init_dict(data, index, columns, dtype=dtype)
        276         elif isinstance(data, ma.MaskedArray):
        277             import numpy.ma.mrecords as mrecords
    

    ~/anaconda3/lib/python3.6/site-packages/pandas/core/frame.py in _init_dict(self, data, index, columns, dtype)
        409             arrays = [data[k] for k in keys]
        410 
    --> 411         return _arrays_to_mgr(arrays, data_names, index, columns, dtype=dtype)
        412 
        413     def _init_ndarray(self, values, index, columns, dtype=None, copy=False):
    

    ~/anaconda3/lib/python3.6/site-packages/pandas/core/frame.py in _arrays_to_mgr(arrays, arr_names, index, columns, dtype)
       5494     # figure out the index, if necessary
       5495     if index is None:
    -> 5496         index = extract_index(arrays)
       5497     else:
       5498         index = _ensure_index(index)
    

    ~/anaconda3/lib/python3.6/site-packages/pandas/core/frame.py in extract_index(data)
       5542             lengths = list(set(raw_lengths))
       5543             if len(lengths) > 1:
    -> 5544                 raise ValueError('arrays must all be same length')
       5545 
       5546             if have_dicts:
    

    ValueError: arrays must all be same length



```python
print(len(labelList))
print(len(textList))
```

    5571
    5570
    


```python
print(labelList[-5:])
```

    ['ham', 'ham', 'ham', 'ham', '']
    


```python
fullCorpus = pd.DataFrame({
    'label': labelList[:-1],
    'body_list': textList
})

fullCorpus.head()
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
      <th>body_list</th>
      <th>label</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>I've been searching for the right words to tha...</td>
      <td>ham</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Free entry in 2 a wkly comp to win FA Cup fina...</td>
      <td>spam</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nah I don't think he goes to usf, he lives aro...</td>
      <td>ham</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Even my brother is not like to speak with me. ...</td>
      <td>ham</td>
    </tr>
    <tr>
      <th>4</th>
      <td>I HAVE A DATE ON SUNDAY WITH WILL!!</td>
      <td>ham</td>
    </tr>
  </tbody>
</table>
</div>




```python
dataset = pd.read_csv("SMSSpamCollection.tsv", sep="\t", header=None)
dataset.head()
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
      <th>0</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ham</td>
      <td>I've been searching for the right words to tha...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>spam</td>
      <td>Free entry in 2 a wkly comp to win FA Cup fina...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>Nah I don't think he goes to usf, he lives aro...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ham</td>
      <td>Even my brother is not like to speak with me. ...</td>
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

```
