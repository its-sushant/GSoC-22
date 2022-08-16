# Google Summer of Code 2022

![ViewCount](https://views.whatilearened.today/views/github/its-sushant/GSoC-22.svg)
![GitHub](https://img.shields.io/github/followers/its-sushant?style=social)
![GSoC @ FOSSology](/static/gsocHeader.png)

<div align = "center"><h2>Improve Minerva OSS Dataset and implement models for Atarashi</h2></div>

## Project Overview

In GSoC 2021 [Minerva Dataset](https://github.com/fossology/Minerva-Dataset-Generation) was created to train machine learning
model for predicting license shortname for [Atarashi](https://github.com/fossology/atarashi) using different machine/deep learning
models. Currently [Atarashi](https://github.com/fossology/atarashi) has four active agents for predicting license statement from the source code.
And the highest accuracy we are getting right now is **62%**, which is from [tfidf](https://github.com/fossology/atarashi/blob/master/atarashi/agents/tfidf.py) agent.

## Results

Below given is the accuracy score for all agents that I have created this Google summer of code 22. The accuracy we are getting is from
[evaluator.py](https://github.com/fossology/atarashi/blob/master/atarashi/evaluator/evaluator.py) and the agent has been created using [Minerva Dataset](https://github.com/fossology/Minerva-Dataset-Generation).

**1. Logistic regression agent**

**Accuracy of agent**
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

**Result from agent:**
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
**1. Logistic regression agent**

**Accuracy of agent**
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

**Result from agent:**
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

## Weekly Updates

| Week   | Updates |
| :---:       |    :----:   |
| Week1 | [Week1 Update](https://github.com/its-sushant/GSoC-22/blob/main/WeeklyUpdate/Week1.md) |
| Week2 | [Week2 Update](https://github.com/its-sushant/GSoC-22/blob/main/WeeklyUpdate/Week2.md) |
| Week3 | [Week3 Update](https://github.com/its-sushant/GSoC-22/blob/main/WeeklyUpdate/Week3.md) |
| Week4 | [Week4 Update](https://github.com/its-sushant/GSoC-22/blob/main/WeeklyUpdate/Week4.md) |
| Week5 | [Week5 Update](https://github.com/its-sushant/GSoC-22/blob/main/WeeklyUpdate/Week5.md) |
| Week6 | [Week6 Update](https://github.com/its-sushant/GSoC-22/blob/main/WeeklyUpdate/Week6.md) |
| Week7 | [Week7 Update](https://github.com/its-sushant/GSoC-22/blob/main/WeeklyUpdate/Week7.md) |
| Week8 | [Week8 Update](https://github.com/its-sushant/GSoC-22/blob/main/WeeklyUpdate/Week8.md) |
| Week9 | Week9 Update|
| Week10 | Week10 Update|
| Week11 | Week11 Update|
| Week12 | Week12 Update|



## Reach out to me
- [Connect with me on LinkedIn](https://www.linkedin.com/in/its-sushant/)
- [Give a follow on GitHub](https://github.com/its-sushant) 
- [Email](sushantmishra02102002@gmail.com)

[![](https://img.shields.io/badge/Made%20With%20❤️%20By-Sushant-red)](https://github.com/its-sushant)
