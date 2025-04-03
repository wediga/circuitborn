## Purpose of the Table

The `effect_types` table defines globally valid categories of effects. Each effect can be assigned to one or more of these types. These types serve for logical classification, UI display, filtering, as well as for balancing and combination mechanics. Separating them into a dedicated table allows easy expansion and consistent reuse across multiple game systems.

---

## Fields

|Field Name|Data Type|Required|Description|
|---|---|---|---|
|`id`|UUID (PK)|Yes|Primary key of the effect type|
|`label`|TEXT|Yes|Machine- and human-readable name, e.g., "Buff", "Debuff"|
|`description`|TEXT|No|Optional description of the type category|
|`created_at`|TIMESTAMP|Yes|Timestamp of creation|
|`created_by`|UUID (FK)|Yes|User who created the type|
|`updated_at`|TIMESTAMP|Yes|Timestamp of last update|
|`updated_by`|UUID (FK)|Yes|User who last updated the type|

---

## Table Specifics

- Typing allows system-wide semantic classification and can also be visually represented differently in the UI.
    
- The link between effects and types is established via the junction table `effect_to_type`, since an effect can have multiple types.
    
- Decoupling from the effect itself enables new categories to be introduced without data migration.
    

---

## DDL

```
CREATE TABLE effect_types (
    id UUID PRIMARY KEY,
    label TEXT NOT NULL,
    description TEXT,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_effect_types_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_effect_types_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```