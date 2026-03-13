# Yelp Recommendation Analysis using LLMs and Review Summarization

## Project Overview

This project investigates the use of Large Language Models (LLMs) for rating prediction and recommendation analysis using the Yelp dataset.
The goal is to explore how contextual and text-rich datasets can improve recommendation performance by leveraging user reviews and business information.

In addition to the standard preprocessing and evaluation pipeline, this project incorporates **automatic review summarization** to extract concise representations of user opinions before model training.

The experimental pipeline includes data preprocessing, review summarization, model fine-tuning, classical evaluation metrics, statistical reliability analysis using conformal prediction, and hallucination detection.

---

# Dataset

The experiments are conducted on the **Yelp dataset**, which is a large-scale dataset describing interactions between users and local businesses.

The dataset contains:

* Business metadata (categories, attributes, location)
* User reviews
* Ratings
* User activity and interaction information

This dataset provides a rich structure for analyzing real-world interactions across multiple domains such as restaurants, services, and retail.

It is particularly suitable for studying:

* Context-aware recommendation systems
* Content-based recommendation approaches
* Hybrid recommendation models

Dataset source:
https://www.kaggle.com/datasets/nguyenhieuxt/processed-yelp-dataset

---

# Data Preprocessing

The preprocessing stage prepares the Yelp dataset for training and evaluation.

The main steps include:

* Cleaning and filtering the dataset
* Handling missing or inconsistent values
* Selecting relevant attributes
* Structuring review data and user interactions
* Preparing contextual inputs for recommendation tasks

Because Yelp reviews are often long and detailed, an additional preprocessing step is introduced: **review summarization**.

---

# Review Summarization

To reduce noise and improve model efficiency, user reviews are summarized using a transformer-based summarization model.

The model used for summarization is:

facebook/bart-large-cnn

This model generates concise summaries that capture the main opinions expressed in the review while preserving the semantic meaning.

The summarized reviews are then used as inputs for the recommendation pipeline.

This step helps:

* Reduce input length
* Focus on essential information
* Improve the quality of contextual signals

---

# Prompt Construction

Similar to the Amazon Books experiments, the processed dataset is converted into an **instruction-style prompt format**.

Each instance contains:

Input:

* Review summary
* Business context information
* Optional user interaction history

Output:

* Predicted rating

Two experimental configurations are considered:

* With user history
* Without user history

---

# Model Fine-Tuning

The recommendation model is based on **Mistral-7B**, which is fine-tuned using the processed Yelp dataset.

Training configuration includes:

* Instruction tuning format
* Hyperparameter optimization
* Two training epochs
* Parameter-efficient fine-tuning

The objective is to enable the model to learn relationships between textual opinions and user ratings.

---

# Model Evaluation

The prediction performance is evaluated using standard regression metrics.

Evaluation metrics include:

* RMSE (Root Mean Squared Error)
* MAE (Mean Absolute Error)
* AUC (Area Under the Curve)

These metrics measure the accuracy of the predicted ratings.

---

# Conformal Prediction

To assess the **statistical reliability of predictions**, conformal prediction techniques are applied.

This method allows the construction of prediction intervals with statistical guarantees, helping to quantify the uncertainty associated with model outputs.

The evaluation is conducted under both experimental settings:

* With user history
* Without user history

---

# Hallucination Detection

To ensure the reliability of model predictions, hallucination detection mechanisms are applied.

Two types of hallucinations are analyzed:

### Syntactic hallucinations

These refer to structural inconsistencies in generated outputs.

### Uncertainty-based hallucinations

These identify predictions that show high levels of uncertainty or instability.

---

# Semantic Verification using LLM as a Judge

To further evaluate prediction quality, a second LLM is used as an evaluator.

The judge model evaluates whether the predicted rating is semantically consistent with the review summary and contextual information.

For each prediction, the judge produces:

* Coherence score
* Verdict
* Explanation

This approach provides an additional layer of validation for recommendation predictions.

---

# Visualization and Analysis

The experimental results are analyzed through several visualizations, including:

* Prediction error distributions
* Performance comparisons
* Hallucination statistics
* Semantic coherence analysis

These visualizations help better understand the behavior and reliability of the model.

---

# Research Objective

The main objective of this project is to investigate how Large Language Models can leverage **contextual and text-rich datasets** such as Yelp to improve rating prediction and recommendation performance.

The study particularly focuses on:

* Exploiting review text through summarization
* Understanding the impact of contextual information
* Evaluating prediction reliability through conformal prediction
* Detecting hallucinations in LLM outputs
* Using LLMs as semantic judges for model validation

---

# Author

Master Research Project
Computer Science
