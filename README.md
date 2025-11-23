# Retrieval-Augmented Generation (RAG) Pipeline on AWS

This project implements a complete Retrieval-Augmented Generation (RAG) workflow using Amazon Bedrock, AWS Glue, Amazon OpenSearch Service, Amazon DynamoDB, and Amazon S3.  
The system extracts knowledge from documents and enables LLMs to answer questions using that knowledge.

---

## 📘 Architecture Overview

![Architecture Diagram](./Blank%20diagram.png)

### Components

#### 1. Amazon S3 (Document Storage)
Stores all raw documents (PDF, TXT, DOCX, reports, etc.).  
Acts as the central repository for ingestion.

#### 2. AWS Glue (ETL Jobs)
Responsible for:
- Extracting text  
- Cleaning and preprocessing  
- Chunking documents  
- Preparing data for embeddings  

#### 3. Amazon Bedrock (Embeddings)
Uses Bedrock embedding models to convert document chunks into vector representations.

#### 4. Vector Store
The generated embeddings and metadata are stored in:

- **Amazon OpenSearch Service** – Vector similarity search  
- **Amazon DynamoDB** – Metadata and fast index lookup  

Together these form the retrieval layer.

#### 5. Amazon Bedrock (LLM – Llama3)
The Large Language Model (LLM) generates final answers using:
- User query  
- Retrieved chunks from OpenSearch  

This creates a grounded and accurate response using RAG.

---

## 🚀 End-to-End Workflow

1. Upload documents to **Amazon S3**.  
2. **AWS Glue** extracts and preprocesses the text.  
3. Bedrock generates embeddings for each text chunk.  
4. Embeddings + metadata stored in **OpenSearch** + **DynamoDB**.  
5. User submits a query.  
6. Relevant chunks are retrieved using similarity search.  
7. Context + query is sent to Bedrock LLM.  
8. A final answer is generated using RAG.

---

## 🧩 Features

- Fully serverless ingestion pipeline  
- Scalable vector search using OpenSearch  
- Bedrock-powered embeddings & LLMs  
- DynamoDB for fast metadata lookup  
- Suitable for enterprise knowledge bases, chatbots, and AI search systems  

---

## 🛠️ Tech Stack

| Component | Service |
|----------|---------|
| Document Storage | Amazon S3 |
| ETL Processing | AWS Glue |
| Embedding Model | Amazon Bedrock |
| Vector Search | Amazon OpenSearch Service |
| Metadata Storage | DynamoDB |
| LLM | Amazon Bedrock (Llama3 or others) |

---
