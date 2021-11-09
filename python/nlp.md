---
description: I'm So Meta Even This Acronym
---

To get to a useful word bag, there are three-ish steps for standard English NLP:

> Noise Removal > Tokenization > Normalization

* Noise Removal is the removal of punctuation, html tags, upper case, and anything else cluttering up words
* Tokenization is turning a line of words into ["line", "of", "words"]
* Normalization, which includes Stemming and Lemmatization, is adjusting the words to fit into similar buckets, i.e. "bucket" and "buckets" should both go in the same bucket

Further reading available in the [doc](https://www.nltk.org/book/ch03.html).


### Noise Removal

This is... hilariously boring, and will take a lot of Regex.  A ton of NLP data engineering is just sorting through this noise removal process.

Gratefully, the syntax is easy, but the monotony and tweaking is what makes this tricky.

```python
import re 

tweet = '@fat_meats, veggies are better than you think.'
tweet_no_at = re.sub(r'@', '', tweet)
# Returns tweet without @ symbols
```

Getting rid of cases is easy, and you can read more about this in the string-hangling doc.  But for ease of use...

```python
brands = 'Salvation Army, YMCA, Boys & Girls Club of America'

brands_lower = brands.lower()
brands_upper = brands.upper()
```



### Tokenization

Tokenization is a simpler step.  However, this comes with the decision point whether the base grain of the analysis should be by the word (`word_tokenize()`) or by the sentence (`sent_tokenize()`).

```python
from nltk.tokenize import word_tokenize
from nltk.tokenize import sent_tokenize

ecg_text = 'An electrocardiogram is used to record the electrical conduction through a person\'s heart. The readings can be used to diagnose cardiac arrhythmias.'

tokenized_by_word = word_tokenize(ecg_text)
tokenized_by_sentence = sent_tokenize(ecg_text)
```

Stop Words are words that, generally, no one cares about in NLP.  Words like "the" or "at" are useful for the sake of syntax, but not for analysis (unless you really want to analyze syntax, but that's not a normal use case).

Gratefully, instead of tracking down all of these things and then loading the same reference set each project, `nltk` has a library for this.

```python
from nltk.corpus import stopwords 
stop_words = set(stopwords.words('english')) 
# this dude right here is how to get a list of stop words

nbc_statement = "NBC was founded in 1926 making it the oldest major broadcast network in the USA"
 
word_tokens = word_tokenize(nbc_statement) 
# tokenize nbc_statement
 
statement_no_stop = [word for word in word_tokens if word not in stop_words]
# creates a new list of words without the stop words list loaded from above
```

Removing stop words isn't quite normalization, and not quite tokenization, but shoving it in this category seems to be the best solution.


### Normalization

First, some definitions:

* Stemming is removing the prefixes or suffixes from a word so it goes in the bucket easier
* Lemmatization is replacing a single word with its root word ()

Stemming can be more efficient because it doesn't need the part-of-speech for a word, where lemmatization really does to work well.


#### Stemming

YAY BUILT-IN PACKAGES, YOU ARE MY FRIEND (AFTER YOU ARE INITIALIZED)
That said, when you convert "was" to "wa", that's not as helpful.

```python
from nltk.stem import PorterStemmer
stemmer = PorterStemmer()

populated_island = 'Java is an Indonesian island in the Pacific Ocean. It is the most populated island in the world, with over 140 million people.'

island_tokenized = word_tokenize(populated_island)

stemmed = [stemmer.stem(word) for word in island_tokenized]
```


#### Lemmatization

This is both more and less helpful than stemming.  On the plus side, it can get to cleaner data.  On the down side, unless each word has the part-of-speech confirmed, the Lemmatizer is going to mess up a lot of words.

```python
from nltk.tokenize import word_tokenize
from nltk.stem import WordNetLemmatizer

populated_island = 'Indonesia was founded in 1945. It contains the most populated island in the world, Java, with over 140 million people.'

lemmatizer = WordNetLemmatizer()

tokenized_string = word_tokenize(populated_island)
lemmatized_words = [lemmatizer.lemmatize(word) for word in tokenized_string]

print(lemmatized_words)
# Output:
# Lemmatized Words: ['Indonesia', 'wa', 'founded', 'in', '1945', '.', 'It', 'contains', 'the', 'most', 'populated', 'island', 'in', 'the', 'world', ',', 'Java', ',', 'with', 'over', '140', 'million', 'people', '.']
# 'wa' isn't a word, but 'was' was, before Lemma ate it
```

You can fix this hiccup by comparing each tokenized word of the string to a thesaurus, then returning the part of speech of the closest word in the thesaurus and passing the part of speech to the lemmatizer.  

Also worth noting is that NLTK has multiple word lemmatizers, and poking about a bit for a more appropriate one may help a project significantly.




