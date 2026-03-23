# poker-hand-machine-learning-project
[README.md](https://github.com/user-attachments/files/26171701/README.md)
Project Overview
This project utilizes a Random Forest Classifier to identify poker hands from the UCI Machine Learning Repository. The primary challenge of this dataset is the extreme class imbalance, where "Nothing" and "One Pair" hands constitute over 98% of the data.

To solve this, I implemented a custom Feature Engineering pipeline that translates raw card data into logical poker signatures, achieving a high-performance classification system.

Poker Hand Rulings (Target Classes)
The model was trained to recognize and categorize hands into the following 10 levels:

Class,Hand Name,Description
0,Nothing,No patterns; high card only.
1,One Pair,"Two cards of the same rank (e.g., 7-7)."
2,Two Pair,"Two different pairs (e.g., 9-9 and 4-4)."
3,Three of a Kind,"Three cards of the same rank (e.g., Q-Q-Q)."
4,Straight,"Five cards in numerical sequence (e.g., 4-5-6-7-8)."
5,Flush,Five cards of the same suit.
6,Full House,"Three of a kind plus a pair (e.g., J-J-J and 2-2)."
7,Four of a Kind,"Four cards of the same rank (e.g., A-A-A-A)."
8,Straight Flush,"Five cards in sequence, all of the same suit."
9,Royal Flush,"10-J-Q-K-A, all of the same suit."



Key Methodology
1. Feature Engineering
Raw data represents cards as individual suits and ranks. My pipeline transformed this into:

Sorted Ranks: To identify sequential "Straight" patterns.

Unique Counts: To detect "Pairs," "Trips," and "Full Houses."

Suit Consistency: To identify "Flushes.

Model Optimization
Algorithm: Random Forest Classifier.

Tuning: Used RandomizedSearchCV to optimize n_estimators and max_depth.

Validation: Performed Nested Cross-Validation (3x3 folds) to ensure results were not biased by the train-test split




Performance Results
Overall Accuracy: 98%

Macro F1-Score (Validated): 0.5452

Analysis: The model is exceptionally strong at identifying common hands. The Confusion Matrix shows a minor overlap between "Three of a Kind" and "Two Pair" due to similar unique-rank counts—a common hurdle in poker AI.


References:
https://archive.ics.uci.edu/dataset/144/poker+hand
Scikit-Learn Documentation
