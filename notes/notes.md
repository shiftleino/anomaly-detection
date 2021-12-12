# Anomaly Detection
Anomaly detection is the process of identifying for example data points in a dataset that differ from the norm.
There are two assumptions in anomaly detection:
1. Anomalies occur very rarely in the data.
2. The features of anomalies differ from the normal instances significantly.

## Statistical Approaches
One does not necessarily need machine learning methods to detect anomalies as there are some statistical methods for this. For example in Interquartile Range (IQR) the data points that are located before Q1 - 1.5 * IQR and after Q3 + 1.5 * IQR are considered outliers. 

## Machine Learning Algorithms

### Isolation Forest
One algorithm for anomaly detection in univariate data is Isolation Forest, which is a supervised learning algorithm. The Isolation Forest model is a tree-based model, which builds a Random Forest in which each decision tree is grown randomly. The anomalies are isolated in fewer steps than the normal values as they are usually far from the other data points. This algorithm should be used for dense high-dimensional data.

```console
from sklearn.ensemble import IsolationForest
```

### Cluster-based Local Outlier Factor (CBLOF)
Calculates an anomaly score for each data point from the distance of the point to its cluster center multiplied by the data points belonging to that cluster. The algorithm is based on the assumption that the anomalies are located in low density areas and it compares a certain point's density with the density of k its nearest neighbours. 

```console
from pyod.models.cblof import CBLOF
```

### Histogram-based Outlier Detection (HBOS)
This algorithm calculates the degree of anomalies by building histograms.

```console
from pyod.models.hbos import HBOS
```

### k - Nearest Neighbours (kNN)
Coming soon...

### Support Vector Machines (SVM)
Coming soon...

### Density-based spatial clustering of applications with noise (DBSCAN)
Coming soon...

## Anomaly Detection in Time Series Analysis

### Anomaly Detection with Seasonal-Trend decomposition
In time series analysis anomalies can be detected for example by using the Seasonal-Trend decomposition. In Seasonal-Trend decomposition the time series is split into three parts: seasonal, trend and residual part. This can be done for example by using LOESS (locally estimated scatterplot smoothing), which makes the decomposition a STL decomposition. In LOESS we fit lines/parabolas (then points) on windows of the data, give weights based the distance from the original point, thus approximating the data with a fitted curve. STL has many advantages, for example it can handle any type of seasonality, the seasonality can change over time and the user can control the smoothness of the trend-cycle part and the rate of change of seasonality. 

```console
from statsmodels.tsa.seasonal import STL
```
