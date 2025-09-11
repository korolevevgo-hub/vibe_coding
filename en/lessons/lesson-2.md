[Back to table of contents](../index.md)

# 🌀 Lesson 2. Models: What Types Exist and How Not to Get Confused

## 🎯 Lesson Goal

Learn to read model names, understand which one to choose for your task and your computer's resources.

---

## 🧩 How to Read Model Names

Let's take an example:

```
qwen2.5-coder:7b-instruct-q4_K_S
```

Let's break it down:

| Part | Meaning |
|------|---------|
| qwen2.5 | model family (developer - Alibaba) |
| coder | trained on code, suitable for programming |
| 7b | model size — 7 billion parameters |
| instruct | fine-tuned for instructions (like "answer" / "explain") |
| q4_K_S | quantization level (compression) — reduces memory requirements with minimal quality loss |

---

## 🔖 Common Suffixes and What They Mean

- **instruct** — responds "human-like", not generating dry text.
- **quant (q4, q5, q6)** — compression level (less memory, slightly less accuracy).
- **distill** — distilled model version: lighter and faster.
- **coder** — trained on code, great for autocompletion, refactoring, and explanations.
- **text** — universal language model for text tasks.
- **thinking** — enhanced for logical reasoning and complex thinking.
- **base** — "raw" model without instruction training (usually not needed for beginners).

---

## 💻 Laptop Configuration vs. Suitable Models

### User Experience (Reddit)

> "My old Dell G5 15 5500 (i7, 64 GB RAM, RTX 2070 8 GB VRAM) works fine with 8, 12, and sometimes 14B models."  
> — shows that on powerful laptops with ~8 GB VRAM you can use up to 14B models.

> "Ryzen 7840HS with a Nvidia 4060 8 GB VRAM… Nemo 12B or Qwen 14B with decent quantization might fit, Mistral small (22B at iq3_s) is also okay."

### General Recommendations:

- **16 GB RAM** is usually enough for models up to 7B parameters.
- For **13B models** it's better to have ≥16 GB RAM.
- Some quant versions can run even on **8 GB VRAM**, for example:
  - Mistral 7B with Q4_K_M (~4.37 GB file, ~6.87 GB memory)
  - Gemma 3:4B (Q4_K_M — 1.71 GB file, required memory ~less than 4 GB) — perfect for weak machines

---

## 📊 Table "Laptop → Which Models Will Work"

| Laptop Configuration | Suitable Models |
|---------------------|-----------------|
| 16 GB RAM, weak/integrated GPU | Light quant models: Mistral 7B (q4), Gemma 3:4B — work fast and stable |
| 16–64 GB RAM, discrete GPU (~8 GB VRAM) | OK for 8–12B models, sometimes 14B, especially with quantization |
| Laptops with 24 GB VRAM or more / M3 Max (Apple) | Possible models up to 32B or even 70B (with M3 Max thanks to unified memory) |

---

## 💡 Practical Tips for Choosing

1. **Check your device's RAM and VRAM** volume.
2. **Start with light models** (e.g., quant versions 4–7B) — they start quickly and work comfortably.
3. **If coding is important** — try DeepSeek R1. For reasoning and multilingual — Qwen 2.5.
4. **Devices without powerful GPU** — quant models like Gemma 3:4B are perfect.
5. **If you want to run large models** — there are ways like llama.cpp that distribute load between CPU and GPU, allowing to run up to 70B models on "home" resources.

---

## 📌 Lesson Summary

- Now you know how to read models and match them with laptop resources.
- Quant models are the key to running LLMs on regular hardware.
- Other users' experience helps choose models experimentally.
- In the next lessons we'll prepare for installation via Ollama and running the first model.

---

**Ready for the next step?** → [Lesson 3: Setting Up Local LLM](lesson-3.md)
