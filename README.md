#  Thai Food RAG Chatbot

A chatbot that answers questions about **Thai cooking** using **RAG (Retrieval-Augmented Generation)**. It retrieves information from a Thai food dataset and generates answers with an LLM.

## Example code
- 

## 🏗️ System Architecture

```
User Question → Embedding (BGE-M3) → FAISS Vector Search → Top-K Documents → LLM (Chinda Qwen) → Answer
```

## 📂 Dataset

- **Source:** [ChokF/thai_food](https://huggingface.co/datasets/ChokF/thai_food)
- **Columns:** Name, Ingredients, Seasonings, Instructions

## 🧠 Models

| Model | Name | Purpose |
|-------|------|---------|
| Embedding | `BAAI/bge-m3` | Convert text to vectors |
| LLM | `iapp/chinda-qwen3-4b` | Generate answers from context |

## ⚙️ RAG Pipeline

1. Load dataset from Hugging Face
2. Convert each dish into a Document
3. Generate embeddings and store in FAISS
4. On user query → retrieve relevant documents → send to LLM to generate answer

## 📦 Installation

```bash
pip install datasets llama-index llama-index-llms-huggingface llama-index-embeddings-huggingface faiss-cpu transformers streamlit
```

## 🚀 Usage

```bash
streamlit run app.py
```

## 🎯 Example Questions

- วิธีทำไข่เจียวมีขั้นตอนอย่างไร?
- ต้มยำกุ้งใช้วัตถุดิบอะไรบ้าง?
- ผัดกะเพราใส่เครื่องปรุงอะไร?
- แกงเขียวหวานทำยังไง?
- ส้มตำมีส่วนผสมอะไรบ้าง?

## 📁 Project Structure

```
ThaiFoodRAG/
├── NLPProjectRAG.ipynb   # Build RAG in Colab
├── deploy.ipynb          # Deploy on Kaggle
├── app.py                # Streamlit Web App
├── rag_storage/          # Vector Database
└── README.md
```


---

👨‍💻 NLP Project — Thai Food RAG Chatbot
