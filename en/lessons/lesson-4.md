[Back to table of contents](../index.md)

# 🌀 Lesson 4. Integrating LLM into IntelliJ IDEA via Continue

## 🎯 Lesson Goal

Connect Continue to IntelliJ IDEA and use a local model (via Ollama) directly in the editor.

---

## 1. What is Continue?

- Free and open-source IDE plugin.
- Full-featured alternative to GitHub Copilot.
- Supports local models via Ollama.
- Works in both VSCode and JetBrains IDEs (IntelliJ, PyCharm, etc.).

> **👉 Main point** — Continue can work as an agent: insert, modify and explain code directly in the editor.

---

## 2. Installing Continue in IntelliJ IDEA

1. Open `File → Settings → Plugins → Marketplace`.
2. Find **Continue**.
3. Install and restart the IDE.

---

## 3. Configuring Continue for Ollama

After installation, you need to connect Continue with a local model.

1. Start Ollama:

   ```bash
   ollama serve
   ```

   (by default API is available at `http://localhost:11434`).

2. In IntelliJ IDEA open: `IDE and Project settings → Models → Configure (right side by model name)`.
In the opened yaml file make necessary changes.

3. In `config.yaml` file insert. Insert your model to config ("TestModel" in my case):

   ```yaml
   name: Local Assistant
   version: 1.0.1
   schema: v1
   models:
     - name: Llama 3.1 8B
       provider: ollama
       model: llama3.1:8b
       roles:
           - chat
           - edit
           - apply
     - name: Qwen2.5-Coder 1.5B
       provider: ollama
       model: qwen2.5-coder:1.5b-base
       roles:
         - autocomplete
     - name: Nomic Embed
       provider: ollama
       model: nomic-embed-text:latest
       roles:
         - embed
     - name: TestModel
       provider: ollama
       model: my_sexy_model:latest
       roles:
         - chat
         - apply
   context:
     - provider: code
     - provider: docs
     - provider: diff
     - provider: terminal
     - provider: problems
     - provider: folder
     - provider: codebase
   ```

4. Save and restart the IDE.

---

## 4. How to Use Continue

- ✍️ **Inline suggestions** — Continue will suggest completions directly in code (like Copilot).
- 🔍 **Explain** — select code section → Right-click → *Explain with Continue*.
- 🔄 **Refactor** — select function/class → *Refactor with Continue*.
- ⚡️ **Generate tests** — ask to generate unit tests for a method.

---

## 5. Practice: Code Fixing

**Source code (with error):**

```java
public int factorial(int n) {
    if (n == 0) return 0;
    else return n * factorial(n - 1);
}
```

**Continue request:**

> Fix the error in factorial function

**Model response (via Ollama):**

```java
public int factorial(int n) {
    if (n == 0 || n == 1) return 1;
    else return n * factorial(n - 1);
}
```

> **👉 The model found and fixed the error** — now the code is correct.

---

## 📌 Lesson Summary

- Installed and configured Continue in IntelliJ IDEA.
- Connected local model via Ollama.
- Got a "mini-copilot" directly in IDE: suggestions, explanations and refactoring.

---

**Ready for the next step?** → [Lesson 5: Full Vibe Copilot](lesson-5.md)
