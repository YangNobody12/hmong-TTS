# 🗣️ Hmong Text-to-Speech (TTS) with Unsloth + LoRA

Hmong-TTS is a high-quality **Text-to-Speech system for the Hmong language**, trained and optimized using **Unsloth** with **LoRA (Robust Low-Rank Adaptation)**. This project aims to provide fast, memory-efficient, and accessible speech models for research, education, and community-based technology.

---

## 🚀 Key Features

* ⚡ **1.5× Faster Training & Inference** using Unsloth Optimizations
* 💾 **50% Less GPU Memory Usage** with LoRA + Flash Attention 2
* 🔊 Generates **natural Hmong speech** with expressive tone and clarity
* 🔐 Full support for **low‑resource training** (small datasets)
* 🧠 Supports **Sesame CSM**, **Orpheus**, and **Transformer‑based TTS models** (CrisperWhisper, Spark, etc.)
* 🧩 Easy fine‑tuning with LLM‑style adapters for TTS

---

## 📌 Why LoRA?

**LoRA (Robust Low-Rank Adaptation)** is a fine‑tuning method designed to be:

* 🧠 **Robust on sparse data** — ideal for low‑resource languages like Hmong
* 🧮 **Efficient with parameters** — trains only small adapter layers
* 🔧 **Compatible with TTS** models that use long audio context

LoRA adapts only the most important latent representations, allowing us to:

> 🏎️ Train faster ⬆️ — 🧠 Use less memory ⬇️ — 🎤 Maintain speech quality 🎯

---

## 🧪 Flash Attention 2 Support

This project uses **Flash Attention 2**, enabling:

* 🏎️ Faster attention computation
* 🔥 Less VRAM usage
* 📏 Efficient long‑context speech modeling

**Perfect for TTS**, where long audio sequences are required.

---

## 📂 Dataset Format

To fine-tune Hmong TTS using **Unsloth + LoRA**, the dataset must contain:

### **🧾 Metadata File (`metadata.csv`)**

Format (pipe-separated):

```
filename|text
```

Example:

```
001.wav|Nyob zoo os, koj nyob li cas?
002.wav|Ua tsaug ntau rau koj qhov kev pab.
```

### **🎧 Audio Files**

* Format: **WAV 16-bit PCM**
* Sample rate: **16 kHz or 22.05 kHz**
* Mono channel
* File names must match `metadata.csv`

```
wavs/
 ├── 001.wav
 ├── 002.wav
 └── ...
```

### **📌 Optional: JSON Format**

If using JSON, follow this structure:

```json
[
  {
    "audio": "wavs/001.wav",
    "text": "Nyob zoo os, koj nyob li cas?"
  },
  {
    "audio": "wavs/002.wav",
    "text": "Ua tsaug ntau rau koj qhov kev pab."
  }
]
```

📍 **Tip:** Ensure all text is normalized (no emojis, no special characters, standardized tones if applicable).

---

## 🧠 LoRA Architecture Explained

**LoRA (Low-Rank Adaptation)** enables efficient fine‑tuning by adding small trainable layers to large TTS models instead of updating the entire model.

### 🔎 How LoRA Works

In a transformer layer with weight matrix:

```
W ∈ ℝ(d × k)
```

LoRA adds two small matrices:

```
B ∈ ℝ(d × r)
A ∈ ℝ(r × k)   (where r ≪ d, k)
```

During fine‑tuning, only **A and B** are trained while the original weights are frozen:

```
W' = W + B · A
```

### 🎤 Why LoRA for TTS?

| Model Component    | What LoRA Learns                      |
| ------------------ | ------------------------------------- |
| Attention Layer    | Rhythm, tone, syllable timing         |
| MLP / Feed‑forward | Timbre, accent, vocal shape           |
| Decoder Blocks     | Speech smoothness, expressive quality |

🔊 **Perfect for Hmong**, where training data is limited. LoRA learns important voice traits without overfitting.

### 🔥 LoRA = Improved LoRA for Low‑Resource Speech

| Method         | Best For                                  |
| -------------- | ----------------------------------------- |
| LoRA           | Fast & memory‑efficient fine‑tuning       |
| LoRA           | Low‑resource languages and noisy datasets |
| LoRA + Unsloth | Fast + Low memory + Robust + High quality |

> 🧠 **LoRA is LoRA optimized for sparse and small datasets like Hmong TTS.**

### 📌 Summary in 15 Seconds

* LoRA = Add small trainable layers instead of modifying the full model
* Trains **only BA**, freezes base model
* Uses **very little memory**, trains **1.5× faster**
* LoRA = **LoRA built for low‑resource speech** (ideal for Hmong)

---
