## Purpose of Internal Modules

Internal modules serve to process, amplify, redirect, and manipulate pulse effects within the grid. They connect cores to end modules and form the tactical backbone of the game. Their primary function is to guide pulses through the grid and strategically alter them along the way – without triggering end effects such as damage, healing, or shielding themselves.

## Technical Foundation

- **Rotatability:** All internal modules are rotatable (0° / 90° / 180° / 270°). Their internal port structure remains fixed (e.g., input at the bottom, output at the top), but can be adjusted freely through rotation.
    
- **Size Classes:**
    
    - **Small:** 2 slots, 1–2 input ports, 1–2 output ports
        
    - **Medium:** 4 slots, 2–4 input ports, 2–4 output ports
        
    - **Large:** 6 slots, 3–6 input ports, 3–6 output ports
        
- **Processing Requirement:** All input ports must be filled for the module to trigger its effect.
    
- **Processing Speed:** Each module has a fixed `processing_time`, indicating how long a pulse takes to be processed within the module. This can be influenced by other modules.
    

## Possible Actions of Internal Modules

Each internal module has **exactly one primary action** that defines its effect within the grid. The following actions are systemically allowed:

### 1. Add Effect

- The module adds a new effect to the pulse (e.g., +5 Decay).
    

### 2. Amplify Effect

- The module enhances existing effects in the pulse (e.g., +50% to existing damage).
    

### 3. Multicast

- The pulse’s effect is triggered multiple times but **displayed as a single combined effect** (e.g., 4× +5 Decay shown as +20 Decay).
    

### 4. Split Pulse

- The pulse is split into multiple sub-pulses (e.g., 1 pulse → 4 pulses at 25% effect strength each). Each sub-pulse can then be processed independently.
    

### 5. Trigger Modules

- The module only triggers its effect if a specific condition in the pulse is met (e.g., "if Decay is present").
    

### 6. Absorb Pulse (Pulse Stoppers)

- The module terminates the pulse flow. Instead, it generates a weak effect that influences other **internal modules in the grid** (e.g., accelerated processing, light buff). **No end effects allowed.** Primarily used as a tactical filler for early/midgame.
    

### 7. Combine Pulse _(systemically defined)_

- A module with multiple inputs and one output automatically merges all incoming pulses into a single pulse. The exact combination behavior (lossless, amplified, reduced) is defined per module. No explicit action required.
    

## Excluded Actions

The following concepts are intentionally excluded as they contradict the design principles:

- **Delay Pulse:** Replaced by the global `processing_time`
    
- **Redirect Pulse:** Achieved through module rotation
    
- **Duplicate Pulse (1:1):** Only allowed as a highly restricted special mechanic in legendary modules
    
- **Convert Effects:** Not allowed
    
- **Filter Pulses:** Not allowed
    
- **Direction Locks:** Not allowed
    
- **Meta Actions (e.g., counters):** Not allowed
    

## Design Principle

Internal modules are clear, predictable, and systemically transparent. All effects are visually and logically traceable. The design follows the principle: **One module, one function, clear effect.**