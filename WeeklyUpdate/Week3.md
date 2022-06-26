## Updates
- Raised **PR's** on both [Minerva](https://github.com/fossology/Minerva-Dataset-Generation) and
[Atarashi](https://github.com/fossology/atarashi)
   - [Add agent for logistic regression model](https://github.com/fossology/atarashi/pull/100)
   - [Add logistic regression model](https://github.com/fossology/Minerva-Dataset-Generation/pull/4)
- Started working on creating the packages for the trained model. For example the folder structure for
**LogisticRegression** model should look like:
              
              └── logreg
                  ├── MANIFEST.in
                  ├── README.md
                  ├── setup.py
                  └── src
                      ├── LICENSE
                      ├── logreg
                      │   ├── data
                      │   │   └── logreg
                      │   └── __init__.py
                      └── model_train.py
