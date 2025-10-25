Multilingual Seq2Seq Transliteration Model
1. Introduction

This project builds a neural network model that can transliterate words from multiple Indian languages (like Hindi or Tamil) into English letters. It uses a Sequence-to-Sequence (Seq2Seq) architecture with an attention mechanism to learn how to map characters between scripts.

2. Data Preparation

The model reads training, validation, and testing data from CSV files stored in separate folders for each language. A special language tag (for example, <hin> or <tam>) is added to each word so the model can recognize which language it belongs to. All datasets are then combined and shuffled.

3. Vocabulary and Dataset

Character-level vocabularies are created for both the input and output sequences. Special tokens are included for padding, start of sequence, end of sequence, and unknown characters. A custom dataset converts text into numerical tensors, and the DataLoader efficiently handles batching during training.

4. Model Architecture

The model consists of three main components:

Encoder: Processes the input sequence using a bidirectional LSTM to capture context.

Attention: Helps the model focus on important parts of the input when generating each output character.

Decoder: Generates the output sequence one character at a time using an LSTM and attention outputs.
A bridge layer connects the encoder’s final states to the decoder’s initial states.

5. Training Process

The model is trained using cross-entropy loss and optimized with Adam. Teacher forcing is used to speed up learning, and gradient clipping prevents instability. The learning rate is adjusted dynamically, and early stopping is applied to avoid overfitting. The best model is saved based on validation loss.

6. Output and Results

After training, the model can transliterate words from various languages into the Roman script. The final trained model file, “seq2seq_attn_multilingual_best.pt,” is ready for use in transliteration tasks or deployment.

7. Conclusion

This project demonstrates how deep learning can be applied to multilingual transliteration. By combining Seq2Seq and attention mechanisms, the system learns to convert characters between scripts effectively while handling multiple languages within one unified model.