## Module Infection

Once a module has been infected through a Core-based Vironet propagation, it starts tracking its own **Vironet Stack Counter**. Each infected module operates independently from the Core and other modules.

- Initial Stack on infection: **1**
    
- Stack increases by **+1** for every Pulse processed by the module
    

Each module’s Vironet stack is **persistent** and does not reset after propagation. This creates local pressure zones within the enemy grid.

## Propagation Threshold

When a module’s Vironet Stack reaches the value of **10**, the Vironet effect spreads:

1. A **random connected port** (Input or Output) is chosen.
    
2. The **connected module** on the other side of that port becomes **infected**.
    
3. The new module begins with **1 Vironet Stack**.
    
4. The original module **keeps its current stack count** (it does not reset).
    

If the selected neighbor is already infected, it simply gains **+1 Stack**.

## Unbounded Spread

There is **no hard limit** to the number of infected modules. Vironet can, in theory, spread to the entire enemy grid. However, propagation requires:

- Stack accumulation via active Pulse processing
    
- Connection via physical ports
    

## Re-Infection and Stack Behavior

- Modules can be infected **multiple times**.
    
- Each infection adds **+1 Vironet Stack**.
    
- There is no maximum stack cap at this stage.
    

## Network Sensitivity

Because propagation is tied to the physical topology of the module grid, players with densely connected networks are more susceptible to rapid Vironet escalation.

This mechanic rewards clean, well-controlled Pulse paths and punishes overly recursive or tangled architectures.