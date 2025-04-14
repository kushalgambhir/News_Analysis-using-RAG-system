# PROBLEM STATEMENT
Journalists and analysts often struggle to process vast amounts of textual data from policy documents, financial reports, legal rulings, and government publications. These documents, often spanning hundreds of pages, require rapid summarization and fact extraction to aid in accurate reporting. Traditional manual methods of extracting insights from such documents are time-consuming, error-prone, and inefficient.
To address this challenge, HelpMateAI_News Analysis is designed as a Retrieval-Augmented Generation (RAG) system that enables journalists and analysts to efficiently search, retrieve, and summarize key insights from uploaded documents. Users can ask natural language questions and receive context-aware, factually grounded responses, significantly reducing research time while ensuring accuracy.

# DATA SOURCES
Our system allows users to manually upload PDFs containing the latest government reports, policy documents, and legal rulings. These documents are preprocessed, indexed, and stored in a vector database for future queries.
## Data Collection Process
•	Users upload policy papers, legal reports, financial statements, or meeting transcripts
•	 Documents are split into smaller chunks and embedded using sentence-transformers
•	 The ChromaDB vector store enables efficient semantic search and retrieval
By structuring the data pipeline this way, the system remains adaptable to evolving news topics while ensuring fast, accurate information retrieval.

# SYSTEM DESIGN & IMPLEMENTATION
The project follows a structured pipeline for document processing, storage, retrieval, and response generation:
## (a) Document Processing: PyMuPDFLoader & RecursiveCharacterTextSplitter
RecursiveCharacterTextSplitter chunks large documents into 200-character segments with a 20-character overlap
This prevents context loss while enabling efficient retrieval
## (b) Embedding & Vector Storage: HuggingFaceEmbeddings + ChromaDB
Each chunk is converted into a numerical vector representation
These embeddings are stored in ChromaDB, allowing fast semantic search
Queries retrieve the most contextually relevant chunks for response generation
## (c) Query Engine: RetrievalQA with Groq Llama 3
User queries trigger retrieval from ChromaDB
Retrieved document chunks are fed into Llama 3 via Groq
The LLM generates a coherent, context-aware response
By leveraging this modular approach, our system ensures scalability, efficiency, and ease of use.

# FLOW CHART
![image](https://github.com/user-attachments/assets/555eb34f-5d94-4bfb-991a-a3f3f273185f)

# Steps to run the python file
This code is written to run in colab environment.
1. Run  all the cell at beginning to install the requirements.
2. Mount your google drive.  
3. Create the JSON file and  store  the api keys for hugging face and groq by providing your api key in the corresponding field. This is for only one time then remove the api from the field and comment out the cell (recommended) or you can delete the cell.
4. Just after creating the data folder load the pdf file of your interest in your google drive in “drive/MyDrive/myproject/data" folder. 
5. There are two stage , 1st without refinement and 2nd with refinement that the model can be tested by providing question in side the cell. 
6. Now the model is ready for your question. Type ‘ exit ‘ to come out from the loop.
