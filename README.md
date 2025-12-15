# Project README

## Overview
This repository contains the code for a PDF-based Question Answering system. The project implements a Retrieval-Augmented Generation (RAG) pipeline that ingests PDF documents, segments them into semantic chunks, embeds those chunks, and answers natural-language questions using a large language model.

The entire workflow is implemented in **`main.ipynb`**, which is intended to be run top-to-bottom either locally or in Google Colab.

---

## Main File

### `main.ipynb`
This notebook contains the complete end-to-end pipeline:

1. **Environment Setup**
   - Installs required Python packages
   - Includes separate setup paths for local execution and Google Colab

2. **PDF Ingestion & Chunking**
   - Uses `unstructured.partition.pdf` to parse PDFs
   - Splits documents into semantic chunks suitable for retrieval

3. **Document Representation**
   - Converts chunks into LangChain `Document` objects
   - Stores cleaned text for downstream processing

4. **Embedding Generation**
   - Uses HuggingFace sentence embeddings
   - Encodes document chunks into dense vector representations

5. **Similarity-Based Retrieval**
   - Computes cosine similarity between query embeddings and document chunks
   - Retrieves the top-*k* most relevant chunks

6. **LLM-Based Question Answering**
   - Uses a transformer-based language model
   - Generates answers conditioned on retrieved document context

7. **Interactive Interface**
   - Provides a Gradio UI for user interaction
   - Allows users to ask questions directly about the uploaded PDFs

---

## Running the Notebook

### Option 1: Google Colab (Recommended)
1. Upload `main.ipynb` to Colab
2. Run all cells sequentially
3. Follow the Colab-specific setup instructions in the notebook

### Option 2: Local Execution
1. Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate  # macOS/Linux
venv\\Scripts\\activate   # Windows
```

2. Install dependencies
```bash
pip install -U pip
pip install unstructured langchain transformers torch gradio sentence-transformers
```

3. Launch Jupyter
```bash
jupyter notebook
```

4. Open and run `main.ipynb`

---

## Key Technologies
- **Unstructured** – PDF parsing and document chunking
- **LangChain** – Document abstraction and pipeline components
- **HuggingFace Transformers** – Embeddings and language models
- **PyTorch** – Model execution
- **Gradio** – Interactive web interface

---

## Example Usage
- Upload a PDF document
- Ask natural-language questions (e.g., *"Which burgers are vegetarian?"*)
- Receive answers grounded in the document content

---

## Results & Reproducibility
- All results shown in the final report are reproducible by running `main.ipynb`
- Chunking, retrieval, and generation steps are deterministic where applicable

---

## Limitations
- Performance depends on PDF structure and text quality
- Large PDFs may increase memory and runtime requirements
- Retrieval quality is sensitive to embedding choice and chunk size
- 7b parameter llm results in hallucinations and poor responses occasionally.

---

## Notes
- Large PDF files are not included in the repository
- GPU acceleration is recommended but not required
- The notebook includes comments explaining each major step

---

## Contact
For questions regarding the implementation or reproduction of results, please feel free to contact the project authors.
