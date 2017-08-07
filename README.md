# speech-generation-using-RNN
This project was developed for Wolters Kluwer whilst my tenure as an Artificial Intelligence Engineer (Intern), and so the code is not posted to this repository.

Problem statement: To generate questions based on a piece of text (facts).

Approach: Develop a RNN using LSTM cells and Attention mechanism with encoder - decoder.

Technologies Used:
-----------------
- Python 3.5
- Keras
- Tensorflow backend
- LSTM (Long short term memory)

Dataset:
--------
- The data was in the format of csv files as question-answer sets.
- The question and answer had to be properly constructed sentences for training and understanding the overlapping words.
- The model was trained on 100,000+ question-answer sets. Reserving nearly 20% for validation and 80% for training.
- For example:

Fact: The primary objective of ankle fracture fixation is to recreate a tibiotalar articulation with physiological contact stresses
 
Question: What is the primary objective of ankle fracture fixation


Preprocessing:
-------------
- Sentence splitting and tokenization
- <SOS> and <EOS> tokens added to the start and end of a sentence respectively
- Some answers span two or more sentences, concatenate them.
- create a vocabulary of the most 45k tokens (including <SOS> and <EOS> tokens and placeholders)
- 28k most frequent tokens for target side vocabulary
- tokens outside vocabulary, replaced by 'UNK' (UNK stands for Unknown)
- Word embedding of 300 dimensions using glove pretrained vectors for initialization
 
 
Model:
-----
- model = Sequential()
- Layers in the encoder network: Embedding, LSTM with hidden size of 1000, RepeatVector
- Layers in the decoder network: LSTM with hidden size of 1000, TimeDistributed, Softmax Activation
- loss = categorical_crossentropy, optimizer = rmsprop


Training:
--------
- Optimization using SGD with an initial learning rate of 1.0
- Mini batch size of 100
- Training upto 25 epochs
- Saving checkpoints whilst training the model to resume with the saved weights next time

Testing:
-------
- A sentence or paragraph is to be provided as an input
- The saved model is loaded
- Question is generated based on the input sentence / paragraph

Tuning the accuracy:
-------------------
- Referring to a few papers and other resources listed under references to help define the model, I tried a few models wth different combination of layers and picked the one that gave the best accuracy. I tried tuning a few parameters of the layers, mostly changing the batch size, vocabulary size, hidden layers, etc to improve accuracy.
- The solver parameters were tuned after every pass. We dropped the learning rate after the first iteration and increased no. of epochs. - Tried to make it distributed.

References:
----------
* [ [1] Sequence to Sequence Learning with Neural Networks](http://papers.nips.cc/paper/5346-sequence-to-sequence-learning-with-neural-networks.pdf)
* [ [2] Learning Phrase Representations using RNN Encoder–Decoder for Statistical Machine Translation](http://arxiv.org/pdf/1406.1078.pdf)
* [ [3] Neural Machine Translation by Jointly Learning to Align and Translate](http://arxiv.org/pdf/1409.0473v6.pdf)
* [ [4] A Neural Conversational Model](http://arxiv.org/pdf/1506.05869v1.pdf)
