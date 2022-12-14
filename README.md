# Speech-to-Text
Code for training model submitted to Attention-Based Speech Recognition Kaggle

<img width="1040" alt="image" src="https://user-images.githubusercontent.com/57874328/207713930-5fb1e0f9-3fda-4f4d-b7ec-da445ecc2572.png">

Achieved 7.5 Levenshtein distance on Attention-Based Speech Recognition Kaggle.


Final model architecture:

Listen, Attend, Spell (LAS) model

with double-layered pyramidial BLSTMs

0.35 Dropout after each pBLSTM

input_size = 15

encoder_hidden_size = 512

embed_size = 256

decoder_hidden_size = 512

decoder_output_size = 128

projection_size = 128


Trained with 0.99 exponential decay teacher forcing schedule

Using 20 freq_mask_value iid masks for frequency masking data augmentation

Trained for 180 epochs, best reached at epoch 145

Stages of model training:

Stage 1 : When starting : TF rate = 1, Dropout disabled, Augmentations disabled

Stage 2 : When LD < 21  : Start decaying teacher forcing rate

Stage 3 : When TF < 1   : Activate dropout in BLSTM

Stage 4 : When LD < 14  : Activate data augmentations


Experiments:

Data augmentation: (None, Frequency masking 20-120)

pBLSTM Dropout: (0, 0.2, 0.35)

pBLSTM Layers: 1-2

Encoder hidden size: 256-512

TF rate: Linear from 30-70, Multi-step Linear 30-60, 70-100, 110-150, 0.99 exponential decay

