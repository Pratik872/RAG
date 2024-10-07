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

![Sample images](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/sample_images_embeds.png)

The embeddings have 512 dimensions and so I have used UMAP to project into 2 dimensions to visualize it

![UMAP](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/embeds_UMAP.png)

- The embeddings of image-text pairs of `cats` (i.e., blue dots) are
closed to each other.
- The embeddings of image-text pairs of `cars` (i.e., orange dots) are
closed to each other.
- The embeddings of image-text pairs of `cats` (blue dots) are far away
from the embeddings of image-text pairs of `cars` (orange dots).


### Preprocessing Videos


### Vector Store - Ingesting and Retrieval


### Large Vision-Language model for completion


### Working of Application


### Built with 🛠️
- Packages/Repo : Pandas,Numpy,Seaborn,Matplotlib,Sklearn,Flask,Pickle,Git

- Dataset : Kaggle

- Coded on : Jupter Notebook (modelling), VSCode(building application)
