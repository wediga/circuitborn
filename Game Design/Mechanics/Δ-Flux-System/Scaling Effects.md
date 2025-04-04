> This document describes the concrete effects of Δ-Flux during combat. Δ-Flux is a dynamic resource generated through complex pulse routings and continuously increases throughout the fight. It affects only the flow of combat – not the behavior or functionality of modules.

---

## 1. Scaling

Δ-Flux influences the combat flow along two continuously scaling axes:

### A. Delay per Module

- Formula: `Delay (in seconds) = 0.0005 × Δ-Flux`
    
- This delay affects **every forwarding of a pulse** through a module.
    

**Examples:**

|Δ-Flux|Delay per Module|
|---|---|
|20|0.01 seconds|
|50|0.025 seconds|
|100|0.05 seconds|
|200|0.1 seconds|

### B. Effect Amplification

- Formula: `Amplification (%) = floor(Δ-Flux / 2)`
    
- Affects **all end effects**: e.g., damage, shielding, conditions, healing
    

**Examples:**

|Δ-Flux|Effect Amplification|
|---|---|
|20|+10 %|
|50|+25 %|
|100|+50 %|
|200|+100 %|

---

## 2. Stage Indicators (Visual Thresholds)

To provide orientation during combat, threshold values are visually highlighted. These do not mark abrupt behavioral changes but serve as player feedback.

|Stage|Δ-Flux Range|Meaning|
|---|---|---|
|1|0–9|Δ-Flux is active but negligible|
|2|10–19|Minimal delay, no strategic impact|
|3|20–29|First measurable amplification effects|
|4|30–39|Low system inertia begins|
|5|40–49|**Hard Cut** – Δ-Flux becomes visible and noticeable|
|6|50–64|Strategic impact becomes relevant|
|7|65–79|Noticeable rhythm changes, builds must adapt|
|8|80–99|Intense usage requires targeted planning|
|9|100–124|Visible system overload, visual reactions recommended|
|10|125+|**Δ-Resonance Phase** – system cracks open, new layer activated|

---

## 3. Unique Effect at Stage 10 – “Δ-Resonance”

Starting from a Δ-Flux value of **125 or higher**, a global special effect takes place:

### Δ-Resonance: Echo Resolution

- **Every fifth pulse** that reaches an end module triggers **an identical copy of its effect**
    
- This copy is **activated 0.5 seconds later**
    
- The echo effect is **not stackable** and only affects the original end effect
    
- It is a **global system reaction**, not a module effect
    

---

## 4. Summary

- Δ-Flux scales continuously – no hard cap
    
- Effects are fully deterministic and predictable
    
- The system does **not** affect functionality, activity, or structure of modules
    
- It provides **strategic depth for high-skill players**, without punishing casual players
    
- From Stage 5 onward, Δ-Flux becomes noticeable; at Stage 10, the player receives a powerful reward
    

---

Δ-Flux is a global system element that reflects the tension in combat – and rewards those willing to play with instability.