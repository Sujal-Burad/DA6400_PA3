# DA6400_PA3

# Taxi-v3 Environment SMDP & IOQL Implementation

**Last Updated:** May 03, 2025  
**Environment:** OpenAI Gym `Taxi-v3`

##  Environment Overview
Grid-based taxi navigation task where an agent must:
- Pick up passengers
- Drop them at target locations
- Avoid illegal pick-up/drop-off actions

##  Actions & Options

### Basic Actions (6 Discrete Deterministic Actions)
| Code | Action          |
|------|-----------------|
| 0    | Move South      |
| 1    | Move North      |
| 2    | Move East       |
| 3    | Move West       |
| 4    | Pick Passenger  |
| 5    | Drop Passenger  |

### Navigation Options (Primitive Options)
**Trigger Condition:** Taxi NOT already at target location
- `Option R`: Navigate to Red location
- `Option G`: Navigate to Green location
- `Option Y`: Navigate to Yellow location
- `Option B`: Navigate to Blue location

### Task-Based Options (Hierarchical Options)
1. **Pickup Option**
   - Activated when passenger needs to be picked up
   - Follows deterministic policy until successful pickup

2. **Dropoff Option**
   - Activated when passenger needs to be dropped
   - Follows deterministic policy until successful delivery

##  Methods & Implementation

### Learning Approaches
- **SMDP (Semi-Markov Decision Process)**
- **IOQL (Intra-Option Q-Learning)**

### Action Selection Strategy
- ε-greedy exploration during option selection - Takes actions in a state to reach R, G, B, Y location using epsilon-greedy policy
- Deterministic policy execution within options - Predefined actions to take in a state to reach the one of the R, G, B, Y location.

### Key Implementation Features
1. **Option Interruption:** Automatic termination when reaching target location
2. **Hierarchical Execution:** 
   - High-level option selection
   - Low-level action execution
3. **Reward Shaping:** Native environment rewards maintained

### Notebooks Overview
1. `geography_based_options.ipynb` : Implements the options as described in the problem statement, utilizing an epsilon-greedy policy selection. (To use the deterministic policies, code similar to the Option function in task_based_option_(task3)_bonus.ipynb can be written in the Option function)
2. `task_based_option_(task3)_bonus.ipynb` : Contains the 'pickup' and 'drop-off' options with deterministic policies, implemented for both SMDP and IOQL frameworks.

### Contribution
1. **Sujal (EE21B144)**: Implemented IOQL and SMDP for both sets of options.
2. **Shivam (EE21B124)**: Responsible for report preparation and documentation.
