# Assignment 1 - Python for Text Processing

*Submission deadline: Friday 12 March 2021, 11:55pm.*

*Assessment weight: 5% of the total unit assessment.*

## Objectives of this assignment

In this assignment you will practice with the use of Python for text processing. The assignment consists of 5 independent tasks, each of which is worth 5 marks.

**The deadline of this assignment is before census date, so that it can serve as a diagnostic test and you can determine whether you want to remain in the unit or to withdraw without academic penalty.**

You are provided with a template that contains the definitions of the functions that you need to implement in each of the tasks below. The template includes simple [Python doctests](https://docs.python.org/3/library/doctest.html) that you can use to check the correctness of the code. These tests are there to help you, but note that we will use the [unittest framework](https://docs.python.org/3/library/unittest.html) with a separate set of tests when we assess your submission. It is your responsibility to run your own tests, in addition to the doctests provided.

Each function will process a document from the NLTK Gutenberg corpus. This document is specified as an input argument to the function.

## The Tasks (1 mark each)

### 1. Find the top stems

Implement a function `get_top_stems` that returns a list with the *n* most frequent stems **which is not in the list of NLTK stopwords**. To determine whether a word is a stop word, remember to lowercase the word. The list must be sorted by frequency in descending order and the words must preserve the original casing. The input arguments of the function are:

* *document*: The name of the Gutenberg document, e.g. `"austen-emma.txt"`.
* *n*: The number of stems to return.

To produce the correct results, the function must do this:

* Use the NLTK libraries to find the tokens and the stems. 
* Use NLTK's sentence tokeniser before NLTK's word tokeniser.
* Use NLTK's list of stop words, and compare your words with those of the list after lowercasing.

### 2. Find the top PoS bigrams

Implement a function `get_top_pos_bigrams` that returns a list with the *n* most frequent bigrams of parts of speech. Do not remove stop words. The list of bigrams must be sorted by frequency in descending order. The input arguments are:

* *document*: The name of the Gutenberg document, e.g. `"austen-emma.txt"`.
* *n*: The number of bigrams to return.

To produce the correct results, the function must do this:

* Use NLTK's `pos_tag_sents` instead of `pos_tag`.
* Use NLTK's `"universal"` PoS tagset.
* When computing bigrams, do not consider parts of speech of words that are in different sentences. For example, if we have this text: "Sentence 1. And sentence 2" the bigrams are: `('NOUN','NUM'), ('NUM','.'), ('CONJ','NOUN'), ('NOUN','NUM')`. Note that this would not be a valid bigram, since the punctuation mark and the word "And" are in different sentences: `('.','CONJ')`.

### 3. Find the distribution of frequencies of parts of speech after a given word

Implement a function `get_pos_after` that returns the distribution of the parts of speech of the words that follow a word given as an input to the function. The result must be returned in descending order of frequency. The input arguments of the function are:

* *document*: The name of the Gutenberg document, e.g. `"austen-emma.txt"`.
* *word*: The word.

To produce the correct results, the function must do this:

* First do sentence tokenisation, then word tokenisation.
* Do not consider words that occur in different sentences. Thus, if a word ends a sentence, there are no words following it.

### 4. Get the words with highest tf.idf

In this exercise you will implement a simple approach to find keywords in a document.

Implement a function `get_top_word_tfidf` that returns the list of *n* words with highest tf.idf. The result must be returned in descending order of tf.idf. The input arguments are:

* *document*: The name of the Gutenberg document, e.g. `"austen-emma.txt"`.
* *n*: The number of words to return.

To produce the correct results, the function must do this:

* Use Scikit-learn's `TfidfVectorizer`.
* Fit the tf.idf vectorizer using the documents of the NLTK Gutenberg corpus.

### 5. Get the sentences with highest average of tf.idf

In this exercise you will implement a simple document summariser that returns the most important sentences based on the average tf.idf.

Implement a function `get_top_sentence_tfidf` that returns the positions of the sentences which have the largest average tf.idf. **The list of sentence positions must be returned in the order of occurrence in the document**. The input arguments are:

* *document*: The name of the Gutenberg document, e.g. `"austen-emma.txt"`.
* *n*: The number of sentence positions to return.

The reason for returning the sentence positions in the order of occurrence, and not in order of average tf.idf, is that this is what document summarisers normally do.

To produce the correct results, the function must do this:

* Use Scikit-learn's `TfidfVectorizer`.
* Fit the tfidf vectorizer using the sentences of the documents of the NLTK Gutenberg corpus. This is different from task 4. Now you want to compute the tf.idf of sentences, not of documents. 
* Use NLTK's sentence tokeniser to find the sentences.


## Submission

The submission must be a single Python file. Do not submit several files or a zip file since the automarker would not know what to do with your submission. Do not submit a Jupyter notebook.

Note that the deadline is a hard deadline and there will be a penalty for late submission as specified in the unit guide (0.5 marks per day late or part thereof). In addition, since the submission date is very near the census date of 18 of March 2021, late submissions might not be assessed before census date.

Finally, note that **the work submitted should be your own work**. You may be tempted to search the Web for Python implementations of the questions asked in this tutorial. Be aware that:

1. If we find out that your work is copied from the Web or from other submissions, you may face disciplinary action.
2. Often, trying to adapt work from the web may be more difficult than when you try from scratch.
3. The work you find on the web may be wrong or not do exactly what is asked in this assignment.

