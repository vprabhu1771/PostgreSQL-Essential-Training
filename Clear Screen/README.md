In **psql** (the PostgreSQL command-line tool), there’s no direct SQL command like `clear`, but there are a few ways to **clear the screen** 👇

---

### 🧹 1. Shortcut Method

**Press:**

```
Ctrl + L
```

✅ This immediately clears the screen — works in **Linux**, **macOS**, and **Windows (Git Bash or PowerShell)**.

---

### 🧾 2. Using Command

You can also run:

```sql
\! clear
```

👉 This tells `psql` to execute the shell command `clear`.

If you’re on **Windows**, use:

```sql
\! cls
```

---

### 💡 Tip

If neither works (for example, on limited terminals), you can simply type:

```sql
\q
```

to quit `psql`, then reconnect:

```bash
psql -U postgres -d your_database
```

---

So:

| Platform      | Command / Shortcut       |
| ------------- | ------------------------ |
| Linux / macOS | `Ctrl + L` or `\! clear` |
| Windows       | `Ctrl + L` or `\! cls`   |

---

Would you like me to give you a quick list of the **most useful `psql` commands** (like list databases, tables, etc.) too?
