# Model with Google Gemini Pro and Pathway

This project is a **Retrieval-Augmented Generation (RAG) pipeline** that uses Google Gemini Pro for LLM-powered chat completions and the Sentence Transformer for embeddings. It allows users to query food recipe documents (such as prep time and ingredients) and receive precise answers based on indexed data.

## Features:

- **Real-time document indexing** with Pathway.
- **Google Gemini Pro** for generating responses.
- **Sentence Transformer** for embedding text chunks.
- **Document query** capabilities, including support for local files.

## Example Queries

- **What is the Prep Time of Appam Recipe?**

  - Response: "4 hrs"
- **What is the Prep Time of Malabar Paratha?**

  - Response: "1 hr 10 mins"
- **What are the ingredients of Malabar Paratha?**

  - Response: "all-purpose flour, sugar, salt, water, oil"

## Requirements

- Docker Desktop (ensure it is installed and running).
- API Key for Google Gemini Pro.
- Python 3.9+
- Git

## Setup Instructions

1. **Clone the repository**:

   ```bash
   git clone https://github.com/Jerald-Joyson/RAG-Gemini-Project.git
   cd RAG-Gemini-Project
   ```
2. **Set up the environment**:

   - Create a `.env` file in the `demo-question-answering` folder and add your **Gemini API Key**:
     ```
     GEMINI_API_KEY=your-gemini-api-key
     ```
3. **Install dependencies**:

   - Add these dependencies to `requirements.txt`:
     ```txt
     pathway[all]>=0.11.0
     python-dotenv==1.0.1
     mpmath==1.3.0
     litellm>=1.35
     Google-generativeai
     Sentence-transformers
     ```
4. **Build the Docker Image**:

   ```bash
   docker build -t raggem .
   ```
5. **Run the Docker container**:

   - For Linux/Mac:

     ```bash
     docker run -v "$(pwd)/data:/app/data" -p 8000:8000 --env-file .env raggem
     ```
   - For Windows:

     ```bash
     docker run -v "${PWD}/data:/app/data" -p 8000:8000 raggem
     ```
6. **Query the model**:
   You can send a `POST` request to the RAG server to retrieve answers from the ingested document data. For example:

   ```bash
   curl -X 'POST' 'http://0.0.0.0:8000/v1/pw_ai_answer' -H 'accept: */*' -H 'Content-Type: application/json' -d '{
     "prompt": "What is the Prep Time of Appam Recipe?"
   }'
   ```
7. **Screenshots**:
   Screenshots of the results ie, example queries and outputs.
   
https://github.com/user-attachments/assets/dafbc636-48c7-4905-9e06-986bdd9e0f00
https://github.com/user-attachments/assets/59118333-5bd9-44a9-bf92-7a500dbf5996
https://github.com/user-attachments/assets/7d76b92b-9852-44dc-8362-8ab749c3e96b
https://github.com/user-attachments/assets/682166b8-a68d-431c-9ce6-c4a886e7d8a4
