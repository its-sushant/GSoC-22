### Updates

- Implemented algorithm for bert transformer:
    - Basically the implementation is done using the labelling of different classes and create a dictionary where the 
    license short name is key and it's label is value.
    ```python
        possible_labels = df.short_name.unique()

        label_dict = {}
        for index, possible_label in enumerate(possible_labels):
            label_dict[possible_label] = index
    ```
    - And for tokenizing and encoding **bert-base-uncased** pretrained model is used.
    ```python
        tokenizer = BertTokenizer.from_pretrained('bert-base-uncased', 
                                          do_lower_case=True)
                                          
        encoded_data_train = tokenizer.batch_encode_plus(
            df[df.data_type=='train'].text.values, 
            add_special_tokens=True, 
            return_attention_mask=True, 
            pad_to_max_length=True, 
            max_length=256, 
            return_tensors='pt'
        )
    ```
- And for now trained a transformer model on smaller part of [minerva dataset](https://github.com/fossology/Minerva-Dataset-Generation)
because the model requires a lot of RAM and time for training the whole dataset.
- Created a simple notebook for the trained model. It can be seen [here](https://www.kaggle.com/sushanttkr07/bertmodel1).
