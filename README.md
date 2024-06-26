# Simple RAG Demo

This repository contains a Jupyter Notebook demonstrating a simple Retrieval-Augmented Generation (RAG) application using various LangChain components for document loading, text splitting, embeddings generation, and retrieval.

## Features

- Load documents from web pages, text files, and PDFs.
- Split documents into manageable chunks.
- Generate embeddings using OpenAI.
- Store embeddings in a Chroma and FAISS vector store.
- Retrieve contextually relevant documents and answer user queries.

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/simple-rag-demo.git
    cd simple-rag-demo
    ```
2. Create a `.env` file in the root directory and add your OpenAI API key:
    ```plaintext
    OPENAI_API_KEY=your_openai_api_key
    ```

## Usage

1. Open the Jupyter Notebook:
    ```bash
    jupyter notebook simple_rag.ipynb
    ```

2. Run the cells sequentially to load documents, split them, generate embeddings, set up the retrieval chain, and input your queries.

## Data Ingestion

- **Web Scraping**: Load content from web pages using `WebBaseLoader`.
  ```python
  from langchain_community.document_loaders import WebBaseLoader
  import bs4

  loader = WebBaseLoader(web_paths=("https://lilianweng.github.io/posts/2023-06-23-agent/",),
                         bs_kwargs=dict(parse_only=bs4.SoupStrainer(class_=("post-title", "post-content", "post-header"))))
  text_documents = loader.load()
  ```

- **Text Documents**: Load content from text files using `TextLoader`.
  ```python
  from langchain_community.document_loaders import TextLoader
  loader = TextLoader("speech.txt")
  text_documents = loader.load()
  ```

- **PDFs**: Load content from PDF files using `PyPDFLoader`.
  ```python
  from langchain_community.document_loaders import PyPDFLoader
  loader = PyPDFLoader('Cover Letter.pdf')
  documents = loader.load()
  ```

## Code Overview

- `simple_rag.ipynb`: The main Jupyter Notebook containing the code for the RAG application.
- The notebook initializes various LangChain components, loads documents, splits them, generates embeddings, and sets up the retrieval chain.
- The user's input is processed, and the response along with relevant document chunks are displayed.

## Dependencies

- `jupyter`
- `langchain`
- `faiss-cpu`
- `python-dotenv`

Make sure to install all dependencies listed in the `requirements.txt` file.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

## Acknowledgements

- [LangChain](https://github.com/hwchase17/langchain)
- [Jupyter](https://jupyter.org/)

Feel free to contribute to this project by submitting issues or pull requests.
