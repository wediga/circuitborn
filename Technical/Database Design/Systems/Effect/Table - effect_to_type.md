## Purpose of the Table

The `effect_to_type` table defines a link between an effect and one or more effect types. This relationship allows an effect to be categorized by functional aspects such as Buff, Debuff, Synergy, or Utility. By placing this in a separate table, multiple type assignments per effect become possible while maintaining full normalization.

---

## Fields

| Field Name                               | Data Type | Required | Description                           |
| ---------------------------------------- | --------- | -------- | ------------------------------------- |
| `id`                                     | UUID (PK) | Yes      | Primary key of the linkage            |
| [`effect_id`](Table%20-%20effects.md)    | UUID (FK) | Yes      | Reference to the linked effect        |
| [`type_id`](Table%20-%20effect_types.md) | UUID (FK) | Yes      | Reference to the assigned effect type |
| `created_at`                             | TIMESTAMP | Yes      | Timestamp of creation                 |
| `created_by`                             | UUID (FK) | Yes      | User who created the linkage          |
| `updated_at`                             | TIMESTAMP | Yes      | Timestamp of last update              |
| `updated_by`                             | UUID (FK) | Yes      | User who last updated the linkage     |

---

## Table Specifics

- The separation between effect and types allows for **multidimensional classification**.
    
- An effect can thus simultaneously be considered, for example, a **Buff and Synergy**.
    
- The structure remains fully extendable and logically clean through the junction table.
    

---

## DDL

```
CREATE TABLE effect_to_type (
    id UUID PRIMARY KEY,
    effect_id UUID NOT NULL,
    type_id UUID NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by UUID NOT NULL,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_by UUID NOT NULL,

    CONSTRAINT fk_eff_to_type_effect
        FOREIGN KEY (effect_id)
        REFERENCES effects(id)
        ON DELETE CASCADE,

    CONSTRAINT fk_eff_to_type_type
        FOREIGN KEY (type_id)
        REFERENCES effect_types(id)
        ON DELETE CASCADE,

    CONSTRAINT fk_eff_to_type_created_by
        FOREIGN KEY (created_by)
        REFERENCES users(id)
        ON DELETE RESTRICT,

    CONSTRAINT fk_eff_to_type_updated_by
        FOREIGN KEY (updated_by)
        REFERENCES users(id)
        ON DELETE RESTRICT
);
```