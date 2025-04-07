## Purpose

This document defines the overall structure of a Run in _Circuitborn – The Synthetic Arena_. It serves as a high-level gameplay flow overview without detailing individual encounter types or escalation mechanics.

---

## Core Loop Structure

Each Run consists of **10 Sectors**. Every Sector contains exactly **10 Nodes**. These Nodes represent individual decision or combat points within the Run.

The player retains full control over their Grid at all times, except during combat encounters.

---

## Sector Flow

### Node 1 — Shop Selection

- The player chooses **one out of three randomly offered Shops**.
    
- Each Shop has different inventory and pricing, but the encounter is fixed in position.
    

### Node 2 — PvE Encounter

- The player selects **one of three PvE enemies**, each with increasing difficulty and better rewards (Easy / Medium / Hard).
    
- This choice occurs at every PvE node, including Node 2.
    

### Nodes 3–9 — Encounter Mix

- These seven nodes contain a **fixed mix of Encounter types**:
    
    - **3x PvE Encounter** (with enemy choice as above)
        
    - **3x Shop Encounter** (choose one: Shop, Minor Event, Instant Bonus)
        
    - **1x Event Encounter** (narrative or systemic effect, TBD)
        
- The order of these nodes is randomized, but their quantity is fixed and deterministic for every player.
    

### Node 10 — Asynchronous PvP

- The player fights a PvP opponent selected from a pool of similarly progressed players.
    
- The fight is asynchronous; builds are pre-recorded.
    

---

## Run Flow Summary

1. **Run Start**: Player selects a Core (possibly with configuration)
    
2. **Sector 1, Node 1**: Choose one of three Shops
    
3. **Sector 1, Node 2**: Choose PvE opponent (Easy / Medium / Hard)
    
4. **Sector 1, Nodes 3–9**: Deterministic mix of PvE, Shop, and Event Encounters
    
5. **Sector 1, Node 10**: Asynchronous PvP fight
    
6. **Repeat** Sectors 2–10 with same structure
    
7. **After Sector 10**: Final Boss fight against the adaptive KI (if Run not terminated via Aetherfract)
    

---

## Grid Building Rules

- The player can build, rearrange, and optimize their Grid **before and after every Node**, except during combat.
    
- Shops and other systems are accessed through the build interface.
    
- Pulse generation begins **only when a combat encounter starts**, never during planning.
    

---

## Related Systems (see other documents)

- **Encounter Types** → `Encounter Types.md`
    
- **Aetherfract System** → `Aetherfract System.md`