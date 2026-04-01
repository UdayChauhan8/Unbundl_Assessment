# Unbundl Assessment — PHP User Management App

**Submitted by:** Uday Chauhan  
**Live Demo:** [https://udaytest.page.gd/unbundl_assessment/](https://udaytest.page.gd/unbundl_assessment/)

---

## Overview

A lightweight, full-stack **User Data Management** web application built with PHP and MySQL. It allows users to submit their personal details through a validated form, view all submitted records in a tabular layout, and edit existing entries — all backed by a relational database.

---

## Features

- **User Submission Form** — Collects Name, Email, Phone Number, and Address with both client-side HTML5 and server-side PHP validation.
- **Inline Error Feedback** — On validation failure, the form repopulates the user's input and shows field-level error messages without losing data.
- **Duplicate Prevention** — Detects and rejects duplicate records based on matching name + phone combinations, and unique email constraint enforced at the database level.
- **Records Table** — Displays all submitted users in a clean, sortable HTML table with Edit actions per row.
- **Edit User** — Pre-populates an edit form with the selected user's current data; validates changes with the same rules as the submission form before saving.
- **Prepared Statements** — All database queries use MySQLi prepared statements to prevent SQL injection.

---

## Tech Stack

| Layer      | Technology        |
|------------|-------------------|
| Backend    | PHP (native)      |
| Database   | MySQL             |
| Frontend   | HTML5, CSS3       |
| Hosting    | Shared Web Host   |

---

## Application Pages

| File         | Route / Purpose                                      |
|--------------|------------------------------------------------------|
| `index.php`  | Home — User submission form with validation          |
| `submit.php` | Handles POST from the form; validates & inserts data |
| `view.php`   | Displays all user records in an HTML table           |
| `edit.php`   | Pre-fills form with a user's existing data           |
| `update.php` | Handles POST from edit form; validates & updates row |
| `db.php`     | Database connection configuration                    |
| `schema.sql` | MySQL DDL — creates `unbundl_db` and `users` table  |

---

## Database Schema

```sql
CREATE DATABASE IF NOT EXISTS unbundl_db;
USE unbundl_db;

CREATE TABLE IF NOT EXISTS users (
    id      INT AUTO_INCREMENT PRIMARY KEY,
    name    VARCHAR(100) NOT NULL,
    email   VARCHAR(100) NOT NULL UNIQUE,
    phone   VARCHAR(15)  NOT NULL,
    address TEXT         NOT NULL
);
```

---

## Validation Rules

| Field   | Rules                                                        |
|---------|--------------------------------------------------------------|
| Name    | Required · Letters and spaces only · Minimum 2 characters   |
| Email   | Required · Must be a valid email format · Must be unique     |
| Phone   | Required · Exactly 10 digits                                 |
| Address | Required · Non-empty                                         |

---

*Submitted as part of the Unbundl technical assessment.*
