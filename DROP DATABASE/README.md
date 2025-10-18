Here’s a quick and safe guide to **dropping (deleting) a database** in **PostgreSQL** 👇

---

## ⚠️ Important Warning

🧨 **Dropping a database permanently deletes all its data.**
There is **no undo**, so double-check before running the command.

---

## 🧾 SQL Syntax

```sql
DROP DATABASE database_name;
```

---

### ✅ Example

If your database is called `shop_db`:

```sql
DROP DATABASE shop_db;
```

---

## ⚙️ Rules / Conditions

1. You **cannot drop** a database **while you are connected to it**.
   You must switch to another database first — usually `postgres` or `template1`.

   Example:

   ```sql
   \c postgres
   DROP DATABASE shop_db;
   ```

2. You must have **superuser** or **database owner** privileges.

---

## 💻 From pgAdmin

1. Right-click the database you want to remove.
2. Choose **Delete/Drop**.
3. Confirm the action.

---

## 🚫 Force Drop (If sessions are active)

If the database is in use (active connections exist), you can force-disconnect them first:

```sql
-- Disconnect all active connections to the database
SELECT pg_terminate_backend(pid)
FROM pg_stat_activity
WHERE datname = 'shop_db';

-- Then drop the database
DROP DATABASE shop_db;
```

---

✅ **Summary:**

| Action                 | Command                                  |
| ---------------------- | ---------------------------------------- |
| Connect to safe DB     | `\c postgres`                            |
| Drop database          | `DROP DATABASE shop_db;`                 |
| Force drop (if in use) | `pg_terminate_backend` + `DROP DATABASE` |

---

Would you like me to show how to **drop only specific tables instead of the whole database** (useful when you want a reset but not total deletion)?
