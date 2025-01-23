# RHEL AI + InstructLab POC (MGB)

This repository contains a Proof-of-Concept (POC) focused on alignment tuning an IBM Granite Large Language Model (LLM) using InstructLab. The goal is to fine-tune the model with publicly available domain-specific data from various industries, enabling it to provide precise and context-aware answers to domain-specific questions.

## Objective

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
