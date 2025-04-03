## Purpose of the Table

The `user_settings` table stores user-specific settings related to gameplay behavior or the user interface. It contains only non-security-relevant information, such as language preferences and tutorial completion status. These settings are technically and legally non-critical and contribute to the personalization of the gameplay experience.

---

## Fields

| Field Name                        | Data Type | Required | Description                                           |
| --------------------------------- | --------- | -------- | ----------------------------------------------------- |
| `id`                              | UUID (PK) | Yes      | Primary key of the user settings                      |
| [`user_id`](Table%20-%20users.md) | UUID (FK) | Yes      | Reference to the user to whom these settings belong   |
| `language`                        | TEXT      | Yes      | Language of the user interface, e.g., `en`, `de`      |
| `notifications`                   | BOOLEAN   | Yes      | General in-app notifications (pop-ups, alerts, hints) |
| `tutorial_completed`              | BOOLEAN   | Yes      | Indicates whether the tutorial has been completed     |
| `created_at`                      | TIMESTAMP | Yes      | Timestamp of record creation                          |
| `created_by`                      | UUID (FK) | Yes      | User who created the entry                            |
| `updated_at`                      | TIMESTAMP | Yes      | Timestamp of the last modification                    |
| `updated_by`                      | UUID (FK) | Yes      | User who last modified the entry                      |

---

## Table Specifics

- It is assumed that exactly one entry per user exists in this table.
    
- The `language` setting can be used for translations, notifications, and localization.
    
- `tutorial_completed` allows enabling or disabling in-game help based on user progress.
    
- Additional gameplay-related preferences can be added as needed.
    
- All changes are fully traceable via `created_by` and `updated_by`.
    

---

## DDL

```
CREATE TABLE user_settings (
    id UUID PRIMARY KEY,
    user_id UUID NOT NULL,
    language TEXT NOT NULL,
    notifications BOOLEAN NOT NULL DEFAULT TRUE,
    tutorial_completed BOOLEAN NOT NULL DEFAULT FALSE,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_user_settings_user
        FOREIGN KEY (user_id)
        REFERENCES users(id)
        ON DELETE CASCADE,

    CONSTRAINT fk_user_settings_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_user_settings_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```