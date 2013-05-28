This package contains the scripts and various python tools for computing the semantic 
interpretability of topics via: (1) the word intrusion task; (2) PMI/NPMI/LCP-based observed 
coherence.

Directory Structure and Files
=============================
* ComputeObservedCoherence.py: computes the topic observed coherence (pairwise PMI/NPMI/LCP)
* ComputeWordCount.py: samples the word and word pair occurrences based on a reference corpus.
* ComputeWordIntrusion.py: computes the model precision of the word intrusion task.
* data: contains the input files (topics and intruder words).
* GenSVMInput.py: generates the feature file for SVM.
* ref_corpus: contains the reference corpus.
* results: contains the computed results for the topics.
* run-oc.sh: the main script for computing the observed coherence.
* run-wi.sh: the main script for running the word intrusion task.
* SplitSVM: splits the feature file generated by GenSVMInput.py to do 10-fold cross validation.
* svm_rank: contains the svm program and input feature files.
* wordcount: contains the word counts sampled by ComputeWordCount.py.

Running the System
==================
Pairwse PMI/NPMI/LCP observed coherence:
* Generate the topic file and put it in data/
* Set up the parameters in run-oc.sh
* Execute run-oc.sh

Word intrusion:
* Generate the topic file (with intruder words) and the intruder word file and put them in data/
* Set up the parameters in run-wi.sh
* Execute run-wi.sh

Input Format
============
* Topic file: one line per topic (displaying top-N words).
* Topic file with intruder word: one line per topic including the intruder word.
* Intruder word file: one line per intruder word (each line corresponds to the topic of the same
line number.

Examples are given in data/

Reference Corpus
================
Parallel processing for sampling the word counts can be achieved by splitting the reference corpus 
into multiple partitions. The format of the reference corpus is one line per document, and the words 
should be tokenised (separated by white space). Best results is achieved by lemmatising the 
reference corpus (and the document collection where the topic model is run on). An example reference 
corpus is given in the package.

Output
======
Debug OFF (in ComputeObservedCoherence.py/ComputeWordIntrusion.py):
* One score per line, each score corresponds to the topic of the same line

Debug ON (in ComputeObservedCoherence.py/ComputeWordIntrusion.py):
* Score, topics and intruder words (for the word intrusion task only) are displayed

Notes

The sampling of word counts work for multi-word topics (i.e. topics with phrases/collocations). Use 
the underscore symbol ("_") to concatenate the phrases/collocations. E.g.:
Topic 1: hello_world this_is_a_collocation apple orange banana durian

Licensing
=========
* MIT license - http://opensource.org/licenses/MIT.

Publications
------------
#### Original Paper
* David Newman, Jey Han Lau, Karl Grieser and Timothy Baldwin (2010). Automatic Evaluation of Topic
Coherence. In Proceedings of Human Language Technologies: The 11th Annual Conference of the North
American Chapter of the Association for Computational Linguistics (NAACL HLT 2010), Los Angeles,
USA, pp. 100—108.

#### Other Related Papers
* Jey Han Lau, Timothy Baldwin and David Newman (to appear). On Collocations and Topic Models. ACM 
Transactions on Speech and Language Processing.