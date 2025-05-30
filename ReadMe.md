
Project Summary This project demonstrates how to perform EDA on a dataset of medical records to attempt to understand or find correlation on why patients get readmitted within 30 days of discharge.

For EDA counts and exploratoy charts like hisograms were built to understand correlation between variables.

Evalusations was done to test the correctness of the model built. In this case Random Forrest was used.

A second task was to analyse and build a retrieval-augmented generation (RAG) system using Google Gemini's embedding and generation APIs. It extracts text,stores them in a vector database (ChromaDB), generates embeddings using Gemini's text-embedding-004 model, and finally enables question answering using a conversational prompt with Gemini. This is to intaggogate the dataset using Natural Language

Setup

Install Dependencies: pip install

!pip uninstall -qqy jupyterlab kfp  # Remove unused conflicting packages
!pip install -qU "google-genai==1.7.0" "chromadb==0.6.3"
!pip install openpyxl 3.1.0
!pip install --upgrade openpyxl
!pip install pdfplumber      
!pip install python-docx PyPDF2 openpyxl
!pip install beir      
!pip install vertexai      
!pip install PyPDF2
!pip install Pillow  
!pip install chromadb 

Set up Gemini API: Replace the placeholder with your actual Google GenAI API key:

GOOGLE_API_KEY = 'YOUR_API_KEY'



