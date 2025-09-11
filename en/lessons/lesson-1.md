[Back to table of contents](../index.md)

# 🌀 Lesson 1. Vibe Coding: Why Do We Need It?

## 🎯 Lesson Goal

Understand why we should even bother with LLMs (Large Language Models) and remove the fear of "it's too complicated."

---

## 🤔 Why Programmers Fear LLMs

- "This is all for data scientists, not for me"
- "Too complicated to set up"
- "I don't want my code leaking to the cloud"
- "What if the model starts writing nonsense"

> 👉 The truth is, local LLMs can be launched in 10 minutes.  
> And your laptop can really work as a little Copilot.

---

## 🌍 Cloud vs Local Models

|                    | ☁️ Cloud (ChatGPT, Copilot)           | 💻 Local (Ollama, LM Studio)          |
|--------------------|:-------------------------------------:|:--------------------------------------:|
| Simplicity         | Works immediately                     | Need to set up once                    |
| Privacy            | Code goes to server                   | Everything stays with you              |
| Cost               | Subscription ($10-20/month)           | Free                                   |
| Power              | Strong models (GPT-4.1, Claude 3.5)  | A bit weaker, but enough for code     |
| Offline            | ❌                                    | ✅                                     |

---

## 🪄 Mini Demo: "Function in 5 Seconds"

Let's say you're writing in Python and want to quickly get a factorial function:

**LLM Query:**

> Write a factorial function in Python.

**Model Response:**

```python
def factorial(n: int) -> int:
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)
```

> 👉 Done! The model not only wrote the code but also added types and handled edge cases.

---

## 🌊 What is "Vibe Coding"?

**Regular Programming:**
- Think → Google → Copy code → Adapt

**Vibe Coding:**
- Think → Ask the model → Get code → Adjust for yourself

> 🎵 It's like programming to music: smooth, stress-free, enjoyable.

---

## 📱 Real Use Cases

### 1. **Quick Prototype**
- Need a function to parse JSON? → Ask the model.
- Want to write a simple API? → Model will give you the skeleton.

### 2. **Explaining Others' Code**
- Colleague's code unclear? → Show it to the model, it will explain.
- Found a library on GitHub? → Model will show how to use it.

### 3. **Refactoring**
- Have messy code? → Model will suggest improvements.
- Need to optimize an algorithm? → It will find bottlenecks.

---

## 🚀 Course Plan

1. **Lesson 2** → We'll figure out which models suit your laptop
2. **Lesson 3** → Install Ollama and run the first model
3. **Lesson 4** → Connect to IntelliJ IDEA via Continue
4. **Lesson 5** → Show full "vibe copilot" in action

---

## ✨ Main Lesson Takeaway

**LLMs are not scary, they're useful.**  
Your laptop can become smarter today. All you need is desire and half an hour for setup.

---

**Ready for the next step?** → [Lesson 2: Which Models to Choose](lesson-2.md)
