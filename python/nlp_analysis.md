---
description: Understanding words without reading
---

Note to Future Self: I'm a little tired, but I'm trying to sketch out some notes that can be cleaned up later.


## The Bag of Words

The basic here for a bag of words (BOW) is to have a dictionary of unique words as keys with values of the sum number of those words in the intended text.

```python
from preprocessing import preprocess_text
# Define text_to_bow() below:

def text_to_bow(some_text):
  bow_dictionary = {}
  tokens = preprocess_text(some_text)
  for token in tokens:
    if token in bow_dictionary:
      bow_dictionary[token] += 1
    else:
      bow_dictionary[token] = 1

  return bow_dictionary
 ```

 That... basicallly is it to get to the data set, besides all the preprocessing.