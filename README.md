# 🏥 AI-Powered Medical Report Summarizer

An advanced, production-grade end-to-end medical report digitization, structuring, validation, and AI-guided summarization system. 

This platform transforms unstructured medical reports (PDFs, scans, camera captures) into structured, highly accurate clinical insights using a **OCR** and **Adaptive LLM Consensus Engine**, and a **Medical Retrieval-Augmented Generation (RAG)** pipeline powered by ChromaDB.

---

## 🚀 Key Features

* **OCR**: Integrates both `Tesseract OCR` and `OpenCV` to process images and PDFs. Scores character-level  to extract the highest-quality text.
* **LLM Parsing**: Uses Gemini  model to parsed medical entities (test name, value, unit, reference range, status) to eliminate LLM hallucinations.
* **Medical Retrieval-Augmented Generation (RAG)**:
  - Embeds scientific literature, dictionaries, and lab-manual references into a persistent `ChromaDB` vector store using `sentence-transformers/all-MiniLM-L6-v2`.
  - Performs real-time semantic lookup for out-of-range parameters.
  
* **FastAPI Secure Backend**: Featuring SQLAlchemy ORM, robust JWT token-based auth (`/auth/register`, `/auth/login`), uploads management, and custom request validations.
* **Modern React + Vite Frontend**: Premium dashboard web application with reactive upload, responsive landing pages, patient dashboard, authentication modal, and intuitive layout.

---





## 🛠️ Installation & Setup

### 1. Prerequisites
Ensure you have the following installed on your machine:
* Python 3.9+
* Node.js 18+ and npm
* Tesseract OCR Engine (installed on system path)

---

### 2. Backend Setup

1. **Navigate to the backend directory**:
   ```bash
   cd backend
   ```

2. **Create a virtual environment and activate it**:
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install the required dependencies**:
   ```bash
   pip install fastapi uvicorn sqlalchemy mysql-connector-python easyocr pytesseract sentence-transformers chromadb pydantic python-dotenv python-multipart groq pillow PyMuPDF
   ```

4. **Configure Environment Variables**:
   Create a `.env` file in the `backend/` directory:
   ```env
   DATABASE_URL=mysql+mysqlconnector://root:YOUR_PASSWORD@localhost/medical_users
   GROQ_API_KEY=your_groq_api_key_here
   SECRET_KEY=your_super_secret_jwt_key
   ALGORITHM=HS256
   ACCESS_TOKEN_EXPIRE_MINUTES=30
   ```

5. **Initialize ChromaDB Vector Store**:
   Place your medical books or reference texts inside `backend/RAG/knowledge_base/` as `.txt` files. Then run the chunking and embedding pipeline:
   ```bash
   python RAG/embed_knowledge.py
   ```

6. **Run the Backend Server**:
   ```bash
   uvicorn main:app --reload
   ```
   *The backend will be running at `http://localhost:8000`.*
   *Interactive API documentation will be available at `http://localhost:8000/docs`.*

---

### 3. Frontend Setup

1. **Navigate to the frontend directory**:
   ```bash
   cd ../frontend
   ```

2. **Install frontend packages**:
   ```bash
   npm install
   ```

3. **Launch the development server**:
   ```bash
   npm run dev
   ```
   *The client web application will be live at `http://localhost:5173`.*

---



## 🔬 Core Technologies

* **FastAPI**: Modern, high-performance web framework for Python.
* **SQLAlchemy**: Powerful Python SQL Toolkit & ORM mapping.
* **ChromaDB**: AI-native vector database for semantic RAG lookups.
* **PyTesseract & OpenCV**: Multi-layered character recognition engines.
* **React + Vite**: Blazing fast modern frontend development tooling.
* **Groq SDK**: Ultra-low latency Llama inference API integration.

---


