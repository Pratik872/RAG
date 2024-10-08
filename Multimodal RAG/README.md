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

![MultiModal RAG Flow](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/Multimodal_RAG_Flow.png)

The RAG Framework involves:
- Preprocessing videos/images for passing into framework

- Computing the joint embeddings of images/videos and captions and ingesting them into vector store

- Passing a query from user to the framework and augmenting the query using the video transcripts

- Using a Large Vision-Language Model to get inference and chat completion

### 1 - Computing Embeddings

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


### 2 - Preprocessing Videos

- Videos were downloaded from Youtube along with the transcripts. For the videos which didn't have transcripts were generated using 'Whisper' model.

- For videos without language, LVLM model was used to generate captions which were then passed as an query.

- For each video segment, we will extract:
    1. A frame right at the middle of the time frame of the video segment;
    2. Its metadata including:
        -extracted_frame_path: Path to the saved extracted-frame;
        -transcript: Transcript of the extracted frame;
        -video_segment_id: The order of video segment from which the frame was extracted;
        -video_path: Path to the video from which the frame was extracted; This helps to retrieve the correct video when there are many ones in your video corpus;
        -mid_time_ms: Time stamp (in ms) of the extracted frame

- Here is the sample generated caption for an image
 ![video_preprocess](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/video_preprocess.png)


### 3 - Vector Store - Ingesting and Retrieval
![vector_store](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/vector_stores.png)

- LanceDB (as retreiever) and Langchain was used to store the embeddings for the metadata.

- Top 'k' results were retrieved. Below are the sample quesry and results for top 3.
        Query - "a toddler and an adult"

        ![1](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/1.png)
        ![2](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/2.png)
        ![3](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/3.png)


### 4 - Large Vision-Language model for completion

![LLMvsLVLM](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/LLM%20vs%20LVLM.png)

#### LLaVA (Large Language-and-Vision Assistant) model
![LLaVA](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/LLaVA.png)
- LLaVA , an end-to-end trained large multimodal model that connects a vision encoder and LLM for general-purpose visual and language understanding.

- LLaVA doesn't just see images but understands them, reads the text embedded in them, and reasons about their context—all while conversing with you in a way that feels almost natural.


### 5 - Working of Application

- ![sample1](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/working1.png)
- ![sample2](https://github.com/Pratik872/RAG/blob/main/Multimodal%20RAG/images/working2.png)


### Built with 🛠️
- Packages/Repo : Langchain, Jupyter, LanceDB, Gradio

- Coded on : Jupter Notebook (modelling), VSCode(building application)
