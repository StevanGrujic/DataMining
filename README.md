# Change Point Detection in Environmental Data

## Overview

This project focuses on detecting change points within environmental data collected from sensors in a factory setting. Change point detection (CPD) is a crucial technique in time series analysis, aiming to identify moments when the statistical properties of data change significantly. This project employs various algorithms, particularly those implemented in the `ruptures` library, to analyze univariate and multivariate time series data, providing insights into the dynamic changes within the factory environment.

## Project Structure

1. **Introduction**
   - Basics of Change Point Detection
   - Offline and Online Detection Approaches
   - Overview of the Ruptures Library

2. **Practical Implementation**
   - Dataset Overview
   - Algorithms for Change Point Detection
   - Data Analysis Workflow

3. **Results**
   - Univariate Change Point Detection
   - Multivariate Change Point Detection
   - Comparative Analysis of Algorithms

4. **Conclusion**

## 1. Introduction

### Basics of Change Point Detection

Change point detection (CPD) involves identifying moments in time series data where statistical properties such as mean, variance, or correlation change significantly. This technique is vital across various fields, including industry, economics, medicine, and telecommunications, allowing for deeper understanding of processes, anomaly detection, and system optimization.

### Offline and Online Detection Approaches

CPD algorithms can be classified as "online" or "offline." Online algorithms detect changes in real-time, while offline algorithms analyze data after collection, providing more in-depth insights. This project focuses exclusively on offline detection.

### Overview of the Ruptures Library

The `ruptures` library is a powerful tool for CPD, offering a range of algorithms for both univariate and multivariate time series analysis. It supports various methods like PELT, BinSeg, and BottomUp, making it a popular choice for researchers.

## 2. Practical Implementation

### Dataset Overview

The dataset, named "Environmental data," consists of time series data recorded over four days with a one-second sampling rate. The data was collected from sensors placed inside a factory room, capturing the following attributes:

- **timestamp**: Precise moment when data was recorded.
- **sound**: Noise level in decibels.
- **pressure**: Atmospheric pressure in hectopascals.
- **temp**: Air temperature in Celsius.
- **humidity**: Relative humidity in percentage.
- **voc**: Volatile organic compounds in parts per million (ppm).
- **pm1.0, pm2.5, pm10**: Particle counts for various sizes per cubic meter.
- **CO2**: Carbon dioxide concentration in ppm.

### Algorithms for Change Point Detection

Three algorithms from the `ruptures` library were utilized for detecting change points in this project:

1. **PELT (Pruned Exact Linear Time)**: Efficient in detecting change points by minimizing a cost function with an added penalty for introducing new change points.
2. **BinSeg (Binary Segmentation)**: Sequentially identifies change points by dividing the signal into two segments and repeating the process.
3. **BottomUp**: Starts with many change points and gradually merges segments based on similarity.

### Data Analysis Workflow

#### Data Visualization

Initial data exploration included examining basic statistics, visualizing daily patterns, and checking data distribution and correlation. Key findings included non-normal data distributions and high correlations among certain attributes, leading to attribute reduction via PCA.

#### Data Preprocessing

The preprocessing steps included handling missing data through interpolation, removing duplicates, resampling the data to a 1Hz frequency, and outlier detection using the IQR method. PCA was used to combine highly correlated attributes into a single attribute, followed by standardization.

## 3. Results

### Univariate Change Point Detection

The univariate analysis focused on detecting change points in individual attributes using the PELT and BinSeg algorithms. The "elbow method" was applied to determine the optimal penalty value for the PELT algorithm. Magnitudes of detected change points were calculated to assess the significance of changes.

### Multivariate Change Point Detection

For multivariate analysis, the goal was to detect change points common across all attributes. The Euclidean distance between vectors before and after change points was used to evaluate the significance of changes. The PELT algorithm performed the best in this scenario.

### Comparative Analysis of Algorithms

The final comparison of algorithms (PELT, BinSeg, BottomUp) was based on metrics such as mean distance, median distance, and standard deviation of detected change points. PELT was found to be the most consistent and accurate across both univariate and multivariate analyses.

## 4. Conclusion

This project provides a comprehensive analysis of environmental data using change point detection techniques. The PELT algorithm emerged as the most effective for detecting significant changes in the data. The results include the creation of a new CSV file containing timestamps and corresponding change point indicators, which can be used for further analysis.

## References

- An Evaluation of Change Point Detection Algorithms by Gerrit J. J. van den Burg, Christopher K. I. Williams
- A survey of methods for time series change point by Samaneh Aminikhanghahi, Diane J. Cook
- Ruptures Documentation: [Ruptures GitHub](https://github.com/deepcharles/ruptures/tree/master/docs)
