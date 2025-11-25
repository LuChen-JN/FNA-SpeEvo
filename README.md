## Introduction
A deep learning model for predicting interactions between nucleic acids and small molecules

## System Requirements
This model is supported for any standard computer and operating system (Windows/macOS/Linux) with enough RAM to run. 
The source code developed in Python 3.6.13 using PyTorch 1.10.2. The required python dependencies are given below. 
To avoid conflicts between the various python packages, we recommend using the following versions of packages：
```
torch = 1.10.2
dgllife = 0.3.2
numpy = 1.19.2
scikit-learn = 0.24.2
pandas = 1.2.4
rdkit = 2020.09.1.0
matplotlib = 3.3.4
```

## Data Sources
Our data contain aptamer and riboswitch datasets. For aptamers, the data were collected from numerous literature collections and websites, including the following websites involved in the article:
1. https://www.aptamer.org/
