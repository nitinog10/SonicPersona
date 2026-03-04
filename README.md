# SonicPersona
**AI that learns a person’s vocal identity.**

SonicPersona fine‑tunes a personalized text‑to‑speech (TTS) voice using **LoRA adapters** on a **pre‑trained XTTS‑v2** model. The workflow is built for **Google Colab**, converts user audio into a training set, auto‑transcribes with **Whisper**, trains a memory‑efficient LoRA adapter, and launches a **Gradio** UI for real‑time inference.

---

## ✨ Highlights
- **Personalized voice cloning** with LoRA adapters
- **Auto‑transcription** of uploaded audio with Whisper
- **XTTS‑v2 fine‑tuning** optimized for low VRAM (≈16GB)
- **Gradio demo UI** for live voice generation
- Colab‑ready workflow (minimal local setup)

---

## 🧠 Workflow Overview

```mermaid
flowchart TD
  A[Upload audio & transcripts] --> B[Convert MP4 to WAV (22050 Hz)]
  B --> C[Whisper auto-transcription]
  C --> D[Create LJSpeech-style metadata.csv]
  D --> E[Load XTTS-v2 + LoRA adapters]
  E --> F[Fine-tune (fp16 + grad accumulation)]
  F --> G[Save LoRA weights + speaker embeddings]
  G --> H[Gradio interface for inference]
```

---

## 📸 Preview
![SonicPersona UI](screenshot/Screenshot%202026-03-04%20155202.png)

---

## 📁 Repo Structure
```
.
├── sonicpersona.ipynb   # Primary Colab notebook
├── sonicpersona.py      # Exported notebook script
└── screenshot/
    └── Screenshot 2026-03-04 155202.png
```

---

## 🚀 Quick Start (Google Colab)

1. Open **`sonicpersona.ipynb`** in Google Colab  
2. Run the **Environment Setup** cells  
3. Upload your **audio files** (`.wav` preferred, `.mp4` supported)  
4. Let the notebook:
   - Convert & resample
   - Auto‑transcribe with Whisper
   - Build `metadata.csv`
5. Fine‑tune XTTS‑v2 with LoRA
6. Launch the **Gradio** UI to generate speech

---

## 🎧 Data Requirements

- **Audio**:  
  - `.wav` (preferred) or `.mp4`  
  - Target: **22050 Hz, mono**
- **Transcripts**:  
  - If not provided, Whisper will auto‑generate  
- Output format is **LJSpeech** style:

```
file_id|transcription|normalized_transcription
```

---

## 🔧 Key Dependencies

- `coqui-tts` / `TTS`
- `peft`, `transformers`, `accelerate`, `bitsandbytes`
- `openai-whisper`
- `gradio`, `pydub`

---

## 🧪 Inference

After training, the notebook saves:
- **LoRA adapters**
- **Speaker embeddings**

Then it loads them to generate speech and runs a **Gradio UI** where you can input text and hear your personalized voice.

---

## ⚠️ Notes & Tips

- For best results, use **clean, consistent audio** (5–30 minutes).
- You’ll need a **GPU runtime** in Colab for practical training times.
- The XTTS‑v2 model is **not** a standard HF model, so LoRA requires extra care in targeting module names (handled in the notebook).

---

## 🛡️ Ethics / Safety

This project can clone voices. Use it **only with consent** and follow local laws and ethical guidelines.

---

## ✅ Status

This project currently lives as a **Colab notebook workflow**.  
If you’d like a Python CLI or packaged app, open an issue or request a PR.

---

## 📄 License

No license file is included yet. Add one if you plan to distribute or reuse.
