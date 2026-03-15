# 🍜 Thai Food RAG Chatbot (NLP Project)

A chatbot that answers questions about **how to cook Thai food** using
the **Retrieval-Augmented Generation (RAG)** technique in **Natural
Language Processing (NLP)**.

The system retrieves information from a Thai food dataset and allows
users to ask questions such as:

-   How to cook Pad Krapow
-   Ingredients of Tom Yum
-   Seasonings used in Green Curry

------------------------------------------------------------------------

# 📌 Features

-   🔎 Search Thai food menu information from a dataset
-   🤖 AI chatbot for Thai cooking questions
-   📚 Uses **RAG (Retrieval-Augmented Generation)**
-   ⚡ Vector search using **FAISS**
-   🧠 Large Language Model (LLM) for answer generation
-   🌐 Simple web interface using **Streamlit**

------------------------------------------------------------------------

# 🏗️ System Architecture

    User Question
          │
          ▼
    Embedding Model
    (BGE-M3)
          │
          ▼
    Vector Database
    (FAISS)
          │
    Retrieve Top-K Documents
          │
          ▼
    LLM (Chinda Qwen)
          │
          ▼
    Generated Answer

------------------------------------------------------------------------

# 📂 Dataset

This project uses a Thai food dataset from Hugging Face.

Dataset: https://huggingface.co/datasets/ChokF/thai_food

Columns used:

  Column         Description
  -------------- ----------------------
  Name           Dish name
  Ingredients    Main ingredients
  Seasonings     Cooking seasonings
  Instructions   Cooking instructions

------------------------------------------------------------------------

# 🧠 Models Used

### Embedding Model

    BAAI/bge-m3

Used to convert text into vector embeddings.

### LLM

    iapp/chinda-qwen3-4b

Used to generate answers based on retrieved context.

------------------------------------------------------------------------

# ⚙️ RAG Pipeline

1.  Load the dataset from Hugging Face.

2.  Convert each food item into a **Document**.

Example:

    Name: Pad Krapow
    Ingredients: pork, garlic, basil
    Seasonings: fish sauce, soy sauce
    Instructions: stir fry pork with garlic...

3.  Generate **embeddings** for each document.

4.  Store embeddings in a **FAISS vector database**.

5.  When a user asks a question such as:

```{=html}
<!-- -->
```
    How to cook Pad Krapow?

The system will:

-   Convert the question into an embedding
-   Retrieve the most relevant documents (Top-K)
-   Send the retrieved context to the LLM
-   Generate the final answer

------------------------------------------------------------------------

# 💻 Development Environment

### RAG Development

Google Colab

### Deployment

Kaggle Notebook

------------------------------------------------------------------------

# 📦 Installation

Install required libraries:

``` bash
pip install datasets
pip install llama-index
pip install llama-index-llms-huggingface
pip install llama-index-embeddings-huggingface
pip install faiss-cpu
pip install transformers
pip install streamlit
```

------------------------------------------------------------------------

# 🚀 Running the RAG System (Colab)

### 1. Load Dataset

``` python
from datasets import load_dataset
dataset = load_dataset("ChokF/thai_food")
```

### 2. Create Documents

``` python
documents = []

for _, row in df.iterrows():
    text = f"Name: {row['Name']}\nIngredients: {row['Ingredients']}\nSeasonings: {row['Seasonings']}\nInstructions: {row['Instructions']}"
    documents.append(text)
```

### 3. Create Embeddings

``` python
from llama_index.embeddings.huggingface import HuggingFaceEmbedding

embed_model = HuggingFaceEmbedding(
    model_name="BAAI/bge-m3"
)
```

### 4. Ask Questions

``` python
answer = chat_engine.chat(question)
print(answer)
```

------------------------------------------------------------------------

# 🌐 Deploy Web App (Kaggle)

This project uses **Streamlit** to create a simple web interface.

Create:

    app.py

Example:

``` python
import streamlit as st

st.title("Thai Food Chatbot")

question = st.text_input("Ask about Thai food")

if question:
    answer = ask(question)
    st.write(answer)
```

Run:

``` bash
streamlit run app.py
```

------------------------------------------------------------------------

# 📊 Evaluation

Evaluation can be done using:

    Precision@K

This metric measures whether the **Top-K retrieved documents are
relevant to the query**.

------------------------------------------------------------------------

# 📁 Project Structure

    ThaiFoodRAG/
    │
    ├── NLPProjectRAG.ipynb     # Build RAG in Colab
    ├── deploy.ipynb            # Deployment in Kaggle
    ├── app.py                  # Streamlit web application
    ├── rag_storage/            # Vector database storage
    └── README.md

------------------------------------------------------------------------

# 🎯 Example Questions

Example queries:

    How to cook Pad Thai?
    What are the ingredients of Tom Yum Goong?
    What seasonings are used in Green Curry?
    How to cook fried rice?

------------------------------------------------------------------------

# 👨‍💻 Author

NLP Project -- Thai Food RAG Chatbot
