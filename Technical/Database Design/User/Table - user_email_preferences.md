## Purpose of the Table

The `user_email_preferences` table stores a user's individual consents for optional email notifications. These refer exclusively to **non-critical system communication** such as product information, event announcements, or surveys. By storing this data in a fine-grained manner, all consents can be documented, managed, and revoked in compliance with data protection regulations. The table supports GDPR compliance and ensures transparency in user communication.

---

## Fields

| Field Name                        | Data Type | Required | Description                                                                     |
| --------------------------------- | --------- | -------- | ------------------------------------------------------------------------------- |
| `id`                              | UUID (PK) | Yes      | Primary key of the consent assignment                                           |
| [`user_id`](Table%20-%20users.md) | UUID (FK) | Yes      | Reference to the user to whom these settings belong                             |
| `event_updates`                   | BOOLEAN   | Yes      | Consent to notifications about in-game events, tournaments, or seasonal content |
| `product_news`                    | BOOLEAN   | Yes      | Consent to receive product information, updates, and new features               |
| `survey_invites`                  | BOOLEAN   | Yes      | Consent to participate in surveys and feedback requests                         |
| `created_at`                      | TIMESTAMP | Yes      | Timestamp of creation of the preferences                                        |
| `created_by`                      | UUID (FK) | Yes      | User who set the preferences (usually the user themselves)                      |
| `updated_at`                      | TIMESTAMP | Yes      | Timestamp of last modification                                                  |
| `updated_by`                      | UUID (FK) | Yes      | User who last modified the preferences                                          |

---

## Table Specifics

- This table is intended exclusively for **optional communication types**. System-critical messages (password reset, security warnings) are **not affected**.
    
- All BOOLEAN fields allow explicit consent or rejection per notification type.
    
- The use of `created_by` and `updated_by` enables full change tracking, e.g., in case of manual adjustments by admins.
    
- Separating consent from the user profile enhances data security and meets the GDPR principles of **data minimization and purpose limitation**.
    

---

## DDL

```
CREATE TABLE user_email_preferences (
    id UUID PRIMARY KEY,
    user_id UUID NOT NULL,
    event_updates BOOLEAN NOT NULL DEFAULT FALSE,
    product_news BOOLEAN NOT NULL DEFAULT FALSE,
    survey_invites BOOLEAN NOT NULL DEFAULT FALSE,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_email_preferences_user
        FOREIGN KEY (user_id)
        REFERENCES users(id)
        ON DELETE CASCADE,

    CONSTRAINT fk_email_preferences_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_email_preferences_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```