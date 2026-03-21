# 🎭 AI Excuse Generator

An AI-powered excuse generation system built with a large language model (Zephyr-7B), featuring multilingual support, voice output, smart ranking, and SMS/email draft templates.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1C3yE3xbftAY2ObNgXqJGnbilnfJ5O4G9)

---

## Features

- **AI-Generated Excuses** — Uses the Zephyr-7B LLM to generate contextual, believable excuses
- **Multiple Scenarios** — Supports work, school, social, and family contexts
- **Tone & Urgency Control** — Choose from professional, sincere, or casual tones with low/medium/high urgency
- **Multilingual Support** — Translates excuses to Hindi using Helsinki-NLP MarianMT
- **Voice Output** — Converts excuses to speech using Google Text-to-Speech (gTTS)
- **Smart Ranking** — Scores excuses on clarity and empathy metrics
- **History Tracking** — Logs all generated excuses with timestamps to CSV
- **Favorites System** — Save and retrieve your best excuses
- **SMS & Email Templates** — Auto-generates ready-to-send message drafts
- **Apology Mode** — Generates heartfelt, emotional apology excuses
- **Time-Based Suggestions** — Recommends excuse type based on time of day

---

## Tech Stack

| Component | Technology |
|-----------|------------|
| LLM | `HuggingFaceH4/zephyr-7b-beta` |
| Translation | `Helsinki-NLP/opus-mt-en-hi` (MarianMT) |
| Framework | PyTorch + HuggingFace Transformers |
| Voice | gTTS (Google Text-to-Speech) |
| Data | Pandas |
| Environment | Google Colab (GPU recommended) |

---

## Project Structure

```
ai-excuse-generator/
├── excuse_generator.ipynb   # Main notebook with all features
├── README.md                # Project documentation
└── .gitignore               # Excludes sensitive files (e.g., kaggle.json)
```

---

## Getting Started

### 1. Open in Google Colab

Click the badge above or open `excuse_generator.ipynb` directly in [Google Colab](https://colab.research.google.com/).

> **Note:** A GPU runtime is strongly recommended (Runtime → Change runtime type → T4 GPU) for loading the Zephyr-7B model.

### 2. Install Dependencies

The notebook handles installations automatically:

```python
!pip install transformers torch accelerate gtts
```

### 3. Authenticate with Hugging Face

You'll need a free Hugging Face account to download the Zephyr-7B model:

```python
!hf auth login
```

### 4. Run the Notebook

Run all cells top to bottom. The demo section at the end shows all features in action.

---

## Usage Examples

```python
# Generate a professional work excuse in English
excuse, proof = generate_excuse("work", "professional", "high", "en")

# Generate a school excuse in Hindi
excuse, proof = generate_excuse("school", "sincere", "low", "hi")

# Apology mode
apology_excuse("family", "high", "en")

# Convert to speech
excuse_to_speech(excuse)

# View top ranked excuses
rank_excuses()

# View history
show_history(5)
```

---

## How It Works

```
User Input (scenario, tone, urgency, language)
        ↓
Zephyr-7B LLM generates excuse
        ↓
[Optional] MarianMT translates to Hindi
        ↓
Supportive text appended
        ↓
Scored (clarity + empathy) → saved to history
        ↓
Output: text + SMS/email draft + voice audio
```

---

## Scoring System

Each generated excuse is automatically scored on two metrics:

- **Clarity Score** — Based on average word length (shorter words = clearer communication)
- **Empathy Score** — Detects empathy markers like "sorry", "apologize", "understand", "क्षमा" etc.

The combined score is used to rank your top 5 best excuses.

---

## Requirements

- Python 3.8+
- Google Colab (free tier works, GPU recommended)
- Hugging Face account (free)
- ~15GB RAM for Zephyr-7B model loading

---

## Author

**Samya Laddha** — [GitHub](https://github.com/SamyaLaddha)

---

## Acknowledgements

- [Zephyr-7B](https://huggingface.co/HuggingFaceH4/zephyr-7b-beta) by HuggingFace H4
- [Helsinki-NLP MarianMT](https://huggingface.co/Helsinki-NLP/opus-mt-en-hi) for translation
- [gTTS](https://gtts.readthedocs.io/) for voice synthesis
