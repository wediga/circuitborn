## Purpose of the Table

The `users` table serves as the central entity for managing all users within the system. It stores only identity- and administration-relevant information. Security-critical data such as passwords is stored in a separate table (`user_credentials`) to ensure security and compliance with the 3rd Normal Form (3NF).

---

## Fields

| Field Name                             | Data Type | Required | Description                                                                                |
| -------------------------------------- | --------- | -------- | ------------------------------------------------------------------------------------------ |
| `id`                                   | UUID      | Yes      | Primary key for uniquely identifying a user.                                               |
| `username`                             | TEXT      | Yes      | Unique username within the system. Used for login or display.                              |
| `email`                                | TEXT      | Yes      | Unique email address of the user. Used for communication and account recovery.             |
| `email_verified`                       | BOOLEAN   | Yes      | Indicates whether the email address has been verified. Default is `FALSE`.                 |
| [`role_id`](Table%20-%20user_roles.md) | UUID      | Yes      | Foreign key to the `user_roles` table, defining the user's role and access rights.         |
| `is_active`                            | BOOLEAN   | Yes      | Indicates whether the user account is active. Default is `TRUE`.                           |
| `deactivation_reason`                  | TEXT      | No       | Optional free-text field documenting the reason for deactivation (e.g., policy violation). |
| `registration_source`                  | TEXT      | Yes      | Source of registration, e.g., `website`, `admin`, `import`, `oauth`. Useful for analytics. |
| `created_at`                           | TIMESTAMP | Yes      | Timestamp when the user account was created.                                               |
| `created_by`                           | UUID      | Yes      | Reference to the user who created this account (e.g., admin or the user themselves).       |
| `updated_at`                           | TIMESTAMP | Yes      | Timestamp of the last modification to this record.                                         |
| `updated_by`                           | UUID      | Yes      | Reference to the user who last modified the record.                                        |

---

## Specifics

- **Referential Integrity:** `role_id`, `created_by`, and `updated_by` are foreign keys linking to other records. This ensures data integrity and full traceability of changes.
    
- **Full Audit Trail:** With mandatory `created_by` and `updated_by` fields, every action is traceable to a user. Self-registrations are modeled by setting `created_by` to the user's own `id`.
    
- **Separation of Sensitive Data:** No password or login data is stored in this table. These are handled exclusively in `user_credentials`.
    
- **Extensibility:** The model allows easy addition of fields such as `avatar_url`, `display_name`, or `two_factor_enabled` without violating normalization.
    

---

## DDL

```
CREATE TABLE users (
    id UUID PRIMARY KEY,
    username TEXT NOT NULL UNIQUE,
    email TEXT NOT NULL UNIQUE,
    email_verified BOOLEAN NOT NULL DEFAULT FALSE,
    role_id UUID NOT NULL,
    is_active BOOLEAN NOT NULL DEFAULT TRUE,
    deactivation_reason TEXT,
    registration_source TEXT NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_role
        FOREIGN KEY (role_id)
        REFERENCES user_roles(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```