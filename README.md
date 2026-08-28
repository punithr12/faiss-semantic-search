# FAISS Semantic Search Engine

A mini semantic search engine built using Python, Sentence Transformers, and FAISS. The project generates embeddings for a small knowledge base and retrieves the most relevant sentences based on the semantic meaning of a user's query.

## Objective

The objective of this project is to understand the core retrieval process used in semantic search and Retrieval-Augmented Generation (RAG) systems.

The project demonstrates how to:

- Generate sentence embeddings
- Store embeddings in a FAISS vector index
- Perform similarity search
- Retrieve the Top 3 most relevant results
- Build an interactive command-line search interface

---

## Technologies Used

- Python
- Sentence Transformers
- all-MiniLM-L6-v2
- FAISS
- NumPy
- Jupyter Notebook

---

# Project Workflow

```text
Knowledge Base Sentences
          ↓
SentenceTransformer Model
          ↓
384-Dimensional Embeddings
          ↓
L2 Normalization
          ↓
FAISS IndexFlatL2
          ↓
User Query
          ↓
Query Embedding
          ↓
FAISS Similarity Search
          ↓
Top 3 Relevant Results


Tasks Completed
Task 1: Setup and Embedding Generation

A knowledge base containing 10 customer support-related sentences was created.

The sentences cover topics such as:

Password reset
Billing information
Subscription management
Login issues
Account management
Unauthorized charges

The all-MiniLM-L6-v2 model was used to convert each sentence into a 384-dimensional embedding.

Example output:

Embedding matrix shape: (10, 384)
Task 2: Build a FAISS Index

The generated embeddings were converted to float32 and normalized using:

faiss.normalize_L2(embeddings)

A FAISS IndexFlatL2 index was created:

index = faiss.IndexFlatL2(384)

All knowledge base embeddings were added to the index.

Example output:

Total vectors stored in FAISS: 10
Task 3: Semantic Search

A user query is converted into an embedding using the same Sentence Transformer model.

The query embedding is normalized and searched against the FAISS index.

The system retrieves the Top 3 nearest results and displays:

Rank | Score | Matched Sentence

Multiple queries were tested, including password, billing, and login-related questions.

Note: Since IndexFlatL2 is used, the returned values are L2 distances. Lower distances indicate closer matches.

Task 4: Interactive CLI

An interactive loop allows users to continuously enter search queries.

Example:

Enter your query (or type 'exit' to quit):

For each query, the system retrieves and displays the Top 3 relevant sentences.

The user can type:

exit

to stop the program.

Task 5: Reflection Questions

The REFLECTION.md file contains answers to the following questions:

What is the difference between IndexFlatL2 and IndexFlatIP?
Why are embeddings normalized when cosine similarity is required?
What does Approximate Nearest Neighbour (ANN) search mean, and why is it useful?
Project Structure
faiss-semantic-search/
│
├── FAISS_Semantic_Search.ipynb
├── REFLECTION.md
├── requirements.txt
└── README.md
Installation

Clone the repository and navigate to the project directory.

Create and activate a virtual environment:

python3 -m venv .venv
source .venv/bin/activate

Install the required dependencies:

pip install -r requirements.txt
Running the Project

Open the Jupyter Notebook:

jupyter notebook FAISS_Semantic_Search.ipynb

Run the notebook cells sequentially to:

Create the knowledge base
Generate embeddings
Build the FAISS index
Perform semantic search
Test multiple queries
Use the interactive search interface
Key Learning

This project demonstrates the retrieval layer used in modern RAG systems.

Text
 ↓
Embeddings
 ↓
Vector Database / FAISS
 ↓
Similarity Search
 ↓
Relevant Information

Unlike traditional keyword search, semantic search compares the meaning of text using vector embeddings.

