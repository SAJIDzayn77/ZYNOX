# ZYNOX
Human-centered AI system focused on privacy, modular intelligence, and constraint-aware design.
What is ZYNOX?
ZYNOX is an independent, self-built AGI prototype designed around one principle: AI should support human judgment, not replace it.
Most AI systems are designed around centralization — your data flows to a remote server, decisions are made opaquely, and users are asked to trust a process they cannot see or control. ZYNOX was built from the opposite direction. It begins with user autonomy, privacy-by-default, and constraint-aware design — then builds capability from there.
The system is modular, iterative, and entirely self-funded. Every component was written, tested, and refined on limited hardware, without institutional support or formal mentorship.

System Architecture
ZYNOX is composed of independent, interoperable modules:
ZYNOX/
├── ZYNOX main          # Core AGI loop — memory, reasoning, command dispatch
├── ZYNOX v1            # Face recognition + emotion detection (DeepFace, OpenCV)
├── ZYNOX v2            # Voice-enabled assistant with encrypted memory + email
├── ZYNOX v3            # Emotion-adaptive interaction + LLM integration (Groq/OpenRouter)
├── ZYNOX v4            # Social analytics — NLP, sentiment, profile analysis
├── ZYNOX voice control # Wake-word engine + voice authentication + module orchestrator
├── ZYNOX server        # FastAPI backend — encrypted memory storage + REST API
├── ZYNOX search        # Web search engine integration (SerpAPI + BeautifulSoup)
├── ZYNOX calendar      # Async encrypted calendar with desktop reminders
├── ZYNOX data          # Multi-domain data pipeline (finance, climate, health, geopolitics)
├── ZYNOX knowledge     # Advanced math/science solver (SymPy, SciPy, mpmath)
└── ZYNOX_dashboard     # Real-time Streamlit monitoring dashboard

Module Breakdown
ZYNOX main — Core Loop
The central entry point. Handles persistent memory (JSON-backed), safe AST-based math evaluation, command routing, and session management. Includes a Memory class for structured fact and task storage.
ZYNOX v1 — Vision & Emotion

Face recognition using face_recognition + DeepFace
Real-time emotion detection with configurable alert thresholds
Cloud memory logging with encrypted binary storage (cryptography.Fernet)
LLM integration via OpenRouter (DeepSeek v3) or OpenAI

ZYNOX v2 — Voice Assistant

Full voice I/O via pyttsx3 (TTS) + speech_recognition (STT)
Encrypted calendar events stored in local binary memory
Email reading and composition (IMAP/SMTP)
Vector memory via ChromaDB for semantic retrieval
Mood history tracking (last 15 states)

ZYNOX v3 — Adaptive Interaction

Wake-word detection ("Hey Zynox") with voice authentication via resemblyzer
Text emotion classification using j-hartmann/emotion-english-distilroberta-base
Failover architecture: primary cloud → local backup server
LLM routing: Groq (Llama 3.3 70B) or OpenRouter with graceful fallback

ZYNOX v4 — Social Intelligence

NLP pipeline: TF-IDF, VADER sentiment, textstat readability scoring
Named entity recognition via spaCy
Social profile discovery via SerpAPI
Jinja2-templated HTML report generation
Emotion lexicon-based classification (anger, joy, anxiety, sadness)

ZYNOX voice control — Orchestrator

Unified entry point that launches all modules
Voice authentication (cosine similarity against registered owner embedding)
Auto-starts FastAPI server and Streamlit dashboard as subprocesses
Graceful fallback to text-only mode when microphone unavailable

ZYNOX server — Cloud Backend

FastAPI REST API with API key authentication
Fernet-encrypted SQLite memory store
AWS S3 integration for persistent file storage
Endpoints: /v1/save, /v1/query/{owner_id}, /v1/delete
CORS-enabled for frontend integration

ZYNOX search — Web Intelligence

SerpAPI-powered Google search with image retrieval
BeautifulSoup page scraping with domain extraction (tldextract)
LLM-synthesized summaries via OpenRouter

ZYNOX calendar — Async Scheduler

Fully async calendar engine (asyncio) with file lock safety
Desktop notifications via plyer
All events encrypted at rest (Fernet)
Configurable reminder parsing (minutes/hours)

ZYNOX data — Multi-Domain Intelligence
Weighted Confidence Scoring Model (WCSM) across 7 data domains:
DomainSourcesWeightFinance Coreyfinance, IMF15%Macro InstitutionalTrading Economics, World Bank, OECD15%Hyper-Spatial FusionNASA, OpenWeather, NOAA15%Geopolitical/HealthGDELT, WHO15%Energy InfrastructureEIA10%NLP ContextualNews API10%LLM Meta-AnalysisGroq / Llama 3.3 70B20%
ZYNOX knowledge — Scientific Computing

