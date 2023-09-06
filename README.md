# Dota 2 Hero Drafting Assistant

## Overview

The Dota 2 Hero Drafting Assistant is a machine learning project aimed at assisting players in selecting suitable heroes for the last pick during the drafting phase of the game. This system suggests three hero choices to the user, taking into account the user's draft, the opponent's draft, and banned heroes. By considering these factors, the suggestions aim to provide diverse and effective hero options for the final pick.

A web application is used to demonstrate the entire drafting process, allowing users to input their currently picked and banned heroes according to the draft flow. The model then displays the three best hero choices as output.

## System Architecture



1. **Dataset Acquisition**: The project starts by acquiring data from open-source websites, specifically OpenDota. API calls are utilized to fetch draft data, and this information is stored in databases using Steam Web API and replay parsing of .dem files.

2. **Data Preprocessing**: Acquired data is processed and structured into a 2-dimensional array, with each row corresponding to a match. To enhance the model's performance, a data duplication technique is implemented to increase the volume of data points.

3. **Model Training**: Deep learning models, including CBOW (Continuous Bag of Words) and LSTM (Long Short-Term Memory), are trained on the processed data. These models learn hero embeddings and predict the categorical output for hero suggestions.

4. **Web Application**: The drafting phase is displayed using a web application. Users input their hero selections and bans, and the model provides hero suggestions based on this input.

## Methodology

### Dataset

The dataset is obtained from OpenDota, allowing 50,000 API calls per month. It comprises draft sequences from 34,877 matches across different patches. Data is cleaned, processed, and structured into a 2D array, with data duplication to increase the dataset size.

### CBOW (Continuous Bag of Words)

Similar to NLP's word2vec, CBOW is used to learn embeddings for heroes based on their pick contexts. Negative sampling is incorporated to optimize the objective and improve computation speed. The Gensim library is employed to learn 30 features for each hero.

### LSTM (Long Short-Term Memory)

LSTMs are used for sequence prediction, as they efficiently handle learning over a large number of time steps. The model comprises two LSTM layers, each with dropout rates to prevent overfitting. Softmax layers are used to predict hero choices.

## Results

The system provides three hero suggestions to accommodate the complexity of Dota 2, which offers 97 different heroes for the last pick. The model achieves commendable accuracy, and the 1st suggestion contains the highest number of correct predictions in the test set. Confusion matrices indicate that 'Mid' heroes are often suggested as last picks.

## Analysis Using Confusion Matrix

Heroes are categorized into four roles: Carry, Mid, Offlane, and Support. Confusion matrices for each suggestion reveal that 'Mid' heroes are frequently recommended, while 'Support' heroes are typically picked earlier in the draft.

## Patches and Meta Shift

Dota 2 regularly receives updates in the form of patches, impacting hero roles and gameplay. To account for this, a data duplication technique is employed to make the model familiar with different patch variations. The model's top-k accuracy remains consistent across patches.

## Conclusion

Despite Dota 2's evolving nature, this machine learning model assists players, from beginners to professionals, in making informed hero picks. The system's accuracy in predicting hero choices enhances gameplay and strategy development, contributing to a more enjoyable Dota 2 experience.

---

*Note: Figures and additional details can be found in the original research paper.*


Co-Auhors - Yassar Mohammed, Siddhesh Iyer, Samundiswary Srinivasan
Publication Link: https://ieeexplore.ieee.org/document/9776822/
