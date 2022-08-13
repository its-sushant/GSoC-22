### Updates

- [Doc2vec Model](https://radimrehurek.com/gensim/models/doc2vec.html) requires tagged document for training the model,
such that it can make a vector for each document that can be further use to calculate cosine similarity for the
license statement. Due to lack of memory in my computer I was not able to tag whole [dataset](https://github.com/fossology/Minerva-Dataset-Generation).
So currently for checking the working of model, this week I have trained a smaller part of dataset on
[Doc2vec Model](https://radimrehurek.com/gensim/models/doc2vec.html).
- Created agent for the same trained model on [atarashi](https://github.com/fossology/atarashi) and got the accuracy score of **8** percent.
```
 Total files scanned = 100
 Successfully matched = 8

      ++++++++++++++++++ Result ++++++++++++++++++
      ++++++++++++++++++++++++++++++++++++++++++++
      ---> Total time elapsed: 13.02 Seconds  <---
      ---> Accuracy: 8.0%                     <---
      ++++++++++++++++++++++++++++++++++++++++++++
      ++++++++++++++++++++++++++++++++++++++++++++
```
- Working of agent is shown below:
```json
{
    "file": "/home/shushant/check.py",
    "results": [
        {
            "description": "",
            "shortname": "BSD-1-Clause",
            "sim_score": 0.5472090244293213,
            "sim_type": "semanticTextSim"
        }
    ]
}
```

### Conclusion and Further Plans

- Trainig has been done on a smaller part of [dataset](https://github.com/fossology/Minerva-Dataset-Generation). Will train
[Doc2vec Model](https://radimrehurek.com/gensim/models/doc2vec.html) on whole dataset and see if any further improvement is
needed or not.
- Will start working on the documentation for final evalutation.
