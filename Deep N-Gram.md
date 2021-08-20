
# Importing Packages

In this notebook we will use the following packages:

Pandas is a fast, powerful, flexible and easy to use open-source data analysis and manipulation tool, built on top of the Python programming language. It offers a fast and efficient DataFrame object for data manipulation with integrated indexing.
os module provides a portable way of using operating system dependent functionality.
trax is an end-to-end library for deep learning that focuses on clear code and speed.
random module implements pseudo-random number generators for various distributions.
itertools module implements a number of iterator building blocks inspired by constructs from APL, Haskell, and SML. Each has been recast in a form suitable for Python.

```

import pandas as pd 
import os
import trax
import trax.fastmath.numpy as np
import random as rnd
from trax import fastmath
from trax import layers as tl
```


# Loading the Data

For this project, I've used the gothic-literature, shakespeare-plays and shakespeareonline datasets from the Kaggle library.

We perform the following steps for loading in the data:

Iterate over all the directories in the /kaggle/input/ directory
Filter out .txt files
Make a lines list containing the individual lines from all the datasets combined

```
directories = os.listdir('/kaggle/input/')
lines = []
for directory in directories:
    for filename in os.listdir(os.path.join('/kaggle/input',directory)):
        if filename.endswith(".txt"):
            with open(os.path.join(os.path.join('/kaggle/input',directory), filename)) as files:
                for line in files: 
                    processed_line = line.strip()
                    if processed_line:
                        lines.append(processed_line)
                       
```

# Pre-Processing

## Converting to Lowercase

Converting all the characters in the lines list to lowercase.

```
for i, line in enumerate(lines):
    lines[i] = line.lower()
```

## Converting into Tensors

Creating a function to convert each line into a tensor by converting each character into it's ASCII value. And adding a optional EOS(End of statement) character.

```
def line_to_tensor(line, EOS_int=1):
    
    tensor = []
    for c in line:
        c_int = ord(c)
        tensor.append(c_int)
    
    tensor.append(EOS_int)

    return tensor
```

## Creating a Batch Generator

Here, we create a batch_generator() function to yield a batch and mask generator. We perform the following steps:

* Shuffle the lines if not shuffled
* Convert the lines into a Tensor
* Pad the lines if it's less than the maximum length
* Generate a mask

```

def data_generator(batch_size, max_length, data_lines, line_to_tensor=line_to_tensor, shuffle=True):
    
    index = 0                         
    cur_batch = []                    
    num_lines = len(data_lines)       
    lines_index = [*range(num_lines)] 

    if shuffle:
        rnd.shuffle(lines_index)
    
    while True:
        
        if index >= num_lines:
            index = 0
            if shuffle:
                rnd.shuffle(lines_index)
            
        line = data_lines[lines_index[index]] 
        
        if len(line) < max_length:
            cur_batch.append(line)
            
        index += 1
        
        if len(cur_batch) == batch_size:
            
            batch = []
            mask = []
            
            for li in cur_batch:

                tensor = line_to_tensor(li)

                pad = [0] * (max_length - len(tensor))
                tensor_pad = tensor + pad
                batch.append(tensor_pad)

                example_mask = [0 if t == 0 else 1 for t in tensor_pad]
                mask.append(example_mask)
               
            batch_np_arr = np.array(batch)
            mask_np_arr = np.array(mask)
            
            
            yield batch_np_arr, batch_np_arr, mask_np_arr
            
            cur_batch = []
```

# Defining the Model

## Gated Recurrent Unit

This function generates a GRU Language Model, consisting of the following layers:

* ShiftRight()
* Embedding()
* GRU Units(Number specified by the n_layers parameter)
* Dense() Layer
* LogSoftmax() Activation

```
def GRULM(vocab_size=256, d_model=512, n_layers=2, mode='train'):
    model = tl.Serial(
      tl.ShiftRight(mode=mode),                                 
      tl.Embedding( vocab_size = vocab_size, d_feature = d_model), 
      [tl.GRU(n_units=d_model) for _ in range(n_layers)], 
      tl.Dense(n_units = vocab_size), 
      tl.LogSoftmax() 
    )
    return model
```


# Long Short Term Memory

This function generates a LSTM Language Model, consisting of the following layers:

ShiftRight()
Embedding()
LSTM Units(Number specified by the n_layers parameter)
Dense() Layer
LogSoftmax() Activation

```
def LSTMLM(vocab_size=256, d_model=512, n_layers=2, mode='train'):
    model = tl.Serial(
      tl.ShiftRight(mode=mode),                                 
      tl.Embedding( vocab_size = vocab_size, d_feature = d_model), 
      [tl.LSTM(n_units=d_model) for _ in range(n_layers)], 
      tl.Dense(n_units = vocab_size), 
      tl.LogSoftmax() 
    )
    return model
```
