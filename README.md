# Circuitborn – The Synthetic Arena

A strategic 2D autobattler built on modular systems and deterministic gameplay

## Project Overview

Circuitborn is a 2D autobattler with roguelite structure, defined by complete determinism, modular grid mechanics, and deep strategic gameplay. Players place modules on a grid, guide pulses through their system, and build complex interactions and synergies. Unlike traditional roguelikes, Circuitborn eliminates randomness entirely and emphasizes clear, planable decision-making.

**Inspirations:** The Bazaar, Into the Breach, Slay the Spire  
**Engine:** Unreal Engine 5.5  
**Language:** C++  
**Status:** In development (solo project)

## Design Philosophy

- 100% deterministic: no RNG, no hidden triggers — every outcome is transparent.
    
- Modular systems: all mechanics emerge from combinations of discrete modules.
    
- Strategic depth: multiple viable builds, clear counters, emergent gameplay.
    
- Planned progression: success through clever positioning, synergy, and long-term build decisions.
    

## Core Gameplay Systems

### Grid-based Construction

- Players place modules on a logical, scalable grid.
    
- Modules have fixed size and orientation.
    

### Pulse System

- A central Core emits pulses across connected modules.
    
- Modules respond by triggering effects, redirecting, amplifying, or absorbing pulses.
    

### Module Types

- Includes processing modules, endpoints, buffs, and special units.
    
- Features upgrades, port logic, directional flow, and module rotation.
    

### Run Structure

- PvE-focused with sequential encounters.
    
- Includes shops, events, and boss fights.
    
- Players build and evolve their strategy across the run.
    

## Technical Architecture

- Engine: Unreal Engine 5.5.4
    
- Language: C++ (Blueprints optionally used for UI only)
    
- System Design: modular, component-based, data-driven
    
- Grid Logic: custom system for pulse routing, port validation, and positioning
    
- UI: built with UMG, fully controlled through C++
    
- Data: PostgreSQL and DataTables, logic separated from data
    

## AI Integration (Planned)

A central AI system is planned as the game's dynamic endgame opponent:

- Analyzes player build patterns and strategy trends
    
- Reacts to meta shifts with adaptive counter-builds
    
- Acts as a final boss with evolving systems
    
- Reads patch data and player stats to improve over time
    
- Generates procedural content: builds, encounters, even lore
    

The long-term goal is a visible, learnable AI that evolves through player interaction — but never breaks determinism.

## Developer Role

This is a solo project focused on:

- Systems design
    
- Architecture (C++, data-driven logic)
    
- UI and interaction design
    
- Full documentation and structured planning
    

Tools used: JetBrains Rider, Obsidian, GitHub, PostgreSQL

## Roadmap

- Playable prototype with grid, UI, and pulse system
    
- Modular build system with upgrades and synergy logic
    
- First encounter types and event mechanics
    
- Future integration of the AI opponent and meta-driven design loops
    

## License and Usage

This project and all related materials are protected.  
See [LICENSE](LICENSE.md) for full restrictions.