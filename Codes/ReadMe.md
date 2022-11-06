## Environment setup for task 1 when using Jupyter Notebook

1) Create a conda environment with python 3.7

 conda create --name tf1 python=3.7

2) Activate the environment
 
 conda activate tf1

3) Install tensorflow 1.15

 conda install -c conda-forge tensorflow=1.15

4) Add this conda enviroment to the jupyter kernel

 pip install ipykernel

 python -m ipykernel install --user --name=tf1

The jupyter kernel might not initialize, The following two problems might be the case

 * Change tensorflow-estimator
  pip install tensorflow-estimator==1.15.0

 * Update hdf5 headers
  pip uninstall h5py
  pip install h5py

5) Install other dependencies for the project:
 * conda install pandas
 * conda install numpy
 * conda install -c anaconda scikit-learn

## Tasks descriptions

### Task 1

Initially, start by studying the Fake News Challenge Initiative and first competition FNC-1, available at Fake News Challenge. In the latter, four classes of association between title and message content of the news document have been set up: Agrees (body text agrees with headline), Disagrees (body text does not agree with headline), Discusses (body text discuss the same topic as the headline but does not take a position), Unrelated (body text discusses different topic than headline). The competition includes both a training and testing dataset. You may also notice that the top three participants used deep learning and neural network architectures and have maintained active GitHub account with all the source code made available, so that you may chose one to test and visualize the results.

### Task 2

Consider modifying the deep learning architecture (e.g., to include CNN and attention layer or any other architecture of your choice), write down the corresponding script and test it using the same dataset to record its performance in terms of accuracy levels on each of the four classes.

### Task 3

We shall consider building a simple rule-based approach that uses NLP components to assess the occurrence of any of the four classes. For this purpose, suggest a script that implements the following tasks. First, after initial preprocessing and stopword removal task, use a simple string matching to see the proportion of headline tokens which are present in the body text. We therefore assume that if this proportion is beyond certain threshold than the news can be Agrees, Disagrees or Discusses class. To find out what is the threshold value to use, you may run this reasoning on the testing dataset of the competition challenge. While, if the proportion is below the threshold, then the News is classified as “Unrelated”. Second, modify the list of stop word and preprocessing such that negation cannot be ignored (e.g., exclude words no, not, none, less, etc., from list of stop words). Suggest a script that implements this preprocessing and assumes the News to be in class Agrees if all tokens of headline are in body text; in Class Disagree if all tokens of headline are in body text and there is presence of negation in body text; Class Discusses if only part of headline token (beyond the established threshold) which are in body text. Test this heuristic on the testing dataset of Fake News Challenge and report the accuracy result for each class.

### Task 4

Now we want to modify slightly the heuristic in 3) by taking into account semantically similar wording. For this purpose, we shall consider the main part-of-speech tags in the headline. For this purpose, use part-of-speech tagger of your choice (e.g., Spacy parser) to identify the part-of-speech tags of both headline and body text document. Then write a script that uses wordnet lexical database to identify synonym of nouns (excluding named-entities), verb and adverb/adjective categories of the headline. Then modify the string matching so that a news is considered in class “Agrees” if  i) all named-entities in the headline are present in the body text, ii) for each noun, verb, adjective/adverb category of the headline, either the same token occurs in the body or its synonym word occurs in the body text, iii) there is preservation of negation (if negation is present in headline, it should be present in body text,  if headline has no negation, then body text should not contain any negation as well);  It is class “Disagrees” if the last requirement (negation preservation) is violated; It is class “Discusses” if there the proportion of matching tokens using i) and ii) is beyond the defined threshold; Otherwise, it is class “Unrelated”. Write a script to test this new heuristic and report the accuracy result of Fake News Dataset Challenge on each of the four categories.

### Task 5

We want to test the above construction on Slovak News related to Corona virus and economic related discussions. For this purpose, consider 100 News in each case (Covid-19 and economic) and manually label the dataset in one of the four categories (Agrees, Disagrees, Discusses and Unrelated) according to your understanding of the content of the article. Then create an 80%, 20%  split for training and testing, respectively.

### Task 6

First we want to test the transfer learning capability of the neural model developed in 1) and 2) to these new datasets. For this purpose run the same model on the testing data of Covid-19 and Economic and visualize the output and record the result in terms of accuracy levels of each of the four categories.

### Task 7

Retrain the models in 6) using the training data of Corona to test on Corona testing data and on Economic for testing on the corresponding testing dataset as well and record the performance for each case.

### Task 8

We also want to test the heuristic 3) and 4) on Corona and Economic dataset. Suggest a script that allows you to output the performance of class accuracy on each dataset accordingly.
