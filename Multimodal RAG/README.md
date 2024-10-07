# Multimodal RAG - Question Answering with multiple modality data

## Overview
- This is a multimodal RAG framework which allows you to chat with the videos through Gradio App.

## Project Structure
- [L2_Multimodal Embeddings.ipynb](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/L2_Multimodal%20Embeddings.ipynb) : Computing multimodal embeddings through 'BridgeTower' open-source model by Intel and Microsoft collaboration.

- [L3_Preprocessing Videos for Multimodal RAG.ipynb](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/L3_Preprocessing%20Videos%20for%20Multimodal%20RAG%20.ipynb) : Preprocessing the videos for passing it to RAG framework.

- [L4_Multimodal Retrieval from Vector Stores.ipynb](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/L4_Multimodal%20Retrieval%20from%20Vector%20Stores.ipynb) : Ingesting data into vector stores and trying to retrieve them with the query.

- [L5_Large Vision-Language Models.ipynb](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/L5_Large%20Vision-Language%20Models.ipynb) : Prompting and Chat Retireval with LLaVa model.

- [L6_Multimodal RAG with Multimodal Langchain.ipynb](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/L6_Multimodal%20RAG%20with%20Multimodal%20Langchain.ipynb) : This notebook collates all the code for the application

## Problem Objective
- To build RAG framework through which you will be able to chat with the videos through a web application.

## Methodology

### EDA (Exploratory Data Analysis) 

![MultiModal RAG Flow](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/Multimodal_RAG_Flow.png)

The RAG Framework involves:
- Preprocessing videos/images for passing into framework

- Computing the joint embeddings of images/videos and captions and ingesting them into vector store

- Passing a query from user to the framework and augmenting the query using the video transcripts

- Using a Large Vision-Language Model to get inference and chat completion

### Computing Embeddings

Here are sample pictures and computation of BridgeTower embeddings

![Sample images](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/Multimodal_RAG_Flow.png)

- I have handled categorical variables i.e nominal ar well as ordinal by using one-hot-encoding and label encoding whereever necessary.

### Feature Selection
- I have used ExtraTreesRegressor for checking feature importances.

- I have also used barplot for visualising them:
![Feature_Imp](https://github.com/Pratik872/ML/blob/main/E2E%20Project/FlightFarePredictor/readme_resources/feature%20importances.png)

### Model Making

- I have built a RandomForestRegressor model with default hyperparameters initially.

- I chose this model just because I thought ensemble model would work better. But you can try different models too.

### Hyper-Parameter Tuning

- I have tuned the hyperparameters 'n_estimators', 'max_depth', 'max_features' by using RandomisedSearchCV. I used  this because this works faster than GridSearchCV.

- I again built a RF model with best hyper-parameters selected from CV.

### Metrics

- I have used 'r2_score' as my metric here. You can use any different metric for regression.

- Further I have plotted and checked error terms also to check whether they are normally distributed around 0.

### DATA SOURCE
- [Flight Fare Dataset](https://www.kaggle.com/nikhilmittal/flight-fare-prediction-mh/)

### Notebook
- [Flight Fare Predictor](https://github.com/Pratik872/ML/blob/main/E2E%20Project/FlightFarePredictor/Flight%20Fare%20Prediction.ipynb)

### Built with 🛠️
- Packages/Repo : Pandas,Numpy,Seaborn,Matplotlib,Sklearn,Flask,Pickle,Git

- Dataset : Kaggle

- Coded on : Jupter Notebook (modelling), VSCode(building application)

### Deployment
- Deployed using Heroku(PAAS)

- For deployment repository click [here](https://github.com/Pratik872/ML/tree/deployFlight)

- For Web Application click [here](https://flight-fare-deploy.herokuapp.com/)
