## Purpose

This document outlines and defines all Encounter types used within the Run structure of _Circuitborn – The Synthetic Arena_. Each Encounter type appears in predetermined positions across the Sectors to ensure fairness and determinism across all players.

---

## Overview of Encounter Types

|Encounter Type|Description|
|---|---|
|Shop Selection|Player chooses one of three random Shops at the start of each Sector|
|PvE Encounter|Player chooses one of three enemies (Easy / Medium / Hard) with scaling rewards|
|Shop Encounter|Player chooses one of: a Shop, a Minor Event, or an Instant Bonus|
|Event Encounter|A special non-combat scenario with narrative or mechanical consequences (TBD)|
|PvP Encounter|Asynchronous combat against another player's build (always in Node 10)|

---

## Detailed Definitions

### Shop Selection (Node 1)

- Triggered at the first Node of every Sector.
    
- The player is offered three Shops with different module inventories and price structures.
    
- The player chooses one Shop to access; the other two are discarded.
    
- No combat occurs in this Encounter.
    

### PvE Encounter

- Occurs in Node 2 of every Sector and three times among Nodes 3–9.
    
- Player chooses between three enemies:
    
    - **Easy**: Low difficulty, low reward
        
    - **Medium**: Moderate difficulty, moderate reward
        
    - **Hard**: High difficulty, high reward
        
- Enemies are built from the same module pool available to players (with some exclusive loot exceptions).
    

### Shop Encounter

- Occurs three times between Nodes 3–9 per Sector.
    
- Each Shop Encounter presents three options:
    
    - **Shop**: Standard module market
        
    - **Minor Event**: A short interaction with a risk/reward element (details TBD)
        
    - **Instant Bonus**: One-time benefit such as Circbytes, free module, or temporary boost
        
- Player selects one and proceeds immediately afterward.
    

### Event Encounter

- Occurs once between Nodes 3–9 per Sector.
    
- Purely systemic or narrative event.
    
- Can affect resources, offer lore insight, apply minor twists to the Run.
    
- Not yet fully defined – placeholder category for future expansion.
    

### PvP Encounter (Node 10)

- Always occurs at Node 10 of each Sector.
    
- The player faces an asynchronous PvP battle against a recorded build of another player.
    
- PvP outcomes influence the Aetherfract System but do not directly alter gameplay options.
    

---

## Notes

- All Encounter types are deterministic in frequency, but random in content.
    
- Players never encounter more or fewer Encounters of a type than defined per Sector.
    
- The precise implementation of Minor Events and narrative Events is still under development.