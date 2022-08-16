# Google Summer of Code 2022

![ViewCount](https://views.whatilearened.today/views/github/its-sushant/GSoC-22.svg)
![GitHub](https://img.shields.io/github/followers/its-sushant?style=social)
![GSoC @ FOSSology](/static/gsocHeader.png)

<div align = "center"><h2>Improve Minerva OSS Dataset and implement models for Atarashi</h2></div>

## PROJECT OVERVIEW

In GSoC 2021 [Minerva Dataset](https://github.com/fossology/Minerva-Dataset-Generation) was created to train machine learning
model for predicting license shortname for [Atarashi](https://github.com/fossology/atarashi). Currently [Atarashi](https://github.com/fossology/atarashi) has four active agents for predicting license statement from the source code. And the highest accuracy we are getting right now is **62%**, which is from [tfidf](https://github.com/fossology/atarashi/blob/master/atarashi/agents/tfidf.py) agent. This summer I have trained few machine/deep learning models
on [Minerva Dataset](https://github.com/fossology/Minerva-Dataset-Generation) and created agents for the trained model. And currently I am getting the highest accuray for **63%** from both [LogisticRegression](https://github.com/fossology/atarashi/pull/102) and [Linearsvc](https://github.com/fossology/atarashi/pull/100) agents that I have implemented.

<h2>CONTRIBUTIONS <img src="https://media.giphy.com/media/dxn6fRlTIShoeBr69N/giphy.gif" width="15"></h2>

### 1. Atarashi agent based on Logistic regression.

To create an agent on [Atarashi](https://github.com/fossology/atarashi) for logistic regression model trained on [Minerva Dataset](https://github.com/fossology/Minerva-Dataset-Generation). Training of dataset is done on [kaggle notebook](https://www.kaggle.com/code/sushanttkr07/logistic).

#### Results:

Below given is the accuracy score for the agent created on atarashi. The accuracy we are getting is from
[evaluator.py](https://github.com/fossology/atarashi/blob/master/atarashi/evaluator/evaluator.py).

- Accuracy of agent

```
 Total files scanned = 100
 Successfully matched = 63

      ++++++++++++++++++ Result ++++++++++++++++++
      ++++++++++++++++++++++++++++++++++++++++++++
      ---> Total time elapsed: 2.76 Seconds  <---
      ---> Accuracy: 63.0%                     <---
      ++++++++++++++++++++++++++++++++++++++++++++
      ++++++++++++++++++++++++++++++++++++++++++++
```

- Result from agent:

```json
{
  "file": "/home/shushant/check.py",
  "results": [
    {
      "description": "",
      "shortname": "Apache-2.0",
      "sim_score": 1.0,
      "sim_type": "logisticRegression"
    }
  ]
}
```

### 2. Atarashi agent based on Linear Support Vector Machine.

To create an agent on [Atarashi](https://github.com/fossology/atarashi) for linear support vector machine model trained on [Minerva Dataset](https://github.com/fossology/Minerva-Dataset-Generation).

#### Results:

Below given is the accuracy score for the agent created on atarashi. The accuracy we are getting is from
[evaluator.py](https://github.com/fossology/atarashi/blob/master/atarashi/evaluator/evaluator.py).

- Accuracy of agent

```
 Total files scanned = 100
 Successfully matched = 63

      ++++++++++++++++++ Result ++++++++++++++++++
      ++++++++++++++++++++++++++++++++++++++++++++
      ---> Total time elapsed: 2.06 Seconds  <---
      ---> Accuracy: 63.0%                     <---
      ++++++++++++++++++++++++++++++++++++++++++++
      ++++++++++++++++++++++++++++++++++++++++++++
```

- Result from agent:

```json
{
  "file": "/home/shushant/check.py",
  "results": [
    {
      "description": "",
      "shortname": "Apache-2.0",
      "sim_score": 1.0,
      "sim_type": "linearsvc"
    }
  ]
}
```

### 3. Okapibm25 agent

Implementation of Okapibm25 was not decided. But just for checking the accuracy and working of bm25 we decided to create a agent for the same. The implementation of agent is based on [this wiki](https://en.wikipedia.org/wiki/Okapi_BM25).

#### Results:

Below given is the accuracy score for the agent created on atarashi. The accuracy we are getting is from
[evaluator.py](https://github.com/fossology/atarashi/blob/master/atarashi/evaluator/evaluator.py).

- Accuracy of agent:

```
 Total files scanned = 100
 Successfully matched = 62

      ++++++++++++++++++ Result ++++++++++++++++++
      ++++++++++++++++++++++++++++++++++++++++++++
      ---> Total time elapsed: 19.04 Seconds  <---
      ---> Accuracy: 62.0%                     <---
      ++++++++++++++++++++++++++++++++++++++++++++
      ++++++++++++++++++++++++++++++++++++++++++++
```

- Result from agent:

```json
{
  "file": "/home/shushant/check.py",
  "results": [
    {
      "description": "",
      "shortname": "ECL-2.0",
      "sim_score": 36.85958665693663,
      "sim_type": "bm25"
    },
    {
      "description": "",
      "shortname": "Apache-2.0",
      "sim_score": 36.58521980445177,
      "sim_type": "bm25"
    },
    {
      "description": "",
      "shortname": "SCEA",
      "sim_score": 36.321346243985616,
      "sim_type": "bm25"
    },
    {
      "description": "",
      "shortname": "Flora",
      "sim_score": 35.987182420391704,
      "sim_type": "bm25"
    },
    {
      "description": "",
      "shortname": "Flora-1.1",
      "sim_score": 35.987182420391704,
      "sim_type": "bm25"
    }
  ]
}
```

### 2. Packaging of trained model

The trained model on [Minerva Dataset](https://github.com/fossology/Minerva-Dataset-Generation) needed to predict license shortname for [Atarashi](https://github.com/fossology/atarashi). For that there were two ideas to do so:

- The first idea was to both train and test the models on [Atarashi](https://github.com/fossology/atarashi) (i.e. the codebase of atarashi will also contain the trained binary files from model). And the atarashi agent for a particular model will predict the license shortname from the binary file generated after training.
- And the second idea was to train models on minerva dataset repository itself. And we can simply create a python package for trained model and the package can be imported to atarashi agent for predicting license shortname.

After discussing both the solution we came to conclusion that second idea is more convincing because if the binary files stay on [atarashi codebase](https://github.com/fossology/atarashi), it will eventually cause more memory usage and may slow the software. Also after packaging the model anyone can used it for their own purpose.

#### Packages:

1. [Linear support vector machine package](https://pypi.org/project/linearsvc/)
2. [Logistic regression package](https://pypi.org/project/logreg/)

#### Results:

```
(installing) (base) shushant@sushant-device:~$ pip install linearsvc
Collecting linearsvc
  Using cached linearsvc-1.0.1-py3-none-any.whl (12.8 MB)
Installing collected packages: linearsvc
Successfully installed linearsvc-1.0.1
```

```
(installing) (base) shushant@sushant-device:~$ pip install logreg
Collecting logreg
  Using cached logreg-0.1.0-py3-none-any.whl (46.6 MB)
Installing collected packages: logreg
Successfully installed logreg-0.1.0
```

## 📚 NOTEBOOKS

- [Sklearn Logistic regression for Multiclass text classification](https://www.kaggle.com/code/sushanttkr07/logistic?scriptVersionId=105138828)
- [Sklearn Linear Support Vector Machine for Multiclass text classification](https://www.kaggle.com/code/sushanttkr07/linearsvc?scriptVersionId=105147878)
- [Doc2Vec For Semantic Similarity](https://www.kaggle.com/code/sushanttkr07/doc2vec)
- [Finetuning using Bert transformer](https://www.kaggle.com/code/sushanttkr07/bertmodel1?scriptVersionId=105132896)

## MAJOR PULL REQUESTS

- [Feat(model): Add agent for logistic regression model](https://github.com/fossology/atarashi/pull/100)
- [Feat(model): Add linearsvc agent](https://github.com/fossology/atarashi/pull/102)
- [Feat(agent): Add okapibm25 agent](https://github.com/fossology/atarashi/pull/101)
- [Feat(package): Add model packages](https://github.com/fossology/Minerva-Dataset-Generation/pull/5)

## 👨🏻‍🏫 DELIVERABLES

|      Tasks       |                    Status                     |                                                              Links                                                               |
| :--------------: | :-------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------: |
|  Logistic agent  |  Both training and testing of model is done   | [Agent](https://github.com/fossology/atarashi/pull/100), [Model](https://github.com/fossology/Minerva-Dataset-Generation/pull/5) |
| Linearsvc agent  |  Both training and testing of model is done   | [Agent](https://github.com/fossology/atarashi/pull/102), [Model](https://github.com/fossology/Minerva-Dataset-Generation/pull/5) |
| Okapi-BM25 agent |        Implementation of agent is done        |                                     [Agent](https://github.com/fossology/atarashi/pull/101)                                      |
|  Doc2vec Model   | Training of model is done and testing is left |                                   [Notebook](https://www.kaggle.com/code/sushanttkr07/doc2vec)                                   |
|    Bert Model    | Training of model is done and testing is left |                    [Notebook](https://www.kaggle.com/code/sushanttkr07/bertmodel1?scriptVersionId=105132896)                     |

## REACH OUT TO ME!

- [LinkedIn](https://www.linkedin.com/in/its-sushant/)
- [GitHub](https://github.com/its-sushant)
- [Email](sushantmishra02102002@gmail.com)

[![](https://img.shields.io/badge/Made%20With%20❤️%20By-Sushant-red)](https://github.com/its-sushant)
