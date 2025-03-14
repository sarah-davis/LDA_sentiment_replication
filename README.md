# LDA Sentiment Replication — CMPUT 501 Term Project
By: Sarah Davis and Henry Tang

The objective of this project is to replicate the work published by Onan et al. in 
*LDA-based Topic Modelling in Text Sentiment Classification: An Empirical Analysis* (2016).

## Introduction

This repository contains all the code, instructions, and data for our replication study.
The `data` directory contains the arff files of each dataset and the results of our LDA topic generation.
The `results` directory contains text files of the results from WEKA as well as a xlsx containing all our results.
The instructions for following our WEKA procedure is detailed in this projects [wiki](https://github.com/sarah-davis/LDA_sentiment_replication/wiki/WEKA-instructions).

## Installation and execution

1. Activate virtual environment and install dependencies 
	```bash
    python3 -m venv venv
 
    venv\Scripts\activate.bat  # windows
    source venv/bin/activate  # unix
 
    pip install -r requirements.txt
	```
 
2. Unzip data files
	```bash
    cd data
    tar -xf multi-domain-sentiment.arff.zip
    tar -xf IrishEconomicSentiment.arff.zip
    cd ..
	```
 
3. Create *document x term* .csv from .arff for each dataset
	```bash
    python src\arff_convert.py data\multi-domain-sentiment.arff data\multidomain_df.csv
    python src\arff_convert.py data\IrishEconomicSentiment.arff data\irish_df.csv
	```
 
4. Generate LDA topics for each dataset
	```bash
    mkdir models
 
    python src\lda.py data\multidomain_df.csv data\multidomain_topics.csv models\multidomain_model.pkl
    python src\lda.py data\irish_df.csv data\irish_topics.csv models\irish_model.pkl
	```
 
5. Convert .csv files to .arff files
	```bash
    csv2arff data\multidomain_topics.csv data\multidomain_topics.arff
    csv2arff data\irish_topics.csv data\irish_topics.arff
	```

6. Upload data to WEKA, train models. WEKA instructions for this project is available in this projects [wiki](https://github.com/sarah-davis/LDA_sentiment_replication/wiki/WEKA-instructions).

 ## Data
 
 http://sites.labic.icmc.usp.br/text_collections/