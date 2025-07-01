# Production-Grade LLM API Server using LangChain + FastAPI

This project demonstrates how to build and deploy **production-grade LLM APIs** using **LangChain**, **FastAPI**, and **Streamlit**.

We expose two REST API endpoints:
- `/cricketer`: Powered by **Groq (OpenAI-compatible) LLM** using the `llama3-8b-8192` model.
- `/recipe`: Powered by **Local Ollama LLM** using the `gemma3:1b` model.

The frontend is a simple **Streamlit client** that interacts with these APIs.

---

## 🧠 Tech Stack

- **[LangChain](https://www.langchain.com/)** – Prompt templating and chaining.
- **[FastAPI](https://fastapi.tiangolo.com/)** – High-performance Python web framework for APIs.
- **[Groq API](https://console.groq.com/)** – OpenAI-compatible API for ultra-fast LLM inference.
- **[Ollama](https://ollama.ai/)** – Local LLM inference engine.
- **[Streamlit](https://streamlit.io/)** – Lightweight UI for demonstration.
- **LangServe** – LangChain’s native support for FastAPI deployment.

---

## 📁 Project Structure

```

.
├── app.py           # FastAPI server exposing LLM endpoints
├── client.py        # Streamlit client to interact with both endpoints
├── .env             # Environment variables (Groq API key, etc.)
└── README.md

````

---

## 📋 Prerequisites

- Python 3.10+
- [Groq API Key](https://console.groq.com/)
- [Ollama](https://ollama.ai/) installed and running locally
- `gemma3:1b` pulled in Ollama

---

## 🔐 .env Configuration

Create a `.env` file in the root directory:

```env
GROQ_API_KEY=your_groq_api_key
````

---

## 📦 Installation

```bash
git clone https://github.com/your-username/langchain-fastapi-llm.git
cd langchain-fastapi-llm

# (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

---

## 🚀 Running the FastAPI Server

Start Ollama if it's not already running:

```bash
ollama run gemma3:1b
```

Then run the FastAPI server:

```bash
python app.py
```

Server will be available at: [http://localhost:9000](http://localhost:9000)

---

## 🔄 API Endpoints

### 1. `/cricketer` – Groq (OpenAI-Compatible) LLM

* **Method**: POST
* **URL**: `http://localhost:9000/cricketer/invoke`
* **Request Payload**:

```json
{
  "input": {
    "topic": "Virat Kohli"
  }
}
```

* **Response**:

```json
{
  "output": {
    "content": "Virat Kohli is an Indian cricketer known for..."
  }
}
```

---

### 2. `/recipe` – Local Ollama LLM

* **Method**: POST
* **URL**: `http://localhost:9000/recipe/invoke`
* **Request Payload**:

```json
{
  "input": {
    "topic": "Pasta"
  }
}
```

* **Response**:

```json
{
  "output": "To make pasta, start by boiling water..."
}
```

---

## 🖥️ Running the Streamlit Client

```bash
streamlit run client.py
```

### Streamlit UI Features:

* Input box to fetch cricketer info from Groq API
* Input box to fetch a recipe using local Ollama model

---

## 📚 Key Concepts Covered

* FastAPI + LangServe integration for clean LLM routes.
* Running local and remote LLMs under a unified API layer.
* Prompt templating using `ChatPromptTemplate`.
* API invocation with Streamlit for a quick frontend.

---

## 📈 Future Improvements

* Add logging, request validation and error handling.
* Dockerize the app for easy deployment.
* Add authentication or API key access control.
* Extend to RAG or agent-based LLM use cases.

---

## 🧠 Learn More

* [LangChain Documentation](https://docs.langchain.com/)
* [FastAPI Docs](https://fastapi.tiangolo.com/)
* [Groq Console](https://console.groq.com/)
* [Ollama Models](https://ollama.ai/library)

---

## 🙌 Contribute

Feel free to fork the repo, file issues, or create PRs to expand this boilerplate for other production use cases!

---
