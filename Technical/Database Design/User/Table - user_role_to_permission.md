## Purpose of the Table

The `user_role_to_permission` table represents an n:m relationship between user roles and permissions. It allows assigning multiple permissions to a role and reusing individual permissions across different roles. This enables a flexible and fine-grained permission management system.

---

## Fields

| Field Name                                   | Data Type | Required | Description                                             |
| -------------------------------------------- | --------- | -------- | ------------------------------------------------------- |
| `id`                                         | UUID (PK) | Yes      | Primary key of the assignment                           |
| [`role_id`](Table%20-%20user_roles.md)       | UUID (FK) | Yes      | Reference to the role in `user_roles(id)`               |
| [`permission_id`](Table%20-%20user_roles.md) | UUID (FK) | Yes      | Reference to the permission in `permissions(id)`        |
| `created_at`                                 | TIMESTAMP | Yes      | Timestamp of the assignment creation                    |
| `created_by`                                 | UUID (FK) | Yes      | User who created the assignment. References `users(id)` |

---

## Table Specifics

- The `id` primary key allows each assignment to be uniquely referenced, which is especially useful for downstream systems or logging.
    
- The combination of `role_id` and `permission_id` should be enforced with a UNIQUE constraint to avoid duplicates.
    
- The table conforms to the 3rd normal form, completely separating roles and permissions.
    
- `created_by` allows complete traceability of permission assignments.
    

---

## DDL

```
CREATE TABLE user_role_to_permission (
    id UUID PRIMARY KEY,
    role_id UUID NOT NULL,
    permission_id UUID NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,

    CONSTRAINT uq_role_permission UNIQUE (role_id, permission_id),

    CONSTRAINT fk_urtp_role
        FOREIGN KEY (role_id)
        REFERENCES user_roles(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_urtp_permission
        FOREIGN KEY (permission_id)
        REFERENCES permissions(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_urtp_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```