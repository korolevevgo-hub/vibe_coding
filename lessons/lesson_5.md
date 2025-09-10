[Назад к оглавлению](../index.md)

# 🌀 Урок 5. Полный вайб-копилот

## 🎯 Цель урока

Научиться использовать локальную LLM не только для подсказок, но и для полного сопровождения кода: от рефакторинга до генерации тестов.

---

## 1. В чём разница между подсказками и «копилотом»?

- **Подсказки** = модель дописывает строку кода.
- **Копилот** = модель работает как напарник: понимает контекст, предлагает правки целого файла, пишет тесты и объясняет архитектуру.

> **👉 С Continue + Ollama** у тебя появляется второй вариант — твой личный локальный Copilot.

---

## 2. Как включить режим «копилота» в Continue

1. Открой `Settings → Tools → Continue`.
2. Убедись, что в настройках включены:
   - **Inline suggestions** (подсказки в коде).
   - **Agent mode** (работа с контекстом целого файла).
3. В качестве модели укажи (пример):

   ```
   qwen2.5-coder:7b-instruct-q4_K_S
   ```

---

## 3. Практика: рефакторинг Java-класса

### Исходный код (неоптимизированный):

```java
public class UserService {
    private List<String> users = new ArrayList<>();

    public void addUser(String user) {
        if (!users.contains(user)) {
            users.add(user);
        } else {
            System.out.println("User already exists");
        }
    }

    public void removeUser(String user) {
        for (int i = 0; i < users.size(); i++) {
            if (users.get(i).equals(user)) {
                users.remove(i);
                break;
            }
        }
    }
}
```

### Запрос в Continue:

> Рефактори класс UserService:
> - Сделай код более читаемым и современным
> - Замени ручной цикл на методы коллекций
> - Добавь логирование вместо System.out.println

### Ответ модели (через Ollama):

```java
import java.util.ArrayList;
import java.util.List;
import java.util.logging.Logger;

public class UserService {
    private static final Logger logger = Logger.getLogger(UserService.class.getName());
    private final List<String> users = new ArrayList<>();

    public void addUser(String user) {
        if (users.contains(user)) {
            logger.warning("User already exists: " + user);
            return;
        }
        users.add(user);
    }

    public void removeUser(String user) {
        if (users.remove(user)) {
            logger.info("Removed user: " + user);
        } else {
            logger.warning("User not found: " + user);
        }
    }
}
```

> **👉 Модель сделала** то, что обычно занимает 15–20 минут рефакторинга вручную.

---

## 4. Генерация тестов

### Запрос в Continue:

> Сгенерируй JUnit-тесты для класса UserService

### Ответ модели:

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class UserServiceTest {

    private UserService userService;

    @BeforeEach
    void setUp() {
        userService = new UserService();
    }

    @Test
    void addUser_shouldAddNewUser() {
        userService.addUser("Alice");
        assertTrue(userService.getUsers().contains("Alice"));
    }

    @Test
    void addUser_shouldNotAddDuplicate() {
        userService.addUser("Bob");
        userService.addUser("Bob");
        assertEquals(1, userService.getUsers().size());
    }

    @Test
    void removeUser_shouldRemoveExistingUser() {
        userService.addUser("Charlie");
        userService.removeUser("Charlie");
        assertFalse(userService.getUsers().contains("Charlie"));
    }

    @Test
    void removeUser_shouldNotFailOnMissingUser() {
        userService.removeUser("NonExisting");
        assertTrue(userService.getUsers().isEmpty());
    }
}
```

> **👉 У тебя сразу есть** полноценные юнит-тесты без ручной рутины.

На самом деле все эти копилоты пока очень плохо пишут unit-тесты, но с рефакторингом и объяснением кода у них всё отлично.
На более или менее сложных классах они точно не помогут, по крайней мере пока

---

## 5. Что ещё может твой вайб-копилот?

- Объяснять чужой код.
- Генерировать документацию.
- Давать советы по архитектуре.
- Работать оффлайн, не сливая код в облако.

---

## 📌 Итоги курса

- Ты научился запускать локальные модели через Ollama.
- Разобрался, какие модели подходят для твоего ноутбука.
- Подключил Continue в IntelliJ IDEA.
- Получил локального Copilot, который умеет:
  - дописывать код,
  - рефакторить классы,
  - писать тесты,
  - объяснять чужой код.

---

## ✨ Заключение

**Добро пожаловать в вайб-кодинг: теперь твой ноутбук стал умнее, а кодинг — легче.**

---

## Подведем итоги [🌊 Послесловие: Шпаргалка по вайб-кодингу](tldr.md)