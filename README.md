# CineExtract Pro - Gen AI Project

A hands-on LangChain project that demonstrates:

- chat models (Mistral and Hugging Face)
- embedding models (OpenAI and Hugging Face)
- structured information extraction from movie text (CineSage)
- both CLI and Streamlit interfaces

This repository is ideal for learning practical GenAI workflows in small, focused scripts.

---

## Project Structure

```text
CineExtract Pro/
├─ requirements.txt
├─ chatmodels/
│  ├─ chat.py
│  ├─ chatbot.py
│  ├─ huggingface.py
│  ├─ localmodel.py
│  └─ UIchatbot.py
├─ CineSage/
│  ├─ core.py
│  └─ UICore.py
└─ embeddingmodels/
   ├─ embeddings.py
   └─ huggingface_embedding.py
```

---

## What Each Module Does

### chatmodels

- `chat.py`: minimal single prompt test using `ChatMistralAI`
- `chatbot.py`: interactive CLI chatbot with selectable personality mode:
  - Angry
  - Funny
  - Sad
- `huggingface.py`: remote Hugging Face endpoint chat example (`deepseek-ai/DeepSeek-R1`)
- `localmodel.py`: local Hugging Face pipeline chat example (`TinyLlama/TinyLlama-1.1B-Chat-v1.0`)
- `UIchatbot.py`: Streamlit chat UI with mood selection and session memory

### embeddingmodels

- `embeddings.py`: OpenAI embeddings demo (`text-embedding-3-large`, dimensions set to 64)
- `huggingface_embedding.py`: Hugging Face embeddings demo (`sentence-transformers/all-MiniLM-L6-v2`)

### CineSage

- `core.py`: CLI movie paragraph parser into structured schema using Pydantic
- `UICore.py`: Streamlit UI for movie information extraction and JSON output

---

## Tech Stack

- Python
- LangChain ecosystem
- Mistral via `langchain-mistralai`
- OpenAI embeddings via `langchain-openai`
- Hugging Face via `langchain_huggingface`
- Streamlit
- Pydantic

---

## Prerequisites

- Python 3.10+
- API keys based on the scripts you run:
  - Mistral API key (for Mistral chat and CineSage)
  - OpenAI API key (for OpenAI embeddings)
  - Hugging Face token (for hosted HF endpoint usage)

---

## Installation

### 1) Create and activate virtual environment

Windows PowerShell:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

### 2) Install dependencies

```powershell
pip install -r requirements.txt
```

### 3) Add environment variables

Create a `.env` file in the project root and add only the variables needed by the scripts you plan to run.

Typical variables:

```env
MISTRAL_API_KEY=your_mistral_key
OPENAI_API_KEY=your_openai_key
HUGGINGFACEHUB_API_TOKEN=your_hf_token
```

Note: variable names can vary by SDK version. If a script fails with authentication errors, verify expected env names for that specific package version.

---

## Run Guide

Run all commands from project root.

### Chat model demos

Single prompt Mistral test:

```powershell
python .\chatmodels\chat.py
```

CLI mood chatbot:

```powershell
python .\chatmodels\chatbot.py
```

Hugging Face endpoint chat:

```powershell
python .\chatmodels\huggingface.py
```

Local TinyLlama pipeline:

```powershell
python .\chatmodels\localmodel.py
```

Streamlit mood chatbot:

```powershell
streamlit run .\chatmodels\UIchatbot.py
```

### Embedding demos

OpenAI embeddings:

```powershell
python .\embeddingmodels\embeddings.py
```

Hugging Face embeddings:

```powershell
python .\embeddingmodels\huggingface_embedding.py
```

### CineSage (movie extraction)

CLI parser:

```powershell
python .\CineSage\core.py
```

Streamlit UI parser:

```powershell
streamlit run .\CineSage\UICore.py
```

---

## Example CineSage Input

```text
Inception is a 2010 science fiction thriller directed by Christopher Nolan, starring Leonardo DiCaprio, Joseph Gordon-Levitt, and Ellen Page. It follows a thief who enters dreams to steal secrets and is offered a chance to erase his past crimes by planting an idea in a target's mind. The film is rated 8.8/10.
```

Expected output shape:

- title
- release_year
- genre[]
- director
- cast[]
- rating
- summary

---

## Common Issues and Fixes

1. Authentication errors
- Confirm `.env` exists in project root.
- Confirm required API key/token for the script you are running.

2. Model/provider package mismatch
- Make sure `pip install -r requirements.txt` completed successfully.
- Upgrade a specific provider package if needed.

3. Streamlit command not found
- Run `pip install streamlit` in your active environment.
- Or use `python -m streamlit run <file>`.

4. Slow local model inference
- `localmodel.py` runs a local text-generation pipeline and can be slow on CPU.

---

## Learning Path (Suggested)

1. Start with `chatmodels/chat.py` to verify Mistral setup.
2. Run `chatmodels/chatbot.py` to understand conversational memory.
3. Try both embedding scripts.
4. Run `CineSage/core.py` for structured extraction.
5. Use both Streamlit apps for interactive testing.

---

## Improvement Ideas

- Add FAISS vector store example with retrieval pipeline
- Add logging and reusable config loader
- Add unit tests for schema validation and prompt output parsing
- Add a single launcher script for all demos

---

## License

No license file detected yet. Add a license if you plan to publish this project.
