# 🔒 Private PQM AI Assistant & Audio Intelligence Engine

A 100% on-premises, privacy-enforced compliance pipeline built to ingest multi-format enterprise documentation and voice recordings with zero cloud connectivity. This system enables project managers and engineers to execute rigorous Project Quality Management (PQM) workflows without exposing proprietary data to third-party APIs.

---

## 🛠️ Architecture Blueprint

The microservice architecture relies entirely on open-source, hardware-optimized local runtimes to achieve air-gapped security boundaries:

*   **Core API Framework:** Asynchronous `FastAPI` runtime with dynamic routing.
*   **Speech-to-Text (STT) Engine:** `faster-whisper` (Base variant) configured for localized CPU inference via floating-point (`float32`) execution.
*   **Local LLM Orchestration:** `Ollama` hosting quantized edge models (`llama3.2:1b`), operating with an expanded 4,096 token context window allocation.
*   **Audio Core:** `pydub` binary ingestion handling dynamic in-memory transformations of compressed WhatsApp audio formats.
*   **OS Automation Hub:** `pyautogui` for desktop capture hooks to enrich live runtime contextual prompts.

---

## 🚀 Key Features

*   **Zero-Leakage Compliance Guard:** Perfect for fields with strict confidentiality requirements (such as industrial QA, ASNT Level II auditing, and FMEA validation loops).
*   **WhatsApp Native Voice Processing:** Automated pipelines that ingest binary `.opus` files from WhatsApp voice logs, transform them to MP3 arrays in-memory, pass them to Whisper STT, and cross-reference the output text against local data stores.
*   **Intelligent Token Optimization:** A name-matching context compiler scans inbound user queries and isolates relevant vault dependencies. This process protects the model's token capacity from context inflation while preventing truncation issues.
*   **Multi-Format Document Intelligence:** Automated text extraction pipelines built specifically for:
    *   **PDFs:** Multi-page text layering via `pypdf`.
    *   **Word Documents:** Document paragraph restructuring via `docx`.
    *   **Excel Spreadsheets:** Multi-tab cell tracking and row serialization via `openpyxl`.
*   **Live Scraping Bridges:** Real-time structural text parsing from online documentation via `BeautifulSoup` context injectors.

---

## 📂 Project Structure

```text
├── app.py                # Asynchronous FastAPI backend & AI pipelines
├── app.html              # Frontend user workspace UI dashboard
├── .gitignore            # Deployment exclusion rule mapping
└── pqm_vault/            # Local data repository (Created on run)
    └── audits/           # Historically archived compliance validation PDFs
```

---

## ⚙️ Installation & Local Setup

### 1. System Dependencies
Ensure you have Python 3.10+ installed. Install the system audio processing framework `ffmpeg` on your machine, as it is required by `pydub` for audio parsing:

```bash
# Windows (Using Chocolatey)
choco install ffmpeg

# Mac
brew install ffmpeg
```

### 2. Install Project Requirements
Clone the repository and install the standard dependencies:
```bash
pip install fastapi uvicorn pydantic requests pypdf python-docx openpyxl beautifulsoup4 pydub faster-whisper pyautogui pandas pillow
```

### 3. Initialize Local Model Dependencies
Ensure **Ollama** is running locally on your system, then pull the lightweight foundational text and parsing models:
```bash
ollama run llama3.2:1b
```

### 4. Launch the Workspace Engine
Execute the app script directly to boot the asynchronous web server:
```bash
python app.py
```
Open your web browser and navigate to **`http://localhost:8000/`** to access your private PQM workspace UI dashboard.

---

## 🛡️ Production & Scalability Roadmap (Next Phases)
*   **Transition to Asynchronous Clients:** Migrating structural network operations inside the core routing endpoints from `requests.post` to `httpx.AsyncClient` to fully preserve non-blocking execution throughout the application loop.
*   **Vector Workspace Engine:** Replacing raw file-looping operations with a local vector index runtime (`ChromaDB` / `LanceDB`) coupled with localized sentence embeddings (`nomic-embed-text`) to achieve horizontal scale as your repository grows.
