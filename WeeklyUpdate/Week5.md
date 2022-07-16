### Updates

- Made changes suggested by the mentors on the [pr](https://github.com/fossology/Minerva-Dataset-Generation/pull/5)
  creted on [Minerva](https://github.com/fossology/Minerva-Dataset-Generation).
- Implemented agent on [atarashi](https://github.com/fossology/atarashi) for
  [okapibm25](https://en.wikipedia.org/wiki/Okapi_BM25) and got the accuracy score of **62%**.

  ```
            Total files scanned = 100
            Successfully matched = 62

            ++++++++++++++++++ Result ++++++++++++++++++
            ++++++++++++++++++++++++++++++++++++++++++++
            ---> Total time elapsed: 11.67 Seconds  <---
            ---> Accuracy: 62.0%                     <---
            ++++++++++++++++++++++++++++++++++++++++++++
            ++++++++++++++++++++++++++++++++++++++++++++
  ```

- And raised the pr for the same.

  - [feat(agent):Add okapibm25 agent](https://github.com/fossology/atarashi/pull/101)

  ```python
   def scan(self, filePath):
        '''
        Read the content of filename, extract the comments and preprocess them.
        Find the license of the preprocessed file.
        :param filePath: Path of the file to scan
        :return: Returns the license's short name with highest similarity scores
        '''
        processedData = super().loadFile(filePath)

        with open(filePath) as file:
            raw_data = file.read()
        spdx_identifers = spdx_identifer(raw_data,
                                         self.licenseList['shortname'])

        match = []
        if spdx_identifers:
            match.extend(spdx_identifers)
        else:
            tokenize_corpus = []
            corpus_identifier = []
            for idx in range(len(self.licenseList)):
                tok = self.licenseList.iloc[idx]['processed_text'].split(" ")
                tokenize_corpus.append(tok)
                tok_identifier = self.licenseList.iloc[idx]['shortname']
                corpus_identifier.append(tok_identifier)

            bm25 = BM25Okapi(tokenize_corpus)
            doc_scores = bm25.get_scores(processedData.split(" "))
            indices = np.argsort(doc_scores)[::-1][:10]

            for index in indices:
                match.append({
                    "shortname": str(corpus_identifier[index]),
                    "sim_score": doc_scores[index],
                    "sim_type": "bm25",
                    "description": ""
                })

        return match
  ```

  - In above given code it can be seen that I have used [bm25](https://pypi.org/project/rank-bm25/) to transform
    processed text and then the similarity score has been calculated.

### Conclusion and Further Plans

- Will make the changes according to further suggestion.
