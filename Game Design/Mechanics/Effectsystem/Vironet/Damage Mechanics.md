## Damage Source

Vironet does not deal damage directly when a Core or module is infected. Instead, the damage is dealt **only when a Pulse is processed through an infected module**.

Each time a Pulse enters and is processed by a Vironet-infected module:

- The enemy Core (owner of the infected module) receives **direct damage**.
    
- The infected module’s **Vironet Stack** increases by **+1**.
    

## Damage Calculation

Damage scaling is determined by game balance decisions, but the following structure applies:

- **Flat Damage**: e.g., 1 damage per Pulse processed
    
- **Stack-Scaled Damage (optional)**: e.g., damage = base × current stack level
    
- **Hybrid Model**: base damage + 0.1× stack
    

Only one of these should be chosen during balance tuning. The damage model should remain consistent for player readability.

## Damage Limitation by Design

- Vironet damage does not multiply per stack unless explicitly balanced to do so.
    
- It is bound to Pulse frequency, which is the core balancing lever.
    

This ensures that:

- Fast Pulse builds suffer rapid, high-frequency damage
    
- Slow builds suffer low-frequency, drawn-out damage
    

## Summary

Vironet is a **passive but escalating damage source** that punishes Pulse volume, not raw power. It ensures system-level fragility for high-traffic builds without introducing random damage spikes.