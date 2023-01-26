# Data-To-Text-Generation

Data-to-Text generation refers to the task of automatically producing text from non-linguistic input.
Entries may be in different forms, such as indexes, tables, key-value pairs, or triplets. This data, by its very nature, cannot be easily used by humans; Determines their urgent need for tuning.
Recently, many businesses have focused on taking advantage of structured data in various applications, such as answering questions or retrieving a table.

## Dataset 

The WebNLG challenge consists in mapping data to text.
The training data consists of Data/Text pairs where the data is a set of triples extracted from DBpedia and the text is a verbalisation of these triples.
For instance, given the 3 DBpedia triples shown in (a), the aim is to generate a text such as (b).

    a. (John_E_Blaha birthDate 1942_08_26) (John_E_Blaha birthPlace San_Antonio) (John_E_Blaha occupation Fighter_pilot)
    b. John E Blaha, born in San Antonio on 1942-08-26, worked as a fighter pilot
    
  
## Sequence to sequence model

The model is built as follows :

A. Encoder with GloVe embedding
It is an input layer followed by a layer embedding) The weights for this layer were taken from GloVe
embedding, ) and then the LSTM layer

B. Decoder: with GloVe embedding and Attention mechnisme
It is an input layer followed by a layer embedding) The weights for this layer were taken from GloVe
embedding, ) then LSTM layer then Attention layer then TimeDistributed layer.

## Results
The model trained on the following hyperparameters :

      Hidden dim = 256
      Embedding dim = 200
      Mask_zero=True (in the embedding layers)
      Drop out in all layers = 0.3
      RMS prop optimizer with learning rate 0.0001
      Batch size = 64
      Epochs = 20

The results were evaluated using the BLEU standard, and the results were as follows:

Training on One triple input training:

      BLEU on test set = 49.42
      BLEU on dev set = 50.96
      
Training on an input composed of several triples (from 1 to 7 triples):

      BLEU on test set = 31.77
      BLEU on dev set = 32.25
