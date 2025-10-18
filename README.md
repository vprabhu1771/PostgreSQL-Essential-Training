# PostgreSQL-Essential-Training
 
Let’s go step-by-step through **PostgreSQL** and **pgAdmin** basics — from installation to essential commands and UI usage 👇

---

## 🧠 1. What is PostgreSQL?

**PostgreSQL** (or **Postgres**) is an open-source **relational database management system (RDBMS)**.
It stores data in **tables** and supports **SQL** (Structured Query Language) for querying and managing data.

✅ **Key Features:**

* ACID-compliant (safe transactions)
* Supports advanced data types (JSON, arrays, etc.)
* Extensible (you can add custom functions, data types)
* Ideal for large-scale, production-grade applications

---

## 🧩 2. What is pgAdmin?

**pgAdmin** is a **GUI (Graphical User Interface)** tool for managing PostgreSQL databases.
It allows you to:

* Connect to local or remote PostgreSQL servers
* Create databases, tables, and queries visually
* Run SQL scripts
* Backup and restore databases

---

## ⚙️ 3. Installation

### 🪟 On Windows:

1. Go to [https://www.postgresql.org/download/](https://www.postgresql.org/download/)
2. Download the installer (includes PostgreSQL, pgAdmin, and StackBuilder).
3. During installation:

   * Set **superuser password** (for user `postgres`)
   * Keep default port **5432**
   * Choose to install **pgAdmin 4**

After installation, open **pgAdmin 4**.

---

## 🔑 4. Connect to Server in pgAdmin

1. Open **pgAdmin 4**
2. When prompted, enter the **master password** (the one you set during setup)
3. Right-click **Servers → Register → Server**
4. Under **Connection** tab:

   * **Host name/address:** `localhost`
   * **Port:** `5432`
   * **Username:** `postgres`
   * **Password:** your password
5. Click **Save**

Now you’re connected!

---

## 🧱 5. Create a Database

### Using pgAdmin:

1. Right-click **Databases → Create → Database**
2. Enter database name, e.g., `shop_db`
3. Click **Save**

### Using SQL:

```sql
CREATE DATABASE shop_db;
```

---

## 🧩 6. Create a Table

### Example (SQL Query):

```sql
CREATE TABLE products (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  price DECIMAL(10,2),
  in_stock BOOLEAN DEFAULT true
);
```

---

## 🧾 7. Insert Data

```sql
INSERT INTO products (name, price, in_stock)
VALUES
('Laptop', 85000.00, true),
('Mouse', 599.00, true);
```

---

## 🔍 8. Query Data

```sql
SELECT * FROM products;
```

Result:

| id | name   | price    | in_stock |
| -- | ------ | -------- | -------- |
| 1  | Laptop | 85000.00 | true     |
| 2  | Mouse  | 599.00   | true     |

---

## ⚡ 9. Update & Delete

```sql
-- Update
UPDATE products SET price = 799.00 WHERE name = 'Mouse';

-- Delete
DELETE FROM products WHERE name = 'Laptop';
```

---

## 🧰 10. Common pgAdmin Tasks

| Task            | pgAdmin UI Path                    | Equivalent SQL          |
| --------------- | ---------------------------------- | ----------------------- |
| Create database | Right-click Databases → Create     | `CREATE DATABASE name;` |
| Create table    | Inside DB → Tables → Create        | `CREATE TABLE ...`      |
| Insert data     | Query Tool → Run SQL               | `INSERT INTO ...`       |
| View data       | Right-click table → View/Edit Data | `SELECT * FROM ...;`    |
| Backup          | Right-click database → Backup      | `pg_dump`               |
| Restore         | Right-click database → Restore     | `pg_restore`            |

---

## 🧠 11. PostgreSQL Directory Overview

| Component         | Description             |
| ----------------- | ----------------------- |
| `postgres`        | Default superuser       |
| `5432`            | Default port            |
| `data/`           | Database files          |
| `pg_hba.conf`     | Controls authentication |
| `postgresql.conf` | Main configuration file |

---

## 🧩 12. Bonus: CLI Basics (psql)

If you want to use **command-line interface**:

```bash
# Connect
psql -U postgres -d shop_db

# List databases
\l

# Connect to database
\c shop_db

# List tables
\dt

# Quit
\q
```

---

## 🧰 13. Backup & Restore

### Backup (pgAdmin or CLI)

```bash
pg_dump -U postgres -d shop_db > backup.sql
```

### Restore

```bash
psql -U postgres -d shop_db < backup.sql
```

---

Would you like me to show a **simple real example project** using PostgreSQL + pgAdmin + Python (or Laravel / Flutter backend) to make it more practical?
