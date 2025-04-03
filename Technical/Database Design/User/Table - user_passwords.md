## Purpose of the Table

The `user_passwords` table stores only the secured password hash of a user. The password hashing algorithm **Argon2id** is used, where the salt is automatically generated and embedded within the hash itself. Separating this from the main `users` table increases security and reduces unnecessary access to security-critical information.

---

## Fields

| Field Name                     | Data Type | Required | Description                                                             |
| ------------------------------ | --------- | -------- | ----------------------------------------------------------------------- |
| `id`                           | UUID (PK) | Yes      | Primary key of the password assignment                                  |
| [`user_id`](Table%20-%20users) | UUID (FK) | Yes      | Reference to the user this password hash belongs to                     |
| `password_hash`                | TEXT      | Yes      | Password hash generated with Argon2id, including the embedded salt      |
| `created_at`                   | TIMESTAMP | Yes      | Timestamp of hash creation                                              |
| `created_by`                   | UUID (FK) | Yes      | User who set or reset the password (e.g., admin or the user themselves) |

---

## Table Specifics

- This table contains **only security-relevant password data**.
    
- The **salt is directly embedded in the hash** (via Argon2id), so no separate salt field is required.
    
- Fields like `updated_at` or `login_attempts` are deliberately omitted to minimize access frequency to this sensitive table.
    
- Each hash is clearly assigned to a user and is traceable via `created_by`.
    
- For password changes, a new entry should be created and the old one either overwritten or archived (depending on the security concept).
    

---

## DDL

```
CREATE TABLE user_passwords (
    id UUID PRIMARY KEY,
    user_id UUID NOT NULL,
    password_hash TEXT NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,

    CONSTRAINT fk_user_passwords_user
        FOREIGN KEY (user_id)
        REFERENCES users(id)
        ON DELETE CASCADE,

    CONSTRAINT fk_user_passwords_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```