
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
