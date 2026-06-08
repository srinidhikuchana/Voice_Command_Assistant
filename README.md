# Klyra Your Personal AI Voice Assistant

> **Live Demo [voicecommandassistant.streamlit.app](https://voicecommandassistant.streamlit.app/)**

Klyra is a real-time, emotion-aware AI voice assistant built with Streamlit. Speak or type Klyra listens, understands how you feel, and responds with a warm, human-like voice in multiple languages.

---

## Features

| Feature | Details |
|---|---|
| **Voice Input** | Record directly in-browser via Streamlit's audio input |
| **AI Responses** | Powered by GPT-4o-mini via OpenRouter |
| **Speech Transcription** | Groq Whisper (`whisper-large-v3-turbo`) for fast, accurate STT |
| **Text-to-Speech** | Auto-plays responses using gTTS |
| **Emotion Detection** | SpeechBrain wav2vec2 (audio) + keyword analysis (text) |
| **Multilingual** | 15 languages including Hindi, Telugu, Tamil, French, Japanese & more |
| **Auto Language Detection** | Detects the language you're speaking and responds accordingly |
| **Web Search** | Real-time DuckDuckGo search for news, weather, movie releases, scores |
| **Live Weather** | OpenWeatherMap integration for real-time weather queries |
| **Dark / Light Mode** | Toggle between themes from the sidebar |
| **Date & Time Aware** | Always knows today's date and current year |

---

## Emotion-Aware Responses

Klyra detects your emotional state from **both your voice and your words** and adapts its tone accordingly:

| Detected Emotion | Klyra's Response Style |
|---|---|
| Sad | Caring, gentle, empathetic "Aww, is everything okay?" |
| Excited / Happy | High-energy, enthusiastic "Wohoooo!! " |
| Angry | Calm and understanding |
| Neutral | Natural, conversational |

Audio emotion uses **SpeechBrain `emotion-recognition-wav2vec2-IEMOCAP`**. Text emotion uses keyword matching. The two are merged with audio taking priority when confidence > 45%.

---

## Tech Stack

- **Frontend / App**: [Streamlit](https://streamlit.io/)
- **LLM**: GPT-4o-mini via [OpenRouter](https://openrouter.ai/)
- **Speech-to-Text**: [Groq](https://groq.com/) `whisper-large-v3-turbo`
- **Text-to-Speech**: [gTTS](https://pypi.org/project/gTTS/)
- **Emotion Recognition**: [SpeechBrain](https://speechbrain.github.io/) wav2vec2 IEMOCAP
- **Web Search**: DuckDuckGo HTML + API
- **Weather**: [OpenWeatherMap API](https://openweathermap.org/api)

---

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/your-username/klyra.git
cd klyra
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Add your API keys

Create a `.streamlit/secrets.toml` file:

```toml
OPENROUTER_API_KEY = "sk-or-v1-..."
GROQ_API_KEY = "gsk_..."
OPENWEATHER_API_KEY = "..." # optional for weather queries
```

### 4. Run the app

```bash
streamlit run app.py
```

---

## Deploying to Streamlit Cloud

1. Push your code to a GitHub repository
2. Go to [share.streamlit.io](https://share.streamlit.io/) and connect your repo
3. Under **App Settings Secrets**, add your API keys (same format as above)
4. Deploy!

> **Note**: SpeechBrain downloads the emotion model (~200MB) on first run. This takes about 1 minute on cold start subsequent runs are instant.

---

## Supported Languages

English Hindi Telugu Tamil French Spanish German Japanese Korean Chinese Arabic Portuguese Russian Bengali Auto-Detect

---

## API Keys Required

| Service | Purpose | Get it here |
|---|---|---|
| OpenRouter | GPT-4o-mini LLM responses | [openrouter.ai](https://openrouter.ai/) |
| Groq | Whisper transcription | [console.groq.com](https://console.groq.com/) |
| OpenWeatherMap | Live weather *(optional)* | [openweathermap.org](https://openweathermap.org/api) |

---

## Project Structure

```
klyra/
 app.py # Main Streamlit application
 requirements.txt # Python dependencies
 .streamlit/
 secrets.toml # API keys (not committed to git)
 pretrained_models/ # SpeechBrain model cache (auto-created)
```

---

## License

MIT License free to use, modify, and distribute.
