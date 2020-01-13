## GloVe: Global Vectors for Word Representation

Repository forked from [Stanford's one](https://github.com/stanfordnlp/GloVe).
Changes were made to make it simpler to train GloVe embeddings on Wikipedia data.

### Getting the embeddings

First, make sure you have both `gensim` and `spacy` installed in your python environment.

The file `MakeWiki` and `src/tokenizer.py` were added to simplify the embedding training process.
To create glove embeddings for a language use the command:
```bash
$ make -f MakeWiki LANGUAGE=<language>
```
In this command, `<language>` can be any language in Wikipedia for which [spacy's tokenizer](https://spacy.io/api/tokenizer) works.
For example, training Portuguese embeddings is done by running:
```bash
$ make -f MakeWiki LANGUAGE=pt
```

This command will download the latest wikipedia data for that language, tokenize it and then train GloVe embeddings on it.
Vectors will be saved in path `results/<language>/vectors.bin`.


## Original README:


| nearest neighbors of <br/> <em>frog</em> | Litoria             |  Leptodactylidae | Rana | Eleutherodactylus |
| --- | ------------------------------- | ------------------- | ---------------- | ------------------- |
| Pictures | <img src="http://nlp.stanford.edu/projects/glove/images/litoria.jpg"></img> | <img src="http://nlp.stanford.edu/projects/glove/images/leptodactylidae.jpg"></img> | <img src="http://nlp.stanford.edu/projects/glove/images/rana.jpg"></img> | <img src="http://nlp.stanford.edu/projects/glove/images/eleutherodactylus.jpg"></img> |

| Comparisons | man -> woman             |  city -> zip | comparative -> superlative |
| --- | ------------------------|-------------------------|-------------------------|
| GloVe Geometry | <img src="http://nlp.stanford.edu/projects/glove/images/man_woman_small.jpg"></img>  | <img src="http://nlp.stanford.edu/projects/glove/images/city_zip_small.jpg"></img> | <img src="http://nlp.stanford.edu/projects/glove/images/comparative_superlative_small.jpg"></img> |

We provide an implementation of the GloVe model for learning word representations, and describe how to download web-dataset vectors or train your own. See the [project page](http://nlp.stanford.edu/projects/glove/) or the [paper](http://nlp.stanford.edu/pubs/glove.pdf) for more information on glove vectors.

## Download pre-trained word vectors
The links below contain word vectors obtained from the respective corpora. If you want word vectors trained on massive web datasets, you need only download one of these text files! Pre-trained word vectors are made available under the <a href="http://opendatacommons.org/licenses/pddl/">Public Domain Dedication and License</a>.
<div class="entry">
<ul style="padding-left:0px; margin-top:0px; margin-bottom:0px">
  <li> Common Crawl (42B tokens, 1.9M vocab, uncased, 300d vectors, 1.75 GB download): <a href="http://nlp.stanford.edu/data/wordvecs/glove.42B.300d.zip">glove.42B.300d.zip</a> </li>
  <li> Common Crawl (840B tokens, 2.2M vocab, cased, 300d vectors, 2.03 GB download): <a href="http://nlp.stanford.edu/data/wordvecs/glove.840B.300d.zip">glove.840B.300d.zip</a> </li>
  <li> Wikipedia 2014 + Gigaword 5 (6B tokens, 400K vocab, uncased, 300d vectors, 822 MB download): <a href="http://nlp.stanford.edu/data/wordvecs/glove.6B.zip">glove.6B.zip</a> </li>
  <li> Twitter (2B tweets, 27B tokens, 1.2M vocab, uncased, 200d vectors, 1.42 GB download): <a href="http://nlp.stanford.edu/data/wordvecs/glove.twitter.27B.zip">glove.twitter.27B.zip</a>
</ul>
</div>

## Train word vectors on a new corpus

<img src="https://travis-ci.org/stanfordnlp/GloVe.svg?branch=master"></img>

If the web datasets above don't match the semantics of your end use case, you can train word vectors on your own corpus.

    $ git clone http://github.com/stanfordnlp/glove
    $ cd glove && make
    $ ./demo.sh

The demo.sh script downloads a small corpus, consisting of the first 100M characters of Wikipedia. It collects unigram counts, constructs and shuffles cooccurrence data, and trains a simple version of the GloVe model. It also runs a word analogy evaluation script in python to verify word vector quality. More details about training on your own corpus can be found by reading [demo.sh](https://github.com/stanfordnlp/GloVe/blob/master/demo.sh) or the [src/README.md](https://github.com/stanfordnlp/GloVe/tree/master/src)

### License
All work contained in this package is licensed under the Apache License, Version 2.0. See the include LICENSE file.
