# FAISS Semantic Search Engine

A mini semantic search engine built using Python, Sentence Transformers, and FAISS.

The system converts knowledge base sentences into vector embeddings and uses FAISS to retrieve the Top 3 most semantically relevant results for a user's query.

---

## Objective

The objective of this project is to understand how semantic search and the retrieval layer of Retrieval-Augmented Generation (RAG) systems work.

This project demonstrates:

- Text embedding generation
- Vector normalization
- FAISS vector indexing
- Semantic similarity search
- Top-K retrieval
- Interactive query searching

---

# Project Workflow

The following diagram represents the complete semantic search pipeline:

```text
Knowledge Base Sentences
          ↓
Generate Embeddings
          ↓
384-Dimensional Vectors
          ↓
L2 Normalization
          ↓
FAISS Vector Index
          ↓
─────────────────────────
          ↓
       User Query
          ↓
Generate Query Embedding
          ↓
L2 Normalization
          ↓
FAISS Similarity Search
          ↓
Top 3 Relevant Results

Tasks Completed
Task 1: Setup and Embedding Generation

A knowledge base containing 10 customer support-related sentences was created.

The knowledge base covers topics such as:

Password reset
Billing information
Subscription management
Login issues
Account management
Unauthorized charges

The all-MiniLM-L6-v2 Sentence Transformer model was used to convert each sentence into a numerical embedding.

Each sentence is represented as a 384-dimensional vector.

Example output:

Embedding matrix shape: (10, 384)
Task 2: Build the FAISS Index

The generated embeddings were prepared for FAISS by:

Converting the embeddings to float32
Normalizing the embeddings using L2 normalization
Creating a FAISS IndexFlatL2 index
Adding all embeddings to the index

Example:

faiss.normalize_L2(embeddings)

index = faiss.IndexFlatL2(384)

index.add(embeddings)

The total number of vectors stored:

Total vectors stored in FAISS: 10
Task 3: Semantic Search

A user query is converted into an embedding using the same all-MiniLM-L6-v2 model.

The query embedding is then normalized and searched against the FAISS index.

The system retrieves the Top 3 nearest knowledge base sentences.

Results are displayed in the following format:

Rank | Score | Matched Sentence

Three different queries were tested to demonstrate semantic search across topics such as password management, billing, and login issues.

Note: Since IndexFlatL2 is used, the returned values represent L2 distances. A lower distance indicates a closer match.

Task 4: Interactive CLI

An interactive command-line interface allows users to enter queries continuously.

For every query, the system:

Generates a query embedding
Normalizes the embedding
Searches the FAISS index
Retrieves the Top 3 results

Example:

Enter your query (or type 'exit' to quit):

The user can type:

exit

to terminate the program.

Task 5: Reflection Questions

The theoretical concepts and reflection answers are documented separately in:

REFLECTION.md

The file covers:

The difference between IndexFlatL2 and IndexFlatIP
Why embeddings are normalized for cosine similarity
Approximate Nearest Neighbour (ANN) search and its importance
Technologies Used
Python
Sentence Transformers
all-MiniLM-L6-v2
FAISS
NumPy
Jupyter Notebook
Project Structure
faiss-semantic-search/
│
├── FAISS_Semantic_Search.ipynb
├── README.md
├── REFLECTION.md
├── requirements.txt
└── .gitignore
Installation

Clone the repository:

git clone <repository-url>

Navigate to the project directory:

cd faiss-semantic-search

Create a virtual environment:

python3 -m venv .venv

Activate the virtual environment:

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
Run the interactive CLI
Key Learning

This project demonstrates the fundamental retrieval pipeline used in semantic search and RAG systems:

Text
 ↓
Embedding Model
 ↓
Vector Representation
 ↓
FAISS Vector Store
 ↓
Similarity Search
 ↓
Relevant Results

Unlike traditional keyword-based search, semantic search retrieves information based on the meaning and context of the user's query.