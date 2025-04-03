## Purpose of the Table

The `effect_to_trigger` table links individual effects to one or more trigger conditions. This allows an effect to be triggered contextually – e.g., only during specific game states, events, or points in time. Using a separate junction table enables fully normalized, flexible, and multidimensional assignment.

---

## Fields

| Field Name                                        | Data Type | Required | Description                                   |
| ------------------------------------------------- | --------- | -------- | --------------------------------------------- |
| `id`                                              | UUID (PK) | Yes      | Primary key of the linkage                    |
| [`effect_id`](Table%20-%20effects.md)             | UUID (FK) | Yes      | Reference to the associated effect            |
| [`trigger_id`](Table%20-%20trigger_conditions.md) | UUID (FK) | Yes      | Reference to the associated trigger condition |
| `created_at`                                      | TIMESTAMP | Yes      | Timestamp of creation                         |
| `created_by`                                      | UUID (FK) | Yes      | User who created the linkage                  |
| `updated_at`                                      | TIMESTAMP | Yes      | Timestamp of last update                      |
| `updated_by`                                      | UUID (FK) | Yes      | User who last updated the linkage             |

---

## Table Specifics

- Enables assignment of **multiple trigger conditions** per effect (e.g., "Combat start" and "SP ≥ 3").
    
- The relationship is fully decoupled, allowing triggers to be maintained and modified centrally.
    
- This structure provides a clean foundation for extendable effect logic with clear UI mapping.
    

---

## DDL

```
CREATE TABLE effect_to_trigger (
    id UUID PRIMARY KEY,
    effect_id UUID NOT NULL,
    trigger_id UUID NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_ettr_effect
        FOREIGN KEY (effect_id)
        REFERENCES effects(id)
        ON DELETE CASCADE,

    CONSTRAINT fk_ettr_trigger
        FOREIGN KEY (trigger_id)
        REFERENCES trigger_conditions(id)
        ON DELETE CASCADE,

    CONSTRAINT fk_ettr_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_ettr_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```