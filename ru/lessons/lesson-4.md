[Назад к оглавлению](../index.md)

# 🌀 Урок 4. Интеграция LLM в IntelliJ IDEA через Continue

## 🎯 Цель урока

Подключить Continue к IntelliJ IDEA и использовать локальную модель (через Ollama) прямо в редакторе.

---

## 1. Что такое Continue?

- Бесплатный и open-source плагин для IDE.
- Полноценная альтернатива GitHub Copilot.
- Поддерживает локальные модели через Ollama.
- Работает и в VSCode, и в JetBrains IDE (IntelliJ, PyCharm и др.).

> **👉 Главное** — Continue умеет работать как агент: вставлять, изменять и объяснять код прямо в редакторе.

---

## 2. Установка Continue в IntelliJ IDEA

1. Открой `File → Settings → Plugins → Marketplace`.
2. Найди **Continue**.
3. Установи и перезапусти IDE.

---

## 3. Настройка Continue для Ollama

После установки нужно связать Continue с локальной моделью.

1. Запусти Ollama:

   ```bash
   ollama serve
   ```

   (по умолчанию API доступен на `http://localhost:11434`).

2. В IntelliJ IDEA открой: `Settings → Tools → Continue`.

3. Укажи конфигурацию модели (пример):

   ```json
   {
     "models": [
       {
         "title": "Qwen Coder",
         "provider": "ollama",
         "model": "qwen2.5-coder:7b-instruct-q4_K_S"
       }
     ]
   }
   ```

4. Сохрани и перезапусти IDE.

---

## 4. Как использовать Continue

- ✍️ **Inline-подсказки** — Continue будет предлагать дополнения прямо в коде (как Copilot).
- 🔍 **Explain** — выдели участок кода → ПКМ → *Explain with Continue*.
- 🔄 **Refactor** — выдели функцию/класс → *Refactor with Continue*.
- ⚡️ **Generate tests** — попроси сгенерировать юнит-тесты для метода.

---

## 5. Практика: исправление кода

**Исходный код (с ошибкой):**

```java
public int factorial(int n) {
    if (n == 0) return 0;
    else return n * factorial(n - 1);
}
```

**Запрос в Continue:**

> Исправь ошибку в функции factorial

**Ответ модели (через Ollama):**

```java
public int factorial(int n) {
    if (n == 0 || n == 1) return 1;
    else return n * factorial(n - 1);
}
```

> **👉 Модель нашла и исправила ошибку** — теперь код корректный.

---

## 📌 Итоги урока

- Установили и настроили Continue в IntelliJ IDEA.
- Подключили локальную модель через Ollama.
- Получили «мини-копилота» прямо в IDE: подсказки, объяснения и рефакторинг.

---

**Готов к следующему шагу?** → [Урок 5: Полный вайб-копилот](lesson-5.md)
