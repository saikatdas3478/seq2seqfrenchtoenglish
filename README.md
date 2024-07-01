# French-English Translator Model

This project focuses on developing a French-English translator using a sequence-to-sequence model with an LSTM architecture. Below are the key sections detailing the methodology, how to run the code, and the results.

## Introduction

Machine translation is a challenging task in natural language processing that involves converting text from one language to another. In this project, we build a neural machine translation model using a sequence-to-sequence approach with LSTM (Long Short-Term Memory) networks. The model is trained on a dataset of French-English sentence pairs.

## Methodology

### Dataset Preparation

1. **Reading the Dataset:**
   - The dataset consists of French-English sentence pairs.
   - We read all the lines from the dataset and store them in a list.

2. **Splitting into Train and Test Sets:**
   - A subset of the dataset is randomly selected as the test set.
   - The remaining data is used for training the model.

3. **Text Preprocessing:**
   - Unicode normalization is applied to the text.
   - Punctuation is substituted, and text is converted to lowercase.

4. **Tokenization:**
   - Tokenizers are created for both French and English texts.
   - These tokenizers convert text to sequences of integers.

### Model Building

1. **Encoder:**
   - The encoder processes the French input sentences.
   - It consists of an embedding layer followed by an LSTM layer.

2. **Decoder:**
   - The decoder processes the English output sentences.
   - It also consists of an embedding layer followed by an LSTM layer.
   - The decoder outputs are passed through a dense layer with a softmax activation.

3. **Model Compilation:**
   - The model is compiled using the Adam optimizer.
   - The loss function used is `sparse_categorical_crossentropy`.

### Training

1. **Callbacks:**
   - ModelCheckpoint is used to save the best model based on validation loss.
   - EarlyStopping is used to stop training if the validation loss does not improve for 3 consecutive epochs.

2. **Fitting the Model:**
   - The model is trained on the padded sequences of French and English sentences.
   - Validation data is used to monitor the model's performance.

### Testing

1. **Preprocessing Test Data:**
   - The test data is preprocessed similarly to the training data.
   - Padded sequences are created for the test set.

2. **Generating Translations:**
   - The trained model is used to generate translations for the test set.
   - The performance of the model is evaluated based on these translations.

## How to Run

1. **Install Required Libraries:**
   - Ensure you have the necessary libraries installed:
     ```sh
     pip install tensorflow numpy pandas
     ```

2. **Prepare the Dataset:**
   - Download the French-English sentence pairs dataset.
   - Place the dataset in the appropriate directory.

3. **Run the Script:**
   - Execute the script to preprocess the data, build and train the model, and evaluate the translations.

## Results

The translations generated by the model are compared to the human translations. The model's performance can be improved by training on a larger dataset and experimenting with different model architectures and hyperparameters.

### Sample Translations

| French Sentence                                  | Human Translation                          | Machine Translation                          |
|--------------------------------------------------|--------------------------------------------|----------------------------------------------|
| Vous n'êtes pas trop en retard.                  | You're not too late.                       | you're not too late .                        |
| C'est plutôt incroyable.                         | It's pretty incredible.                    | this is pretty incredible .                  |
| Cette ville est réputée pour ses magnifiques j...| This city is famous for its beautiful park.| this town is famous for its famous .         |
| Je coopérerai.                                   | I'll cooperate.                            | i'll play along .                            |
| Nous allons manquer de faire ceci.               | We're going to miss doing this.            | we're going to have to do this .             |
| Il me reste encore des choses à faire.           | I still have things left to do.            | i still have a lot of things to do .         |
| Vous l'ai-je déjà dit ?                          | Did I tell you that already?               | did i tell you that ?                        |
| Nous sommes restés dans un hôtel au bord du lac. | We stayed at a hotel by the lake.          | we stayed at a hotel in the lake .           |
| On n'en ressort que ce qu'on y a introduit.      | You get out only what you put in.          | you get out only what you put in .           |
| C'est l'homme parfait pour toi.                  | He's the perfect man for you.              | this is the perfect man for you .            |
| Elle écrit à son fils de temps en temps.         | She writes to her son every so often.      | she writes to her son in time .              |
| Ça te gardera chaud.                             | This will keep you warm.                   | this will keep you warm .                    |
| Ils vivent dans des tentes.                      | They live in tents.                        | they live in tents .                         |
| Je suppose que nous devrions aller prendre que...| I guess we should go get something to eat. | i guess we should make something that go .   |
| Tu ne t'en iras pas, si ?                        | You won't go, will you?                    | you won't go , do you ?                      |

The translations are fairly accurate, with some replaced synonyms and minor errors. Further training and model optimization can enhance the accuracy.

![Kaggle link](https://www.kaggle.com/code/saikatsaligia/french-to-english-machine-translation)
The dataset I've used comes from ![Tatoeba](https://tatoeba.org/en), a collection of sentence translations in a variety of languages sourced from volunteers. 
