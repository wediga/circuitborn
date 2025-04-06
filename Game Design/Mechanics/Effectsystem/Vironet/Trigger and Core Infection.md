## Trigger Condition

Vironet is not a passive effect. It is actively triggered by a specific type of **Endmodule** during combat. This Endmodule is designed as a **Vironet Weapon** and is responsible for initializing the viral loop on the opponent’s side.

When this module is activated (i.e., a Pulse reaches it and it resolves its effect), it targets the **enemy Core** directly. This does not cause damage immediately but begins the Vironet process.

## Core Infection Mechanism

Once triggered, the enemy Core is considered **infected with Vironet**. From that moment on, every further activation of a Vironet Weapon adds **+1 Vironet Stack** to that Core.

- Stacks accumulate only through activation of Vironet Weapons
    
- Multiple Vironet modules can contribute to the same enemy Core
    

## Stack Threshold and Propagation

When the infected Core reaches **20 Vironet Stacks**, the following happens:

1. A **random Output Port** from the enemy Core is selected.
    
2. The **first directly connected module** (via that output port) becomes **infected**.
    
3. That module begins with **1 Vironet Stack**.
    
4. The Core’s Vironet Stack counter is **reset to 0**.
    

This begins the internal propagation system. The Core itself can be reinfected repeatedly by future Vironet Weapon activations.

## Notes

- If the selected output port is not connected to any module, no infection occurs, and stacks are still reset.
    
- Repeated infections from multiple Endmodules accelerate the initial phase.
    
- This structure ensures Vironet maintains pressure without requiring random targeting or direct Core damage up front.