# Uncertainty-Aware Vibration-Based Fault Diagnosis for Electric Motors Using Conformal Prediction

This repository contains the results of the split conformal prediction for uncertainty quantification in vibration-based electric motor fault diagnosis.

## Research Objectives

- Evaluate machine learning models for vibration-based electric motor fault classification.
- Compare statistical time-domain features with FFT-based frequency-domain representations combined with PCA.
- Investigate the application of Split Conformal Prediction to multiclass fault diagnosis.
- Assess empirical coverage, coverage error, and prediction set size at different target confidence levels.
- Examine the trade-offs between classification performance and uncertainty quantification.

## Methodology

The experimental pipeline consists of the following stages:

**1. Signal preprocessing**

Vibration measurements are segmented into fixed-length windows with overlap to construct samples for feature extraction and classification.

**2. Feature extraction**

Two feature representations are considered:

- **Statistical features:** Time-domain descriptive and signal characteristics extracted from the three vibration axes.
- **FFT + PCA:** Frequency-domain representations derived from the Fast Fourier Transform, followed by dimensionality reduction using Principal Component Analysis.

**3. Classification**

Three conventional machine learning algorithms are evaluated:

- Support Vector Machine (SVM) with an RBF kernel
- Random Forest (RF)
- Extreme Gradient Boosting (XGBoost)

**4. Uncertainty quantification**

Split Conformal Prediction is applied to the trained classifiers to construct prediction sets for unseen samples. The resulting sets may contain one or more candidate fault classes, depending on the conformity scores and selected significance level.

**5. Evaluation**

Classification metrics and conformal prediction metrics are used to assess model performance and uncertainty characteristics.

## Experimental Design

The experimental design combines two feature representations with three classifiers, resulting in six model configurations.

| Feature Representation | Classifier |
|---|---|
| Statistical | SVM |
| Statistical | Random Forest |
| Statistical | XGBoost |
| FFT + PCA | SVM |
| FFT + PCA | Random Forest |
| FFT + PCA | XGBoost |

The conformal prediction experiments consider target confidence levels of 80%, 85%, 90%, and 95%.

## Evaluation Metrics

### Classification

Classification performance is assessed using accuracy and, where reported, additional class-wise or aggregate classification metrics.

### Conformal Prediction

- **Empirical Coverage:** The proportion of prediction sets containing the true class label.
- **Coverage Error:** The difference between empirical coverage and the target coverage level.
- **Average Set Size:** The average number of candidate labels in each prediction set.
- **Maximum Set Size:** The maximum number of candidate labels returned for a sample.

These metrics characterize the relationship between the desired coverage level and the informativeness of the resulting prediction sets.

## Dataset

The experiments use the Electric Motor Vibrations Dataset available on Kaggle.

**Source:** [Electric Motor Vibrations Dataset](https://www.kaggle.com/datasets/amirberenji/electric-motor-vibrations-dataset)

The dataset contains vibration measurements along three axes: AccX, AccY, and AccZ. The experimental pipeline processes the signals into windows and extracts the features required for classification.


```

## License

A license will be specified according to the intended terms of use and redistribution of the source code.
