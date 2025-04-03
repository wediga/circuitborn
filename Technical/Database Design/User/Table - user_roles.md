## Purpose of the Table

The `user_roles` table defines the possible roles within the system to which users can be assigned. Each role represents a specific permission profile and determines which actions a user is allowed to perform. Roles also form the basis for permission management through their assignment to individual permissions.

---

## Fields

|Field Name|Data Type|Required|Description|
|---|---|---|---|
|`id`|UUID|Yes|Primary key of the role. Unique for each role in the system.|
|`role_name`|TEXT|Yes|Technical name of the role, e.g., `admin`, `player`, `moderator`. Must be unique.|
|`description`|TEXT|No|Optional free-text description of the role and its function in the system.|
|`created_at`|TIMESTAMP|Yes|Timestamp of record creation.|
|`created_by`|UUID (FK)|Yes|User who created the entry. References `users(id)`.|
|`updated_at`|TIMESTAMP|Yes|Timestamp of last modification.|
|`updated_by`|UUID (FK)|Yes|User who last modified the entry. References `users(id)`.|

---

## Table Specifics

- The `role_name` is unique within the system and is used internally to identify user roles.
    
- The fields `created_by` and `updated_by` allow full tracking of changes.
    
- This table serves as a central reference for all roles used in the `users` table.
    
- In combination with the `user_role_to_permission` table, it allows for granular permission assignment.
    

---

## DDL

```
CREATE TABLE user_roles (
    id UUID PRIMARY KEY,
    role_name TEXT NOT NULL UNIQUE,
    description TEXT,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_user_roles_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_user_roles_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```