# RHEL AI + InstructLab POC

This repository contains a Proof-of-Concept (POC) focused on alignment tuning an IBM Granite Large Language Model (LLM) using InstructLab. The goal is to fine-tune the model with publicly available domain-specific data from various industries, enabling it to provide precise and context-aware answers to domain-specific questions.

## Use Case (Mass General Brigham)

### Background

Mass General Brigham (MGB) is a renowned integrated healthcare system based in Massachusetts, United States. It was formerly known as Partners HealthCare and includes prestigious institutions like Massachusetts General Hospital (MGH) and Brigham and Women’s Hospital. The network comprises a wide range of hospitals, community health centers, research facilities, and specialty practices.
MGB is known for its leadership in healthcare innovation, cutting-edge research, and clinical excellence. It is a major hub for medical research, with robust partnerships in academia and significant contributions to medical advancements. The system focuses on delivering comprehensive, patient-centered care and advancing healthcare through initiatives in artificial intelligence, digital health, and precision medicine.

### Justification

In a discovery conversation with a healthcare innovation lead at Mass General Brigham (MGB), the AI solutions team learned that MGB seeks to improve patient care and operational efficiency by enhancing their chatbot capabilities. The chatbot is intended to provide accurate and timely responses to patient queries, ranging from appointment scheduling and medication guidance to complex questions about healthcare services and medical conditions.

## Objective

Given the vast and specialized knowledge base within MGB, implementing a Retrieval-Augmented Generation (RAG) model in addition to a fine tuned model is a strategic fit. It will combine the strengths of large language models (LLMs) with domain-specific knowledge retrieval, ensuring that the chatbot provides accurate, contextually relevant answers backed by MGB’s trusted healthcare resources.

The primary objective of this POC is to:

- Fine-tune an LLM to enhance its domain-specific knowledge.
- Leverage InstructLab and IBM Granite to build a chatbot capable of understanding and responding to specialized queries across different industries.

## Data Scope

The data utilized for this POC includes publicly available information across multiple verticals, such as:

- Healthcare
- Automotive
- Finance
- Other relevant industries

## Data Formats

The public data used in this POC may be published in various formats, including:

- PDFs
- DOCX files
- Other structured and unstructured document formats

## Approach

### 1. Data Collection and Preprocessing

- **Document Transformation**:  
  Use `docling` to transform raw data into Markdown format for consistent processing.

- **Chunking and Taxonomy Creation:**  
  Split large documents into smaller, manageable chunks and generate taxonomy files with seed data. These taxonomies will serve as the foundation for generating synthetic data to enrich the training datasets.

- **Preprocessing Pipeline:**  
  Text extraction from source formats (PDFs, DOCX, etc.).  
  Organizing content into domain-specific categories.

### 2. Alignment Tuning

- Use InstructLab for alignment tuning of the IBM Granite LLM.
- Ensure the model adapts to industry-specific terminologies and contexts.
- Optimize the model for high accuracy and relevance in answering domain-specific questions.

### 4. Chatbot Implementation

- Build a chatbot interface that utilizes the fine-tuned model.
- Enable seamless querying for users, providing precise and contextual answers.

## Feedback

- Creating qna.yaml manually can lead to errors (e.g., indentation, whitespaces). A tool or UI that accepts questions and answers to generate a properly formatted qna.yaml would be beneficial.
- Make validation rules (e.g., performed by ilab taxonomy diff) more explicit and user-friendly.
- Provide clear guidance on handling long contexts and large tables to minimize ambiguity.
- Offer real-time feedback for long-running tasks such as SDG generation and alignment.
- Ensure setup and run instructions are compatible across all platforms (Mac, Windows, Linux).
- Include practical guidelines or rules of thumb for document chunking.
- Break down documentation into smaller, more focused sections instead of a monolithic structure.
- Advise users to delete existing taxonomy folders before performing a new diff to avoid false positives.
- Avoid bulk fetching of documents that triggers multiple calls, as this approach may not scale effectively.
- The strong Git requirement for taxonomy and documents is overly limiting, being able to directly reference local storage or other options would be greatly helpful.
- The IBM Cloud Service should provide taxonomy validation directly, so the full workflow can be completed through the service. Having to set up and install InstructLab locally or remotely just to validate taxonomy before moving to the service leads to an over-complicated experience.

## Status

[ x ] Convert PDF to MD using Docling  
[ x ] Create seed data qna.yaml for MD  
[ x ] Create seed data qna.yaml for PDF  
[ x ] Validate taxonomy  
[ x ] Create synthetic data for both MD  
(knowledge count = 22,619 Skills Count = 413,633)  
[ x ] Create synthetic data for PDF  
(knowledge count = 64,185 Skills Count = 492,403)  
[ x ] Align model (MD and PDF)  
[ x ] Serve model using RHOAI  
[ ] Evaluate model