Symbolic math via SymPy (equations, derivatives, PDEs)
High-precision arithmetic via mpmath (80 decimal places)
Polynomial root finding via Durand-Kerner method
Sparse linear algebra via SciPy
ArXiv paper fetching and parsing
Lagrangian mechanics solver

ZYNOX_dashboard — Monitoring UI

Real-time Streamlit dashboard with 5-second auto-refresh
Emotion score time series, decision frequency charts
Full decision history viewer with raw JSON inspection


Privacy Architecture
ZYNOX gives users three data storage modes:
ModeDescriptionLocal OnlyAll memory stored encrypted on user's own machine — zero cloud transmissionCloudEncrypted sync to personal cloud server via authenticated REST APIHybridSelective sync with user-defined rules; local fallback if cloud unreachable
All stored data is encrypted using cryptography.Fernet (AES-128-CBC). API access requires key authentication. No data is shared with third parties.

Tech Stack
LayerTechnologyCore LanguagePython 3.10+AI/MLTensorFlow Lite, DeepFace, HuggingFace Transformers, resemblyzerLLM IntegrationGroq (Llama 3.3 70B), OpenRouter (DeepSeek v3)Computer VisionOpenCV, face_recognitionNLPspaCy, VADER, TextBlob, TF-IDF, textstatScientific ComputingSymPy, SciPy, NumPy, mpmathBackendFastAPI, SQLite, AWS S3Frontend/DashboardStreamlitEncryptioncryptography (Fernet/AES)Voicepyttsx3, SpeechRecognition, sounddeviceSearchSerpAPI, BeautifulSoup, tldextractMemoryChromaDB (vector), JSON (persistent), SQLite (cloud)

Setup & Installation
Prerequisites

Python 3.10+
A .env file with the following keys:

envOPENROUTER_API_KEY=your_key
GROQ_API_KEY=your_key
CLOUD_API_KEY=your_key
CLOUD_API_URL=https://your-server/v1/save
SERPAPI_KEY=your_key
OPENWEATHER_API_KEY=your_key
NEWS_API_KEY=your_key
NASA_API_KEY=your_key
EMAIL_ADDRESS=your_email
APP_PASSWORD=your_app_password
Install Dependencies
bashpip install -r requirements.txt
Key packages:
bashpip install fastapi uvicorn pyttsx3 speechrecognition deepface face_recognition \
            cryptography chromadb streamlit groq openai aiohttp pandas numpy \
            scikit-learn sympy scipy mpmath spacy textblob vaderSentiment \
            resemblyzer sounddevice tldextract serpapi yfinance plyer python-dotenv
Run
Start the backend server:
bashuvicorn "ZYNOX server":app --reload
Launch the main AGI loop:
bashpython "ZYNOX main"
Start the dashboard:
bashstreamlit run ZYNOX_dashboard
Launch full system with voice control:
bashpython "ZYNOX voice control"

Demo
📺 2-minute demo video
📋 Development roadmap

Current Status & Roadmap

 Core AGI loop with persistent memory
 Voice authentication + wake-word detection
 Encrypted local and cloud memory
 Emotion-adaptive interaction layer
 Multi-domain data intelligence pipeline
 FastAPI backend with S3 support
 Real-time monitoring dashboard
 Mobile-compatible lightweight client
 Multi-user permission model
 Local LLM support (no API key required)
 Formal evaluation benchmarks
 Deployment guide for low-spec hardware


Related Research
Early Sepsis Prediction (Clinical AI)
A separate applied ML project developed using a de-identified ICU dataset:

Architecture: Bidirectional LSTM (TensorFlow Lite)
Model size: ~1.2 MB (edge-optimized)
Performance: 87% AUC on held-out test set
Purpose: Demonstrate clinically meaningful temporal pattern recognition under hardware constraints

This work directly informed ZYNOX's constraint-aware design philosophy.

Design Philosophy
Four questions asked before every design decision:

Does this respect user autonomy? No feature silently collects or transmits data.
Does this work under constraint? If it requires enterprise hardware, it excludes the people who need it most.
Is the cost of this decision visible? Every trade-off is documented.
Who is this actually for? People in low-resource environments who have historically been excluded from — or harmed by — technology built without them in mind.


About
ZYNOX was built independently by Md Sajid (Zayn), a self-taught developer from Gazipur, Bangladesh. Development began with no institutional resources, no mentor, and no formal lab — only a secondhand laptop, open-source documentation, and a commitment to building technology that respects its users.
📧 mdsajidzayn77@gmail.com

ZYNOX is independent research. All development is self-funded and self-directed.
