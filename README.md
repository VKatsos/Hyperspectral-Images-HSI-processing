# Hyperspectral Image (HSI) Processing: Spectral Unmixing and Classification

This project explores the application of various spectral unmixing and classification techniques on the **Salinas** Hyperspectral Image (HSI). The dataset contains 7 distinct endmembers, each representing a different material. The primary goal is to perform pixel-wise spectral unmixing and classify each pixel into its respective material class, using multiple algorithms for both tasks. Additionally, we investigate correlations between the results obtained from unmixing and classification.

## Table of Contents

- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Part 1: Spectral Unmixing](#part-1-spectral-unmixing)
  - [Unmixing Methods](#unmixing-methods)
  - [Abundance Maps and Reconstruction Error](#abundance-maps-and-reconstruction-error)
- [Part 2: Classification](#part-2-classification)
  - [Classification Methods](#classification-methods)
  - [Cross-Validation and Confusion Matrix](#cross-validation-and-confusion-matrix)
- [Part 3: Results Correlation](#part-3-results-correlation)
- [Installation and Usage](#installation-and-usage)
- [Dependencies](#dependencies)
- [License](#license)

## Dataset

The **Salinas** HSI dataset contains pixel-wise spectral data along with ground truth labels for seven endmembers, which correspond to different materials (or types of cultivation) as described below:

| Endmember | Material  |
|-----------|-----------|
| 1         | Grapes    |
| 2         | Broccoli  |
| 3         | Fallow 1  |
| 4         | Fallow 2  |
| 5         | Fallow 3  |
| 6         | Stubble   |
| 7         | Celery    |

## Project Structure

This project is divided into three main parts:

1. **Spectral Unmixing:** Deriving abundance maps for each pixel with respect to the 7 endmembers.
2. **Classification:** Assigning each pixel to the most appropriate class using different classifiers.
3. **Results Correlation:** Analyzing the correlation between the results from unmixing and classification.

## Part 1: Spectral Unmixing

### Unmixing Methods

We aim to decompose each pixel in the image (with nonzero labels) into a mixture of the 7 endmembers using the following methods:

1. **Least Squares:** Basic unmixing using least squares.
2. **Sum-to-One Constraint:** Least squares with the additional constraint that the abundances sum to 1.
3. **Non-Negativity Constraint:** Least squares with non-negative abundance coefficients.
4. **Non-Negativity and Sum-to-One Constraints:** Combines both constraints in the least squares method.
5. **LASSO (L1 Norm Minimization):** Introduces sparsity in the abundance map via L1 norm regularization.

### Abundance Maps and Reconstruction Error

For each unmixing method, we derive 7 abundance maps, corresponding to each endmember, and compute the reconstruction error for each pixel. The reconstruction error is defined as:

\[
\text{Reconstruction Error} = ||𝒚𝑖− 𝑿𝜽𝑖||^2
\]

where \( \theta_i \) is the abundance vector for pixel \( y_i \), and X is the matrix of endmembers.

We then compare the methods based on the abundance maps and average reconstruction error.

## Part 2: Classification

### Classification Methods

The task in this part is to classify pixels with nonzero labels into one of the seven classes, using four different classifiers:

1. **Naïve Bayes Classifier**
2. **Minimum Euclidean Distance Classifier**
3. **k-Nearest Neighbor (k-NN) Classifier**
4. **Bayesian Classifier**

### Cross-Validation and Confusion Matrix

For each classifier:

1. Perform **10-fold cross-validation** to train the model and report the mean validation error along with the standard deviation.
2. Train the classifier on the entire training set and evaluate it on the test set by computing the **confusion matrix** and **success rate**. The confusion matrix helps to identify classes that are not well-separated by the classifier.

## Part 3: Results Correlation

In this section, we investigate any correlation between the results obtained from spectral unmixing and those from classification. This includes comparing how well the abundance maps align with the classification outcomes and identifying patterns in the confusion matrix.

## Installation and Usage

### Installation

To run this project locally, follow these steps:

## Clone the repository:
    ```bash
    git clone https://github.com/your-username/hsi-unmixing-classification.git
    cd hsi-unmixing-classification
    ```


## License

This project is licensed under the MIT License.
