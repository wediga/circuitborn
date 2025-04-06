## Core Principle

Δ-Flux is a scaling combat resource that is generated automatically as pulses traverse complex module routes. It cannot be directly influenced by the player and is determined entirely by their build. Δ-Flux only affects the flow of combat and can scale infinitely. As Δ-Flux increases, the system slows down naturally, creating an emergent self-limiting effect.

---

## Permanent Base Effects

These effects are active from Δ = 1 and scale continuously with each point of Δ-Flux:

- **Processing delay per module:** `+0.0005 seconds × Δ-Flux`
    
- **End-effect amplification:** `+0.5 % × Δ-Flux`
    

These base effects are always active and apply independently of stage effects.

---

## Stage Effects

Δ-Flux is divided into 20 stages. Each stage covers a range of 10 Δ-Flux points. When a new stage is reached, its effect is permanently activated. All previous stage effects remain active. Two distinct phases are defined:

- **Phase I (Stages 1–10):** Fully deterministic, predictable, and consistent
    
- **Phase II (Stages 11–20):** Randomized but always positive effects
    

---

## Phase I – Stable Zone (Stages 1–10, Δ = 0–99)

|Stage|Δ-Range|Effect|
|---|---|---|
|1|0–9|No effect|
|2|10–19|End effects gain +5% power|
|3|20–29|DoT effects (e.g. Decay, Glitch) tick 1 extra time|
|4|30–39|Shields block +10% more damage before breaking|
|5|40–49|Damage +10% if the pulse passed through ≥3 modules|
|6|50–59|Healing may temporarily overheal beyond max (bonus buffer)|
|7|60–69|Every 5th DoT starts with +1 additional stack|
|8|70–79|End modules with upgrade level 2+ gain +10% effectiveness|
|9|80–89|Pulses that passed ≥5 modules create a secondary effect (25% strength)|
|10|90–99|Every 7th pulse that reaches an end module creates an echo (50% strength, delayed by 0.5s)|

---

## Phase II – Torsion Zone (Stages 11–20, Δ = 100–199)

_All effects are RNG-based, but always beneficial to the player._

|Stage|Δ-Range|Effect|
|---|---|---|
|11|100–109|Every 8th pulse has 33% chance to duplicate its effect (50% strength)|
|12|110–119|DoTs have 20% chance to apply with double initial stacks|
|13|120–129|Healing has 25% chance to also apply a shield worth 50% of the heal amount|
|14|130–139|End effects have 10% chance to trigger again after 1s (25% strength)|
|15|140–149|Pulses with ≥5 modules have 20% chance to trigger an extra end effect (25% strength)|
|16|150–159|Every second pulse may apply a random DoT effect (1 stack, if valid)|
|17|160–169|Damage that exceeds shield has 15% chance to apply a Feedback stack|
|18|170–179|Every 6th pulse has 50% chance to fully double its damage|
|19|180–189|End effects have 15% chance to delay the target by 1s (next pulse is paused)|
|20|190–199|Every 4th pulse spawns a second pulse after 2s (same effect, 50% strength)|