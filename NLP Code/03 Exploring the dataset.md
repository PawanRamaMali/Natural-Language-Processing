## NLP : Exploring the dataset

### Read in text data


```python
import pandas as pd

fullCorpus = pd.read_csv('SMSSpamCollection.tsv', sep='\t', header=None)
fullCorpus.columns = ['label','body_text']
fullCorpus.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
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



### Explore the dataset


```python
# What is the shape of the dataset?
print("Input data has {} rows and {} columns".format(len(fullCorpus), len(fullCorpus.columns)))
```

    Input data has 5568 rows and 2 columns
    


```python
# How many spam/ham are there?
print("Out of {} rows, {} are spam, {} are ham".format(len(fullCorpus),
                                                       len(fullCorpus[fullCorpus['label']=='spam']),
                                                       len(fullCorpus[fullCorpus['label']=='ham'])))
```

    Out of 5568 rows, 746 are spam, 4822 are ham
    


```python
# How much missing data is there?
print("Number of null in label : {}".format(fullCorpus['label'].isnull().sum()))
print("Number of null in label : {}".format(fullCorpus['body_text'].isnull().sum()))
```

    Number of null in label : 0
    Number of null in label : 0
    


```python

```
