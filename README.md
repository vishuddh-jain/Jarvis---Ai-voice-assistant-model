# Jarvis: Edge-Computed Voice Assistant with Cloud Fallback

A fully local python voice assistant featuring a dual-brain architecture. The system uses low-latency cloud inference when online and automatically falls back to secure, local on-device neural networks during network outages.

## 🛠️ System Requirements & Prerequisite Assets

### 1. Hardware & OS
* **OS:** Windows 10/11 (Required for the `pyttsx3` SAPI5 native audio driver).
* **Hardware:** Microphone and speakers properly configured in OS settings.

### 2. Required External Software
* **Ollama Desktop Client:** Must be installed and running locally.
  * *Local Model Required:* Run `ollama pull qwen2.5:0.5b` in the terminal.
* **Groq API Cloud Account:** A free API Key from `console.groq.com`.

### 3. Offline Language Database (Vosk)
* **Download:** `vosk-model-small-en-us-0.15.zip` from alphacephei.com/vosk/models.
* **Installation:** Must be unzipped and placed inside the active Python virtual environment's site packages folder:
  `\.venv\Lib\site-packages\speech_recognition\models\vosk\`
  *(The directory should directly contain the 'am', 'graph', and 'ivector' folders).*

---

## 📂 Project Directory Structure

```text
1_mega_project/
│
├── .env                  # Secure file holding: GROQ_API_KEY=gsk_...
├── requirements.txt      # Python dependencies list
├── musicLibrary.py       # Custom local library for mapping song strings to URLs
│
├── models/
│   └── ai_assistant.py   # The Dual-Brain Routing Core (Groq <-> Ollama)
│
└── main_offline.py       # The Main Application Loop (Vosk Input -> Audio Chunk Queue)