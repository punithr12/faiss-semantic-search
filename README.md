FAISS Semantic Search Engine

A mini semantic search engine built using Python, Sentence Transformers, and FAISS.

This project demonstrates how text can be converted into vector embeddings and searched based on semantic meaning rather than exact keyword matches.

Objective

The objective of this project is to understand the core retrieval process used in Semantic Search and Retrieval-Augmented Generation (RAG) systems.

The project demonstrates how to:

Generate embeddings from text
Normalize vector embeddings
Store embeddings in a FAISS index
Perform similarity search
Retrieve the Top 3 most relevant results
Build an interactive command-line search interface
Project Workflow

The semantic search process follows this pipeline:

Knowledge Base Sentences
        ↓
Generate Embeddings
        ↓
384-Dimensional Vectors
        ↓
L2 Normalization
        ↓
FAISS Vector Index

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

The all-MiniLM-L6-v2 model from Sentence Transformers was used to convert each sentence into a numerical vector representation.

Each sentence is represented as a 384-dimensional embedding.

Example output:

Embedding matrix shape: (10, 384)
Task 2: Build the FAISS Index

The generated embeddings were prepared for similarity search by:

Converting embeddings to float32
Applying L2 normalization
Creating a FAISS IndexFlatL2 index
Adding all embeddings to the index

Example:

faiss.normalize_L2(embeddings)

index = faiss.IndexFlatL2(384)

index.add(embeddings)

The index stores all 10 knowledge base vectors.

Example output:

Total vectors stored in FAISS: 10
Task 3: Semantic Search

For semantic search:

The user enters a query.
The query is converted into an embedding using the same model.
The query embedding is normalized.
FAISS compares the query vector with the stored vectors.
The Top 3 most relevant sentences are returned.

Results are displayed in the following format:

Rank | Score | Matched Sentence

The system was tested using multiple queries related to password issues, billing, and login problems.

Note: Since IndexFlatL2 is used, the returned values represent L2 distances. Lower values indicate closer matches.

Task 4: Interactive CLI

The project includes an interactive search loop that allows users to continuously enter queries.

For every query, the system:

Generates a query embedding
Normalizes the embedding
Searches the FAISS index
Displays the Top 3 relevant results

Example:

Enter your query (or type 'exit' to quit):

Typing:

exit

terminates the program.

Task 5: Reflection Questions

The theoretical questions and answers are documented separately in:

REFLECTION.md

The reflection covers:

The difference between IndexFlatL2 and IndexFlatIP
Why embeddings are normalized for cosine similarity
What Approximate Nearest Neighbour (ANN) search means and why it is useful
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

git clone https://github.com/punithr12/faiss-semantic-search.git

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

This project demonstrates the basic retrieval pipeline used in semantic search and RAG systems:

Text
 ↓
Embedding Model
 ↓
Vector Representation
 ↓
FAISS Vector Index
 ↓
Similarity Search
 ↓
Relevant Results

Unlike traditional keyword-based search, semantic search retrieves results based on the meaning and context of the user's query.