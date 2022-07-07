### Updates

- Created the python packages for both **[LogisticRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html)** and **[Linear SVC](https://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html)**
  model. Below is the file structure for created package:
  
```python

                  ├── linearsvc
                  │   ├── LICENSE
                  │   ├── MANIFEST.in
                  │   ├── README.md
                  │   ├── setup.py
                  │   └── src
                  │       ├── linearsvc
                  │       │   ├── data
                  │       │   │   └── linearsvc
                  │       │   └── __init__.py
                  │       └── model_train.py
                  └── logreg
                      ├── LICENSE
                      ├── MANIFEST.in
                      ├── README.md
                      ├── setup.py
                      └── src
                          ├── logreg
                          │   ├── data
                          │   │   └── logreg
                          │   └── __init__.py
                          └── model_train.py
```                        

- Modified **init.py** from the **src** folder of both the python packages as suggested:

  - In the code below it can be seen that the class of linearsvc have two functions:
  - **linearsvc.classify()** can be called to get the model classifier and the classifier can
    be further used to predict the license shortname for **[atarshi](https://github.com/fossology/atarashi)**
    agent just by using the **[predict()](https://www.askpython.com/python/examples/python-predict-function)**
    function.
  - And in **linearsvc.predict_shortname()**, we can directly pass the preprocessed file and it will
    return the license shortname.
  - Similar functions has been implemented for **logreg** model also.
```python
            class linearsvc():
              def __init__(self, preprocessed_file):
                  self.preprocessed_file = preprocessed_file

              def classify(self):
                  data = resource_filename("linearsvc", "data/linearsvc")
                  with open(data, 'rb') as f:
                      Classifier = pickle.load(f)
                  return Classifier

              def predict_shortname(self):
                  predictor = self.classify()
                  return predictor.predict(self.preprocessed_file)
```

- Implemented the agent for **[Linear SVC](https://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html)**
  on **[atarshi](https://github.com/fossology/atarashi)** locally.

### Conclusion and Further Plans

- Will make the changes according to further suggestion.
- Will start implementing **[okapi_BM25](https://en.wikipedia.org/wiki/Okapi_BM25)** in place of
  **[tfidftransformer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfTransformer.html)**
  for ranking the license text on dataset for training the models and compare which among the two is working better
  on dataset.
