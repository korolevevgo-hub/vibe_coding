[Back to table of contents](../index.md)

# 🌀 Lesson 3. Setting Up Local LLM with Ollama

## 🎯 Lesson Goal

Install Ollama, download a model and run LLM locally — to make sure everything works, and then connect it to IDE.

---

## 1. Installing Ollama

### Windows / macOS / Linux (including WSL)

- Go to the [official Ollama website](https://ollama.com/) and download the installer for your operating system. After installation, the application will run in the background or in the system tray.
- On Linux (Ubuntu, WSL) you can install via command:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

---

## 2. Installation Check and Service Launch

- Check version and functionality:

```bash
ollama --version
```

- Start the server:

```bash
ollama serve
```

- Go to `http://localhost:11434/` in your browser. It should display "Ollama is running" message.

---

## 3. Downloading and Running Models

- You can download and run a model with one command:

```bash
ollama pull llama3
ollama run llama3
```

Or with one command directly — `ollama run` will download and run the model if it doesn't exist.

- Below is an example of downloading CodeUp — a model for programming (~13B, requires ≥16 GB RAM):

```bash
ollama pull codeup
ollama run codeup
```

---

## 4. Working with Models: Basic Commands

| Command | Purpose |
|---------|---------|
| `ollama list` | Show all downloaded models |
| `ollama ps` | Show running models |
| `ollama stop <model>` | Stop running model |
| `ollama rm <model>` | Remove model from computer |
| `ollama show <model>` | Show model information |
| `ollama create ...` | Create custom model from Modelfile |

---

## 5. Alternative: GUI Version for Windows 11

For Windows 11, an official Ollama GUI is now available — much more convenient for beginners:

- Supports drag-&-drop for images and files, model context settings and interaction without terminal.
- Compatible with CPU and GPU, but ≥16 GB RAM is recommended for comfortable work.

---

## 6. Basic Usage Example

After installation and model launch, you can start a dialogue:

```bash
ollama run llama3
```

Example dialogue:
```
>>> Write a function to sort an array in Python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr
```

---

## 📌 Lesson Summary

- Installed Ollama and ran the first model locally.
- Learned basic commands for model management.
- Made sure LLM works and can generate code.
- Ready for IDE integration in the next lesson.

---

**Ready for the next step?** → [Lesson 4: Connecting to IntelliJ IDEA via Continue](lesson-4.md)
