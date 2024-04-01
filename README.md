# Retina Disease Classification Chatbot (WIP)

## About 
The Retina Disease Classification Chatbot is an innovative tool designed to assist in the early detection and diagnosis of retinal diseases. 

The World Health Organization's 2019 World Report on Vision estimates that there are 2.2 billion visually impaired persons in the globe, at least 1 billion of whom have untreated or preventable vision impairments. When it comes to eye care, the globe has many obstacles, such as disparities in access to and the standard of preventive, treatment, and rehabilitation services. Visual impairment may be prevented if ocular disorders were identified and diagnosed early.

As an enthusiast of Computer Vision and Natural Language Processing, I am building this project as it applies a combination of CV and NLP principles.

## Key Features
- **Retinal Disease Image Classification**: Utilizes a state-of-the-art CV model to analyze retinal fundus images and identify potential diseases.
- **Interactive Chatbot**: Employs NLP to converse with users, assess symptoms, and provide personalized recommendations.
- **Integration of CV and NLP**: Combines image classification with conversational AI for a comprehensive diagnostic tool.
- **User-Friendly Interface**: Designed for ease of use, allowing users to upload images and interact with the chatbot seamlessly.

## Project Status
**Currently working on building dataset to train chatbot**
 - [x] Retinal Disease Classification - CV
	 - [ ] Hyperparameter tuning
	 - [ ] Use larger dataset
	 - [ ] Try other models
 - [ ] Chatbot - NLP
	 - [ ] Build retinal dataset
	 - [ ] Train Model
		 - [ ] Question Answering + RAG Approach
		 - [ ] Chatbot + RAG Approach 
 - [ ] Implement chatbot using Flask
 - [ ] Deploy application 

## Details
   
There are two main aspects to the project: the Retinal Disease Image Classification and the Chatbot. After I complete both aspects, I will integrate the Image Classification Model and Chatbot using a user interface that allows users to upload retinal disease images and interact with the chatbot. 

### Chatbot - NLP

#### Dataset
To effectively train the chatbot, I need a high-quality medical dataset that includes retinal disease information, symptoms, diagnosis methods, treatment options, and follow-up procedures. Unfortunately, no such dataset exists to my knowledge.  Therefore, I will collect and create comprehensive dataset from reputable sources such as medical journals, textbooks, and online medical databases.

#### Model
There are two conversational AI approaches that interact with users through natural language processing: **Question Answering Bot** and **Chatbot**. Both have their individual use cases, advantages and disadvantages, so I wish to try both approaches. 

 - Purpose
	 - QA Bot: Provide precise answers to specific questions based on the available knowledge base
	 - Chatbot: Designed for interactive conversations with users. They engage in more extended exchanges, addressing a variety of user queries, and often have a broader scope beyond factual answers.
 - Interaction Style
	 - QA Bot: Focused on giving concise and accurate answers to specific questions. 
	 - Chatbot: Focused on maintaining conversational flows and engaging users in dialogue.
- Knowledge Base
	- QA Bot: Rely on a structured or unstructured knowledge base, from which they extract information to answer questions accurately.
	- Chatbot: May have a broader scope of knowledge and can handle a wide range of topics, often relying on scripted responses or machine learning models trained on diverse datasets.

**Chatbot Approach**

In this approach, I will build a chatbot. The idea is to build a LLM-powered chatbot architecture using retrieval augmented generation (RAG) as seen below. 

![Chatbot](https://truera.com/wp-content/uploads/2023/09/truera-architecture-for-chatot-figure-1.png)

 1. Data Preparation - With Pinecone
	- As mentioned above, comprehensive dataset of medical literature, research papers, and clinical guidelines specifically related to retinal diseases will be used
	- This dataset would be preprocessed and indexed using a combination of vector indexing (for semantic search) and text indexing (for exact matching) to enable efficient retrieval
 2. [OPTIONAL] Image Classification
	 - If the user uploads an image, it is passed through the image classification model, which predicts possible diseases.
 3. Retrieval - Using LangChain
	 - When a user asks a question (or using the output of the classification model), the chatbot's retrieval system would first generate an embedding vector for the user's query
	 - The system will use this query to perform a semantic search and a full-text search against the dataset, retrieving the most relevant documents
4. Fine-tuning the LLM - BERT/GPT4
	-  The LLM will be fine-tuned on the specific dataset of retinal disease information to improve its performance
5. Generation	
	- The LLM is fed the query along with the relevant retrieved documents, allowing the LLM to generate a response information from the retrieval system
	
**Question Answering Bot Approach**

In this approach, I will build a Question Answering bot. 

### Retinal Disease Image Classification - CV

#### Dataset
The dataset Retinal Disease Classification can be found at [Retinal Disease Image Classification](https://www.kaggle.com/datasets/andrewmvd/retinal-disease-classification). The Retinal Fundus Multi-disease Image Dataset (RFMiD) consists of a total of 3200 fundus images captured using three different fundus cameras with 46 conditions (45 retinal diseases and 1 healthy retina class) annotated through adjudicated consensus of two senior retinal experts.

#### Model
The model used is a ResNext50 network. 

#### Metrics
Metrics include accuracy, f1-score, precision and recall. However, since we are mainly concerned with limiting False Negatives, we will prioritize recall.

## Results

## Next Steps

## Acknowledgments

- [Chatbot with RAG](https://blog.gopenai.com/system-design-of-an-llm-based-chatbot-application-for-an-educational-consultancy-agency-9da74088da48)
