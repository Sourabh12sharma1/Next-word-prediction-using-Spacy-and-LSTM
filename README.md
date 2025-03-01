We were building a next-word prediction model using an LSTM-based architecture on a Medium dataset. 
We relied on spaCy for tokenization to convert text into numerical sequences, which were then fed into our Keras/TensorFlow model.

Solution Explanation:

Ensuring Proper Tokenization with spaCy:
We first used spaCy to clean and tokenize the Medium dataset, transforming each title (or other text fields) into sequences of integer IDs.
Fixing the 0 Trainable Parameter Issue:
We explicitly specified the input shape in the Embedding layer, for example, input_shape=(max_len,) or used a dummy forward pass (e.g., passing a batch of zeros) to force the model to build. Once the model was built with correct input dimensions from our spaCy-tokenized sequences, the parameter count displayed correctly.
Training the LSTM Model:
With the model properly built (Embedding → LSTM → LSTM → Dense), we trained on the tokenized data. The embedding captured word semantics, and the stacked LSTM layers modeled temporal dependencies in text sequences. Finally, the Dense layer with softmax served as the next-word predictor, providing a probability distribution over the entire vocabulary.
