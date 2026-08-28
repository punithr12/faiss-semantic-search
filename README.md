# FAISS Semantic Search Engine

A mini semantic search engine built using Python, Sentence Transformers, and FAISS.

This project demonstrates how text can be converted into vector embeddings and searched based on semantic meaning rather than exact keyword matches.

---

## Objective

The objective of this project is to understand the core retrieval process used in Semantic Search and Retrieval-Augmented Generation (RAG) systems.

The project demonstrates how to:

- Generate embeddings from text
- Normalize vector embeddings
- Store embeddings in a FAISS index
- Perform similarity search
- Retrieve the Top 3 most relevant results
- Build an interactive command-line search interface

---

## Project Workflow

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

---

## Tasks Completed

### Task 1: Setup and Embedding Generation

A knowledge base containing 10 customer support-related sentences was created.

The knowledge base covers topics such as:

- Password reset
- Billing information
- Account management
- Login issues
- Subscription management

The `all-MiniLM-L6-v2` model from Sentence Transformers was used to convert each sentence into a numerical vector representation.

Each sentence is represented as a 384-dimensional embedding.

Example output:

Example output:

```text
Embedding matrix shape: (10, 384)
```
### Task 2: Build the FAISS Index


The generated embeddings were prepared for similarity search by:

1. Converting embeddings to `float32`
2. Applying L2 normalization
3. Creating a FAISS `IndexFlatL2` index
4. Adding all embeddings to the index

Example implementation:

```python
faiss.normalize_L2(embeddings)

index = faiss.IndexFlatL2(384)

index.add(embeddings)
```text
Total vectors stored in FAISS: 10

```
### Task 3: Semantic Search

A user query is converted into an embedding using the same `all-MiniLM-L6-v2` model.

The query embedding is normalized and searched against the FAISS index to retrieve the Top 3 most relevant knowledge base sentences.

The results are displayed in the following format:

```text
Rank | Score | Matched Sentence
```

### Task 4: Interactive CLI

An interactive command-line interface allows users to continuously enter search queries.

For each query, the system:

1. Generates an embedding for the user query
2. Normalizes the query embedding
3. Searches the FAISS index
4. Retrieves the Top 3 most relevant results

The user can continue searching until they type `exit`.

Example:

```text
Enter your query (or type 'exit' to quit):
```
### Task 5: Reflection Questions

The theoretical questions and answers are documented separately in the `REFLECTION.md` file.

The reflection covers:

1. The difference between `IndexFlatL2` and `IndexFlatIP`
2. Why embeddings are normalized when cosine similarity is required
3. What Approximate Nearest Neighbour (ANN) search means and why it is useful

---

## Technologies Used

- Python
- Sentence Transformers
- `all-MiniLM-L6-v2`
- FAISS
- NumPy
- Jupyter Notebook

## Project Structure

```text
faiss-semantic-search/
├── FAISS_Semantic_Search.ipynb
├── README.md
├── REFLECTION.md
├── requirements.txt
├── .gitignore
└── .venv/
```
## Installation

Clone the repository:

```bash
git clone https://github.com/punithr12/faiss-semantic-search.git
```

Navigate to the project directory:

```bash
cd faiss-semantic-search
```

Create a virtual environment:

```bash
python3 -m venv .venv
```

Activate the virtual environment:

```bash
source .venv/bin/activate
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Project

Open the Jupyter Notebook:

```bash
jupyter notebook FAISS_Semantic_Search.ipynb
```

Run the notebook cells sequentially to:

1. Create the knowledge base
2. Generate embeddings
3. Build the FAISS index
4. Perform semantic search
5. Test multiple queries
6. Run the interactive CLI

---

## Key Learning

This project demonstrates the basic retrieval pipeline used in semantic search and RAG systems:

```text
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
```

Unlike traditional keyword-based search, semantic search retrieves results based on the meaning and context of the user's query.

---

