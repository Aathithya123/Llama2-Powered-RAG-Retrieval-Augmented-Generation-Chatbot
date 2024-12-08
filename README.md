# Llama2-Powered-RAG-Retrieval-Augmented-Generation-Chatbot
This project demonstrates a pipeline for building a Retrieval-Augmented Generation (RAG) system powered by LLaMA 2 for knowledge extraction from a PDF book on human nutrition. The system allows users to query specific topics, retrieve relevant context from the book, and generate AI-powered detailed answers.

## Features

- **Automated PDF Download**: Downloads the "Human Nutrition" book in PDF format if not already present locally.
- **Text Extraction**: Extracts and preprocesses text from each page of the PDF.
- **Sentence Chunking**: Splits the extracted text into smaller chunks for efficient embedding and retrieval.
- **Semantic Embedding**: Uses `sentence-transformers` to create embeddings of text chunks for semantic similarity-based retrieval.
- **Query-based Retrieval**: Retrieves the most relevant chunks of text from the dataset for a given query.
- **LLaMA 2 Integration**: Combines retrieved context with LLaMA 2 to generate detailed, human-like responses to user queries.
- **Interactive Query Examples**: Examples include questions like *"What are fast-releasing carbohydrates?"* and *"Foods high in fiber?"* with results ranked by relevance.

## Project Workflow

1. **Download and Preprocess PDF**:
   - If the PDF file is not found locally, it is downloaded from an open-source repository.
   - Text is extracted and formatted using libraries like `PyMuPDF` and `spaCy`.

2. **Chunk and Embed Text**:
   - Text is segmented into sentence-level chunks, grouped into chunks of 10 sentences.
   - Semantic embeddings are computed for these chunks using the `all-mpnet-base-v2` model from `sentence-transformers`.

3. **Query Execution**:
   - A user query is embedded and compared with the dataset embeddings using dot product similarity.
   - The top results are retrieved, including page numbers and relevant text snippets.

4. **Generate Detailed Responses**:
   - Retrieved context is passed as input to LLaMA 2 (via the Ollama API), which generates detailed answers.
   - The system mimics conversational AI for intelligent, content-rich responses.
