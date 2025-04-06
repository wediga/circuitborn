## Core Principle

Δ-Flux is generated automatically during combat based on the structure and complexity of pulse routing. Each pulse generates its own Δ-Flux value, which is only added to the global Δ-Flux counter when the pulse reaches an end module.

The system is entirely passive – players **cannot directly create or influence Δ-Flux**, but can manipulate it through their grid design.

---

## Calculation Process per Pulse

Each pulse internally tracks two values:

- **Base Δ-Flux**: Accumulates as the pulse passes through modules
    
- **Travel Time (`travel_time`)**: Time in seconds from core to end module
    

Upon reaching the end module, the final Δ-Flux value is calculated as:

```plaintext
Δ = Σ (ModuleValue) × (1 + travel_time × 0.25)
```

### Explanation:

- `Σ (ModuleValue)`: Sum of Δ-base values from all passed modules
    
- `travel_time`: Total time (in seconds) the pulse has been traveling
    
- `0.25`: Amplification factor for longer travel times _(tweakable)_
    

Only **at the end module** is this value added to the global Δ-Flux.

---

## Δ-Flux Base Values by Module Size

|Module Size|Δ-Flux Base Value per Pass|
|---|---|
|Small|`0.2`|
|Medium|`0.4`|
|Large|`0.8`|

All modules – regardless of type – generate these values. No distinction is made between intermediate and end modules.

---

## Handling of Splits and Merges

### Splits:

- A pulse is duplicated
    
- **Base value and travel time are copied**
    
- From the split onward, each pulse is calculated separately
    

### Merges:

- Two pulses are combined into one
    
- **Base values are summed**
    
- **Travel times are also summed**
    
- The resulting pulse continues calculation with the combined values
    

---

## Example Calculation

A pulse passes through:

- 1 Small module → `+0.2`
    
- 2 Medium modules → `+0.8`
    
- 1 Large module → `+0.8`
    
- Travel time: 1.5 seconds
    

→ `Base = 1.8`

→ `Final Δ = 1.8 × (1 + 1.5 × 0.25) = 1.8 × 1.375 = 2.475 Δ-Flux`

---

## Balancing Goal

- A typical build with realistic routes and 1 pulse/sec should reach **up to Stage 12 (~120 Δ-Flux)**
    
- Builds using loops, splits, and complex paths can exceed this significantly
    
- This creates a **natural risk/reward dynamic** without artificial caps or external triggers
    

---

This system is fully deterministic, traceable, and allows players to design, optimize, or intentionally overload their builds – with meaningful RNG effects unlocking from Stage 11 onward.