# Encrypted text classification 

Contest and dataset can be taken from here: https://aihub.ml/competitions/759#learn_the_details

**Overview**:

This is the text classification contest which the records are the sequences of encryped numbers. The goal is to classify them into 3 classes 0, 1 and 2.

There are multiple solutions for this contest:

**1) With unlabel dataset**

*a)* **(Highest F1 score)**

Chunk unlabel dataset based on the mean length of the records of train dataset.

=> Create TF-IDF vector for each class.

=> Compute cosine similarity among unlabel records and train records.

=> Take the majority voting and assign that as pseudo labels.

*b)*

After finetuning multi large language models with train dataset (i use 5 LLMs here: DistiBERT, RoBERTa, DeBERTa, XLNet and ELECTRA), infer those models with chunked dataset.

=> Then use that chunked dataset to finetune again those LLMs and infer with test dataset.

*c)* Semi-supervised method

First finetune the DistiBERT Masked Language model with unlabel dataset then create the pseudo labels

=> Combine pseudo-labeled datas with training data and train with DistiBERT.

**2) With similar dataset**

Use similar dataset to augment the training data by replacing the token which is near with toekns in similar

=> Create augment dataset and finetune the those LLMs 

Because the dataset is smaill, ovefitting is unavoidable.

