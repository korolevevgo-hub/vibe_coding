[Back to table of contents](../index.md)

# 🌀 Lesson 5. Full Vibe Copilot

## 🎯 Lesson Goal

Learn to use local LLM not only for suggestions, but for full code support: from refactoring to test generation.

---

## 1. What's the Difference Between Suggestions and "Copilot"?

- **Suggestions** = model completes a line of code.
- **Copilot** = model works as a partner: understands context, suggests fixes for entire files, writes tests and explains architecture.

> **👉 With Continue + Ollama** you get the second option — your personal local Copilot.

---

## 2. How to Enable "Copilot" Mode in Continue

1. Open `Settings → Tools → Continue`.
2. Make sure these are enabled in settings:
   - **Inline suggestions** (code suggestions).
   - **Agent mode** (working with entire file context).
3. As a model specify (example):

   ```
   qwen2.5-coder:7b-instruct-q4_K_S
   ```

---

## 3. Practice: Java Class Refactoring

### Source code (unoptimized):

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

### Continue request:

> Refactor UserService class:
> - Make code more readable and modern
> - Replace manual loop with collection methods
> - Add logging instead of System.out.println

### Model response (via Ollama):

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

> **👉 The model did** what usually takes 15–20 minutes of manual refactoring.

---

## 4. Test Generation

### Continue request:

> Generate JUnit tests for UserService class

### Model response:

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

> **👉 You immediately have** full-fledged unit tests without manual routine.

---

## 5. What Else Can Your Vibe Copilot Do?

- Explain others' code.
- Generate documentation.
- Give architecture advice.
- Work offline without leaking code to the cloud.

---

## 📌 Course Summary

- You learned to run local models via Ollama.
- Figured out which models suit your laptop.
- Connected Continue to IntelliJ IDEA.
- Got a local Copilot that can:
  - complete code,
  - refactor classes,
  - write tests,
  - explain others' code.

---

## ✨ Conclusion

**Welcome to vibe coding: now your laptop became smarter, and coding became easier.**

---

**Go to the final cheat sheet** → [Epilogue: Vibe Coding Cheat Sheet](tldr.md)
