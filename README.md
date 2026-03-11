# ZYNOX AGI
### A Privacy-First, Modular AI System Built Under Constraint

> *"I stopped asking what is the most powerful solution, and started asking what is the most responsible and efficient one."*

[![Status](https://img.shields.io/badge/status-active--development-brightgreen)](https://github.com/SAJIDzayn77/ZYNOX)
[![Python](https://img.shields.io/badge/python-3.10%2B-blue)](https://python.org)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
[![Demo](https://img.shields.io/badge/demo-YouTube-red)](https://youtu.be/0t1YKItM-N8)
[![Roadmap](https://img.shields.io/badge/roadmap-Google%20Drive-yellow)](https://drive.google.com/drive/folders/1mdYuRk1ospgyOsbyM5MFdMA_ejTuYmMe?usp=sharing)

---

## What is ZYNOX?

ZYNOX is an independent, self-built AGI prototype designed around one principle: **AI should support human judgment, not replace it.**

Most AI systems are designed around centralization — your data flows to a remote server, decisions are made opaquely, and users are asked to trust a process they cannot see or control. ZYNOX was built from the opposite direction. It begins with user autonomy, privacy-by-default, and constraint-aware design — then builds capability outward from there.

The system is modular, iterative, and entirely self-funded. Every component was written, tested, and refined on limited hardware — without institutional support or formal mentorship.

---

## System Architecture

ZYNOX is composed of 12 independent, interoperable modules:

```
ZYNOX/
├── zynox_main.py            # Core AGI loop — memory, reasoning, command dispatch
├── zynox_v1_vision.py       # Face recognition + real-time emotion detection
├── zynox_v2_voice.py        # Voice assistant with encrypted memory + email
├── zynox_v3_adaptive.py     # Emotion-adaptive interaction + LLM routing
├── zynox_v4_social.py       # Social analytics — NLP, sentiment, profile analysis
├── zynox_voice_control.py   # Wake-word engine + voice auth + module orchestrator
├── zynox_server.py          # FastAPI backend — encrypted REST API + S3 storage
├── zynox_search.py          # Web search integration (SerpAPI + scraping)
├── zynox_calendar.py        # Async encrypted calendar with desktop reminders
├── zynox_data.py            # Multi-domain data intelligence pipeline
├── zynox_knowledge.py       # Advanced math/science solver (SymPy, SciPy, mpmath)
└── zynox_dashboard.py       # Real-time Streamlit monitoring dashboard
```

---

## Module Breakdown

### `zynox_main.py` — Core Loop
The central entry point. Handles persistent memory (JSON-backed), safe AST-based math evaluation, command routing, and session management. Includes a `Memory` class for structured fact and task storage.

### `zynox_v1_vision.py` — Vision & Emotion
- Face recognition using `face_recognition` + `DeepFace`
- Real-time emotion detection with configurable alert thresholds
- Encrypted cloud memory logging via `cryptography.Fernet`
- LLM integration via OpenRouter (DeepSeek v3) or OpenAI

### `zynox_v2_voice.py` — Voice Assistant
- Full voice I/O: `pyttsx3` (TTS) + `speech_recognition` (STT)
- Encrypted calendar events stored in local binary memory
- Email reading and composition (IMAP/SMTP)
- Vector memory via ChromaDB for semantic retrieval
- Mood history tracking across the last 15 states

### `zynox_v3_adaptive.py` — Adaptive Interaction
- Wake-word detection ("Hey Zynox") with voice authentication via `resemblyzer`
- Text emotion classification using `j-hartmann/emotion-english-distilroberta-base`
- Failover architecture: primary cloud → local backup server
- LLM routing: Groq (Llama 3.3 70B) or OpenRouter with graceful fallback

### `zynox_v4_social.py` — Social Intelligence
- NLP pipeline: TF-IDF, VADER sentiment, `textstat` readability scoring
- Named entity recognition via spaCy
- Social profile discovery via SerpAPI
- Jinja2-templated HTML report generation
- Emotion lexicon classification: anger, joy, anxiety, sadness

### `zynox_voice_control.py` — System Orchestrator
- Unified entry point that boots all modules
- Voice authentication via cosine similarity against registered owner embedding
- Auto-launches FastAPI server and Streamlit dashboard as subprocesses
- Graceful text-only fallback when microphone is unavailable

### `zynox_server.py` — Cloud Backend
- FastAPI REST API with API key authentication
- Fernet-encrypted SQLite memory store
- AWS S3 integration for persistent file storage
- Endpoints: `POST /v1/save`, `POST /v1/query/{owner_id}`, `DELETE /v1/delete`
- CORS-enabled for frontend integration

### `zynox_search.py` — Web Intelligence
- SerpAPI-powered Google search with image retrieval
- BeautifulSoup page scraping with domain extraction (`tldextract`)
- LLM-synthesized result summaries via OpenRouter

### `zynox_calendar.py` — Async Scheduler
- Fully async calendar engine with `asyncio` file-lock safety
- Desktop push notifications via `plyer`
- All events encrypted at rest (Fernet)
- Configurable reminder parsing: minutes or hours before event

### `zynox_data.py` — Multi-Domain Intelligence

Weighted Confidence Scoring Model (WCSM) across 7 data domains:

| Domain | Sources | Weight |
|---|---|---|
| Finance Core | yfinance, IMF | 15% |
| Macro Institutional | Trading Economics, World Bank, OECD | 15% |
| Hyper-Spatial Fusion | NASA, OpenWeather, NOAA | 15% |
| Geopolitical / Health | GDELT, WHO | 15% |
| Energy Infrastructure | EIA | 10% |
| NLP Contextual | News API | 10% |
| LLM Meta-Analysis | Groq / Llama 3.3 70B | 20% |

### `zynox_knowledge.py` — Scientific Computing
- Symbolic math via SymPy: equations, derivatives, PDEs
- High-precision arithmetic via mpmath (80 decimal places)
- Polynomial root finding via Durand-Kerner method
- Sparse linear algebra via SciPy
- ArXiv paper fetching and parsing
- Lagrangian mechanics solver

### `zynox_dashboard.py` — Monitoring UI
- Real-time Streamlit dashboard with 5-second auto-refresh
- Emotion score time series + decision frequency bar charts
- Full decision history viewer with raw JSON inspection

---

## Privacy Architecture

ZYNOX gives users three data storage modes:

| Mode | Description |
|---|---|
| **Local Only** | All memory stored encrypted on user's machine — zero cloud transmission |
| **Cloud** | Encrypted sync to personal server via authenticated REST API |
| **Hybrid** | Selective sync with user-defined rules; local fallback if cloud unreachable |

All stored data is encrypted with `cryptography.Fernet` (AES-128-CBC). API access requires key authentication. No data is shared with third parties.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Core Language | Python 3.10+ |
| AI / ML | TensorFlow Lite, DeepFace, HuggingFace Transformers, resemblyzer |
| LLM Integration | Groq (Llama 3.3 70B), OpenRouter (DeepSeek v3) |
| Computer Vision | OpenCV, face_recognition |
| NLP | spaCy, VADER, TextBlob, TF-IDF, textstat |
| Scientific Computing | SymPy, SciPy, NumPy, mpmath |
| Backend | FastAPI, SQLite, AWS S3 |
| Dashboard | Streamlit |
| Encryption | cryptography (Fernet / AES-128-CBC) |
| Voice | pyttsx3, SpeechRecognition, sounddevice |
| Search | SerpAPI, BeautifulSoup, tldextract |
| Memory | ChromaDB (vector), JSON (persistent), SQLite (cloud) |

---

## Setup & Installation

### 1. Clone the Repository

```bash
git clone https://github.com/SAJIDzayn77/ZYNOX.git
cd ZYNOX
```

### 2. Configure Environment

```bash
cp .env.example .env
# Edit .env and add your API keys
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

### 4. Run

**Backend server:**
```bash
uvicorn zynox_server:app --reload
```

**Main AGI loop:**
```bash
python zynox_main.py
```

**Monitoring dashboard:**
```bash
streamlit run zynox_dashboard.py
```

**Full system with voice:**
```bash
python zynox_voice_control.py
```

---

## Demo

📺 [Watch the 2-minute ZYNOX demo](https://youtu.be/0t1YKItM-N8)

📋 [Development roadmap](https://drive.google.com/drive/folders/1mdYuRk1ospgyOsbyM5MFdMA_ejTuYmMe?usp=sharing)

---

## Roadmap

- [x] Core AGI loop with persistent memory
- [x] Voice authentication + wake-word detection
- [x] Encrypted local and cloud memory
- [x] Emotion-adaptive interaction layer
- [x] Multi-domain data intelligence pipeline (WCSM)
- [x] FastAPI backend with AWS S3 support
- [x] Real-time Streamlit monitoring dashboard
- [ ] Mobile-compatible lightweight client
- [ ] Multi-user permission model
- [ ] Local LLM support (no API key required)
- [ ] Formal evaluation benchmarks
- [ ] Deployment guide for low-spec hardware

---

## Related Research

### Early Sepsis Prediction — Clinical AI

A separate applied ML project developed using a de-identified ICU patient dataset:

| Detail | Value |
|---|---|
| Architecture | Bidirectional LSTM (TensorFlow Lite) |
| Model size | ~1.2 MB (edge-optimized) |
| Performance | 87% AUC on held-out test set |
| Purpose | Clinically meaningful temporal pattern recognition under hardware constraints |

This research directly informed ZYNOX's constraint-aware design philosophy: if a system cannot operate responsibly on modest hardware, it cannot serve the environments that need it most.

---

## Design Philosophy

Four questions asked before every design decision:

1. **Does this respect user autonomy?** No feature silently collects or transmits data.
2. **Does this work under constraint?** If it requires enterprise hardware, it excludes the people who need it most.
3. **Is the cost of this decision visible?** Every trade-off is documented.
4. **Who is this actually for?** People in low-resource environments who have historically been excluded from — or harmed by — technology built without them.

---

## About

ZYNOX was built independently by **Md Sajid (Zayn)**, a self-taught developer from Gazipur, Bangladesh. Development began with no institutional resources, no mentor, and no formal lab — only a secondhand laptop, open-source documentation, and a commitment to building technology that respects its users.

📧 [mdsajidzayn77@gmail.com](mailto:mdsajidzayn77@gmail.com)

---

*ZYNOX is independent research. All development is self-funded and self-directed.*
