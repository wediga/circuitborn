## Purpose of the Table

The `trigger_conditions` table defines all system-wide triggers under which effects can become active. Trigger conditions describe either temporal, rule-based, or state-dependent events, such as "Combat start" or "When SP ≥ 3". Separating effects from their triggers allows for maximum reusability, easier balancing, and clear UI representation.

---

## Fields

|Field Name|Data Type|Required|Description|
|---|---|---|---|
|`id`|UUID (PK)|Yes|Unique primary key|
|`label`|TEXT|Yes|Machine- and human-readable name (e.g., "Combat start")|
|`description`|TEXT|No|More detailed description for tooltips or internal understanding|
|`created_at`|TIMESTAMP|Yes|Timestamp of creation|
|`created_by`|UUID (FK)|Yes|User who created the trigger condition|
|`updated_at`|TIMESTAMP|Yes|Timestamp of last update|
|`updated_by`|UUID (FK)|Yes|User who last updated the trigger condition|

---

## Table Specifics

- An effect can be linked to one or more trigger conditions via the `effect_to_trigger` table.
    
- Outsourcing the trigger conditions provides a clear separation between effect logic and triggering criteria.
    
- The structure supports both simple ("on combat start") and more complex conditions ("when SP ≥ 3 and shield < 50%"), as long as they are clearly described.
    

---

## DDL

```
CREATE TABLE trigger_conditions (
    id UUID PRIMARY KEY,
    label TEXT NOT NULL,
    description TEXT,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_trigger_conditions_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_trigger_conditions_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```