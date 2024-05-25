# Deep Neural Network Classification of CAA Status

## Team 9: Enrique Chimal Juarez, Hyder Basha Shaik & Rashed Doha
### Fall 2023

## Table of Contents
1. [Introduction](#introduction)
2. [Problem Description](#problem-description)
3. [Dataset Description](#dataset-description)
4. [Methodology](#methodology)
5. [Results](#results)
6. [References](#references)
7. [Appendix](#appendix)

## Introduction
Alzheimer’s Disease (AD) stands as the most prevalent form of dementia, posing a profound impact on the lives of millions. Its pathophysiology is linked to the accumulation and spread of extracellular ß-amyloid and intracellular Tau Neuro Fibrillary Tangles (NFTs) that lead to synaptic loss and neuroinflammation [1-2]. These pathological hallmarks are not confined solely to AD; they extend to other forms of neurodegenerative disorders, highlighting the complex interplay between molecular mechanisms and disease progression.

The deposition and accumulation of proteins in neurodegeneration can be either parenchymal or vascular; the deposition of amyloid in the vasculature of the brain is categorized as Cerebral Amyloid Angiopathy (CAA). While keeping a close molecular relationship to AD, CAA remains clinically distinct [3]. This complex environment presents a unique challenge in both diagnostics and treatment.

## Problem Description
Given the complexity and heterogeneity of AD and cerebrovascular processes, no single protein is likely to be predictive of all mechanisms or phenotypes which lead to neurodegeneration and cognitive symptoms [8]. Extracting meaningful or key features from complex transcriptomic data remains a challenge. Deep learning and training of an unsupervised deep autoencoder could be used to reduce the dimensionality and complexity of transcriptomic data and extract features to help predict complex biological and pathological behavior such as cancer [9] or in this case, accumulation of amyloid in the cerebrovasculature.

## Dataset Description
This project will use two datasets:

1. **Spatial Transcriptomics NanoString GeoMx Human Whole Transcriptome Atlas:** This dataset measures over 18,000 protein-coding genes for user-defined regions of interest (ROI) from a tissue section. Paraffin brain sections of 4 patients with mixed AD/CAA pathology will be stained with DAPI to visualize the nucleus, GFAP to visualize astrocytes, and anti-Aβ antibody to visualize amyloid. The total ROI collected were 20 ROI of CAA and 15 ROI of Vascular free. These ROI were sequenced at the IU Center for Medical Genomics.

2. **Mayo Clinic AD-CAA (MC-CAA) study:** A subset of 75 patients of this databank will be used (32 AD/CAA+, 43 AD/CAA-; Male:Female ratio 39:36). Bulk RNA sequencing from the temporal cortex will be obtained from the AD knowledge portal.

Both datasets were preprocessed and normalized before any subsequent processing.

## Methodology
Both datasets were filtered and 3Q Normalized. The Autoencoder and the DNN were coded on Python 3.7 using TensorFlow and Keras framework. Transcriptome expression was scaled between zero and one before being fed into the autoencoder. Data preprocessing scripts used scikit-learn 1.3.2.

Network construction and model training:
- Autoencoder: Constructed with 5 encoder levels, 5 decoder levels, including activation function: tanh; and batch normalization; iterations: 200; batch size: 128; optimization algorithm: Adam; loss: MSE.
- DNN Classifier: Built with 5 hidden layers, iterations: 200; batch size: 36; optimization algorithm: Adam; learning rate: 1e-3; loss: MSE; L1 regularization: 0.001 (layer 2), 0.01 (layer 5); L2 regularization: 0.05 (layer 2), 0.001 (layer 5).

## Results
The Deep autoencoder allowed us to embed gene transcription into a 32-dimensional vector. The designed DNN correctly identified 95% of the training set and 95% of the testing set. To validate the findings, a subset of a publicly available dataset, the Mayo Clinic CAA-AD dataset, was used. The evaluation yielded a 55% accuracy of prediction of CAA. 

## References
[1] Karch CM, Cruchaga C, Goate AM. Alzheimer’s disease genetics: from the bench to the clinic. Neuron. 2014;83(1):11–26.
[2] Citron M. Alzheimer’s disease: strategies for disease modification. Nat Rev Drug Discov. 2010;9(5):387–98.
[3] Biffi A, Greenberg SM (2011) Cerebral amyloid angiopathy: a systematic review. J Clin Neurol 7:1–9.

## Appendix
Contributions from each member:
- E.C.J. built the deep learning model and conducted the analysis.
- E.C.J. and R.D. wrote the report.
- E.C.J. and H.B.S performed the data preprocessing.
- E.C.J. and R.D. optimized the hyperparameters on the whole project.

