📘 Retrieval-Augmented Generation (RAG) Pipeline on AWS

This project implements a complete Retrieval-Augmented Generation (RAG) workflow using Amazon Bedrock, AWS Glue, Amazon OpenSearch Service, Amazon DynamoDB, and Amazon S3.
The goal is to build a scalable, secure, and production-ready architecture that extracts knowledge from documents and allows LLMs to answer questions using that knowledge.

🏗️ Architecture Overview

🔹 Components
1. Amazon S3 (Document Storage)

All input documents—PDFs, text files, Word files, reports—are stored in an S3 bucket.
This acts as the central storage for the entire knowledge ingestion pipeline.

2. AWS Glue (ETL Jobs)

AWS Glue jobs perform:

Document extraction

Text parsing

Chunking/splitting

Preprocessing (cleaning, formatting)

The output is ready for vector embedding generation.

3. Amazon Bedrock (Embeddings)

Processed chunks from Glue are passed to Amazon Bedrock’s embedding model.
Bedrock transforms each document chunk into a numerical vector representation.

4. Vector Store

Vector embeddings and metadata are stored in:

Amazon OpenSearch Service — for vector similarity search

Amazon DynamoDB — for metadata indexing and fast key-value lookups

This forms the knowledge base that powers retrieval.

5. Amazon Bedrock (LLM – Llama3)

A Bedrock-hosted LLM generates accurate responses based on:

User query

Retrieved context from the vector store

This enables high-quality Retrieval-Augmented Generation.

🚀 End-to-End Workflow

Upload documents to Amazon S3.

AWS Glue extracts and preprocesses the text.

Clean chunks are sent to Amazon Bedrock Embeddings.

Generated vectors are stored in OpenSearch alongside metadata in DynamoDB.

User submits a query.

System retrieves semantically similar document chunks from OpenSearch.

Retrieved context is fed to Bedrock LLM (Llama3).

The LLM generates a final grounded answer.

🧩 Features

🔹 End-to-end serverless ingestion

🔹 Highly scalable vector search engine

🔹 Fast and reliable metadata indexing

🔹 Bedrock-powered embeddings and LLM reasoning

🔹 Suitable for enterprise knowledge bases and AI search applications

📦 Tech Stack
Layer	Service
Storage	Amazon S3
ETL	AWS Glue
Embeddings	Amazon Bedrock
Vector Search	Amazon OpenSearch Service
Metadata DB	DynamoDB
LLM	Amazon Bedrock (Llama3 or other models)
