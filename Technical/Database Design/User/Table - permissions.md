## Purpose of the Table

The `permissions` table defines all permissions available in the system. These permissions specifically control access to functions, actions, and content within the application. Each permission can be assigned to one or more roles via the junction table `user_role_to_permission`, allowing for a flexible and extendable rights management system.

---

## Fields

|Field Name|Data Type|Required|Description|
|---|---|---|---|
|`id`|UUID|Yes|Primary key of the permission.|
|`key`|TEXT|Yes|Technical identifier, e.g., `manage_users`, `edit_content`. Must be unique.|
|`label`|TEXT|Yes|Human-readable name, e.g., "Manage Users".|
|`description`|TEXT|No|Optional description of the permission and its function.|
|`created_at`|TIMESTAMP|Yes|Timestamp of record creation.|
|`created_by`|UUID (FK)|Yes|User who created the entry. References `users(id)`.|
|`updated_at`|TIMESTAMP|Yes|Timestamp of the last modification.|
|`updated_by`|UUID (FK)|Yes|User who last modified the entry. References `users(id)`.|

---

## Table Specifics

- The `key` serves as a unique internal identifier and should be used for programmatic checks.
    
- Separating `key` and `label` allows technical use of the key and language-dependent representation in the UI.
    
- The fields `created_by` and `updated_by` enable full traceability of all changes.
    
- The table is a central part of the permission system and is linked to roles via `user_role_to_permission`.
    

---

## DDL

```
CREATE TABLE permissions (
    id UUID PRIMARY KEY,
    key TEXT NOT NULL UNIQUE,
    label TEXT NOT NULL,
    description TEXT,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_permissions_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_permissions_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```