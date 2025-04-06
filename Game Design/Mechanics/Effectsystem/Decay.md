# Final Design: Decay (Effect)

## Core Mechanics:

- **Type:** Damage over Time (DoT)
    
- **Function:**
    
    - Each target affected by Decay takes damage **once per second** equal to the current number of Decay stacks.
        
    - Each stack deals **1 fixed damage**
        

## Stack Behavior:

- **Unlimited number of stacks**
    
- **10% of current stacks decay** per tick (rounded up)
    

## Visualization:

- The target's health bar visually highlights the amount of HP that will be lost due to Decay.
    
- **Example:** If a unit has 1000 HP and 200 stacks, the top 200 HP are highlighted (e.g., in violet)
    
- This highlighted section is reduced with each tick to reflect Decay damage
    

## Modularity:

- Only **specialized Decay modules** can apply Decay
    
- There are **no side effects**: Decay only deals damage – no debuff, no heal block, no synergy effects
    
- Any amplification or manipulation of Decay can only occur through **modules**, never from the effect itself