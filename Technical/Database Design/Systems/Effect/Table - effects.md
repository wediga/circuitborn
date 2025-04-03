## Purpose of the Table

The `effects` table describes individual passive effects that can be triggered by skills, modules, or other systems. The specific nature of an effect – such as its type, trigger, or value – is entirely mapped through external link tables. This results in a highly normalized, reusable, and infinitely extensible structure.

---

## Fields

|Field Name|Data Type|Required|Description|
|---|---|---|---|
|`id`|UUID (PK)|Yes|Unique primary key|
|`name`|TEXT|Yes|Clear, short name for tooltips, logs, or internal UI|
|`description`|TEXT|Yes|Free-text description of the effect|
|`created_at`|TIMESTAMP|Yes|Time of creation|
|`created_by`|UUID (FK)|Yes|User who created the effect|
|`updated_at`|TIMESTAMP|Yes|Time of last update|
|`updated_by`|UUID (FK)|Yes|User who last updated the effect|

---

## Table Specifics

- The concrete contents of the effect (e.g., type, value, trigger condition) are **not stored in this table**.
    
- Instead, the full breakdown is managed via:
    
    - `effect_to_type` → Type of the effect (e.g., Buff, Debuff, Utility)
        
    - `effect_values` → Concrete numerical values, texts, or modifiers
        
    - `effect_to_trigger` → Timing or condition of the effect (e.g., “Combat start”, “SP ≥ 3”)
        
- The effect is thus **a logical wrapper** that functions contextually based on the linked data.
    

---

## DDL

```
CREATE TABLE effects (
    id UUID PRIMARY KEY,
    name TEXT NOT NULL,
    description TEXT NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_effects_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_effects_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```