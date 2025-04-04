## Purpose of End Modules

End modules form the final point of a pulse flow within the grid. They are the only modules allowed to **trigger end effects**, such as **damage, healing, shielding, glitch, feedback, or decay**. They are the objective of all build strategies and convert the prepared pulse into an immediate, tangible outcome. End modules are not rotatable and follow a clearly defined connection principle.

## Technical Foundation

- **Fixed Orientation:** End modules are **not rotatable**. Their input ports are located **exclusively at the bottom**.
    
- **No Outputs:** End modules have **only input ports**.
    
- **Size Classes:**
    
    - **Small:** 2 slots, 1–2 input ports
        
    - **Medium:** 4 slots, 2–4 input ports
        
    - **Large:** 6 slots, 3–6 input ports
        
- **Processing Requirement:** All input ports must be filled for the module to trigger its effect.
    
- **Processing Speed:** End modules also have a defined `processing_time`, indicating how long the pulse takes to be processed. This time can be influenced by other modules.
    

## Allowed Properties and Actions

An end module can **trigger one or more end effects simultaneously**. The following properties are permitted:

- **Multi-effect Capability:** End modules may trigger multiple effects simultaneously (e.g., damage + decay).
    
- **Enhanced Effectiveness with More Inputs:** Effect strength scales with the number and quality of incoming pulses.
    
- **Clearly Defined Target Effect:** Each triggered effect must be clearly visible and understandable in the game.
    

## Permitted End Effects

End modules may trigger the following effect types (depending on module design):

- **Damage**
    
- **Healing**
    
- **Shield**
    
- **Glitch**
    
- **Feedback**
    
- **Decay**
    

Effects may be combined, scaled, or specialized based on module design. AoE effects are not permitted, as there is only one target.

## Excluded Properties

The following concepts are excluded from end modules:

- **Rotatability:** End modules are fixed in orientation
    
- **Outputs:** End modules have no outputs
    
- **Meta Effects:** End modules do not influence other modules in the grid
    
- **System Effects:** No influence on Circbytes, analysis points, or external resources
    
- **Random Effects (RNG):** Not allowed. All outcomes are deterministic.
    

## Design Principle

End modules represent the **goalposts of every build path**. They define the player's success in a run and are central to the effectiveness of deck and grid building. Their impact is visible, powerful, and unambiguous. Their function: **Receive pulses, trigger effects, secure victory.**