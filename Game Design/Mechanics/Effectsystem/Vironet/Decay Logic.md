## Purpose of Decay

Vironet should not persist indefinitely. While it is intended as a soft counter to high-frequency Pulse builds, the effect must remain relevant but fair when facing slower opponents. The decay system provides a built-in method for automatic self-regulation.

## Decay Trigger

Decay is handled **per infected module**, not globally. The Core itself never decays — only modules can be cleansed through inactivity.

Each infected module maintains a **Decay Timer**, which behaves as follows:

- When the module receives a Pulse → **Timer is reset to 0**
    
- When the module receives **no Pulse** for **X seconds** → **Timer activates**
    

## Decay Process

Once the timer activates (e.g., after 10 seconds of inactivity):

- The module begins to lose **1 Vironet Stack per second** (adjustable rate)
    
- If a Pulse arrives during this decay phase → **Timer resets**, and decay is suspended
    
- When the Vironet Stack reaches **0**, the module is considered **cleansed**
    

## Functional Summary

|Condition|Effect|
|---|---|
|Pulse received|Reset timer, add +1 stack|
|Inactive ≥ X seconds|Begin decay|
|During decay|−1 stack/sec|
|Reaches 0 stacks|Remove Vironet|

## Design Considerations

- Ensures **slow builds** are not unfairly punished
    
- Preserves Vironet’s relevance without being overly punishing
    
- Encourages continual Pulse activity to sustain spread
    

## Balancing Parameters

|Parameter|Description|
|---|---|
|`Decay Delay`|Seconds before decay begins (e.g. 10s)|
|`Decay Rate`|Stack loss per second (e.g. 1/s)|

These can be tuned per game mode, difficulty level, or even modified via supporting modules or effects.