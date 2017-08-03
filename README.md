# speech-generation-using-RNN

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
-
