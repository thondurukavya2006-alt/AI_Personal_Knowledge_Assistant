# 🤖 AI Personal Knowledge Assistant
### A Multi-Agent AI Application Powered by Retrieval-Augmented Generation (RAG)

An intelligent AI-powered knowledge assistant that helps users understand documents, generate study materials, create quizzes, conduct online research, and compare multiple documents through an interactive web application.

---

## 📌 Project Overview

The **AI Personal Knowledge Assistant** is a multi-agent application designed to make information retrieval and learning easier.

Users can upload documents and interact with them using natural language. The system uses Retrieval-Augmented Generation (RAG) to retrieve relevant information from uploaded documents and generate context-aware responses.

In addition to document question answering, the application provides specialised AI agents for studying, quiz generation, online research, and document comparison.

The application provides an interactive web interface built using **Gradio**.

## ✨ Key Features

### 1. 📚 AI Knowledge Chat
- Upload and interact with personal documents.
- Ask questions using natural language.
- Retrieve relevant information from uploaded documents.
- Generate context-aware answers.
- Display document source information where available.

### 2. 🎓 Study Assistant
- Generate study notes from uploaded documents.
- Simplify complex technical concepts.
- Create summaries and revision materials.
- Support learning and exam preparation.

### 3. 📝 AI Quiz Generator
- Automatically generate multiple-choice questions (MCQs).
- Generate quizzes from uploaded documents.
- Evaluate submitted answers.
- Display scores and correct answers.

### 4. 🌐 Research Assistant
- Conduct online research using web search.
- Retrieve information about selected topics.
- Generate research-oriented responses.

### 5. 📄 Document Comparison
- Compare two uploaded documents.
- Identify similarities and differences.
- Generate comparative summaries.

### 6. 🗂️ Document Library
- Upload and manage documents.
- Support PDF, DOCX, and TXT files.
- Extract document content.
- Index documents for retrieval.

---

## 🏗️ System Architecture

The application follows a multi-agent architecture coordinated using LangGraph.

```text
                 USER
                   |
                   v
             GRADIO UI
                   |
                   v
          MAIN COORDINATOR
             (LangGraph)
                   |
       +-----------+-----------+
       |           |           |
       v           v           v
   KNOWLEDGE     STUDY       QUIZ
    AGENT        AGENT       AGENT
       |           |           |
       +-----------+-----------+
                   |
          +--------+--------+
          |                 |
          v                 v
      RESEARCH          DOCUMENT
       AGENT          COMPARISON AGENT
          |                 |
          +--------+--------+
                   |
                   v
             RAG PIPELINE
                   |
          +--------+--------+
          |        |        |
          v        v        v
       CHUNKING EMBEDDING RETRIEVAL
                   |
                   v
              FAISS INDEX
                   |
                   v
            LLM GENERATION
                   |
                   v
             FINAL RESPONSE
```

## ⚙️ RAG Pipeline

The Retrieval-Augmented Generation pipeline works through the following stages:

1. **Document Upload:** Users upload PDF, DOCX, or TXT files.
2. **Text Extraction:** Text is extracted from uploaded documents.
3. **Text Chunking:** Extracted text is divided into smaller chunks.
4. **Embedding Generation:** Sentence Transformers converts text chunks into numerical embeddings.
5. **Vector Storage:** FAISS stores the embeddings for efficient similarity search.
6. **Information Retrieval:** Relevant document chunks are retrieved based on the user's question.
7. **Response Generation:** The language model generates answers using the retrieved context.
8. **Source Information:** Relevant document references are displayed where supported.

### Default RAG Configuration

| Parameter | Default Value |
|---|---|
| Embedding Model | all-MiniLM-L6-v2 |
| Vector Database | FAISS |
| Chunk Size | 800 characters |
| Chunk Overlap | 150 characters |
| Top-K Retrieval | 5 chunks |

These are the default configuration values and may be adjustable through application settings.

---

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Gradio | Interactive web interface |
| LangGraph | Multi-agent orchestration |
| FAISS | Vector similarity search |
| Sentence Transformers | Text embedding generation |
| all-MiniLM-L6-v2 | Embedding model |
| OpenAI-compatible API | LLM integration |
| PyMuPDF | PDF text extraction |
| python-docx | DOCX text extraction |
| DuckDuckGo Search | Online research |
| NumPy | Numerical processing |
| Pandas | Data processing |
| Plotly | Data visualization |

---

## 🔐 API Key Configuration

The project uses Google Colab Secrets to store API credentials securely.

**Step 1:** Open your notebook in Google Colab.

**Step 2:** Open the Secrets panel from the left sidebar.

**Step 3:** Create a secret with the following name:

```text
API_KEY
```

**Step 4:** Enable notebook access.

**Step 5:** Retrieve the key securely in Python:

```python
from google.colab import userdata

API_KEY = userdata.get("API_KEY")
```

Configure the API endpoint and model using the values provided by your API provider:

```python
BASE_URL = "YOUR_API_BASE_URL"
MODEL = "YOUR_MODEL_ID"
```

Initialize the OpenAI-compatible client:

```python
from openai import OpenAI

client = OpenAI(
    base_url=BASE_URL,
    api_key=API_KEY
)
```

**Security Note:** Never upload API keys, passwords, or other credentials to GitHub. Use environment variables or secure secret management.

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10 or compatible version.
- Google account.
- Google Colab.
- Valid API credentials.
- Internet connection.
- GitHub account (for source-code hosting).

### Installation and Execution

**1. Clone the repository**

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

**2. Navigate to the project directory**

```bash
cd YOUR_PROJECT_FOLDER
```

**3. Open the Jupyter Notebook**

Open:

```text
AI_Personal_Knowledge_Assistant.ipynb
```

Alternatively, upload the notebook to Google Colab.

**4. Configure API credentials**

Add your API key through Google Colab Secrets and configure the correct API endpoint and model ID.

**5. Execute the notebook**

Run the notebook cells in sequence to install dependencies, initialize models, configure the RAG pipeline, and initialize the AI agents.

**6. Launch the Gradio application**

Execute the application launch cell.

Gradio will generate a local URL and, when public sharing is enabled, a temporary public URL.

Open the public URL to access the application.

---

## 🧪 Testing

The project includes a testing function named:

```python
run_all_tests()
```

The test suite covers:

- Document extraction.
- RAG retrieval.
- Quiz grading.
- Agent routing.
- Knowledge Agent.
- Study Agent.
- Quiz Agent.
- Research Agent.
- Document Comparison Agent.
- Main Coordinator.

Run the test function after initializing the required project components.

---

## 📂 Project Structure

```text
AI-Personal-Knowledge-Assistant/
│
├── AI_Personal_Knowledge_Assistant.ipynb
│
├── README.md
│
├── requirements.txt          # If provided separately
│
├── screenshots/              # Optional application screenshots
│
└── sample_documents/         # Optional sample documents
```

*The notebook is the primary project implementation. Optional folders and files can be added when organising the GitHub repository.*

---

## 💡 Example Use Cases

- Students can generate study notes from academic research papers.
- Researchers can ask questions about technical documents.
- Learners can create practice quizzes.
- Users can compare multiple research papers.
- Users can conduct online research on selected topics.
- Professionals can retrieve
