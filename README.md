# EcoTrack AI - Advanced Carbon Footprint Tracker

EcoTrack AI is an advanced, privacy-first progressive web application designed to help users track, analyze, and optimize their daily carbon footprint using dynamic profiling algorithms and smart habit building. 

---

##  Chosen Vertical
**Sustainability & Climate Tech (Personal Carbon Accounting)**
The application targets the personal sustainability vertical, bridging the gap between abstract climate data and daily consumer habits. It transforms complex emission factors into an actionable, gamified, and localized personal budget.

---

##  Approach and Logic

The core philosophy of EcoTrack AI is **immediacy, friction-free logging, and contextual feedback**. 

### 1. The Budgeting Engine
Instead of utilizing fixed, arbitrary emission goals, the application relies on an **AI-Calibrated Carbon Budget**. The logic determines a user's baseline by evaluating three primary high-impact vectors:
*   **Transport Metrics:** Commute distances weighted by vehicle efficiency coefficients.
*   **Dietary Configurations:** Food consumption footprint scales (e.g., high-meat vs. plant-based impacts).
*   **Strategy Aggression:** Adjusts target thresholds based on whether a user selects a *steady* or an *aggressive* reduction timeline.

### 2. Dual-State Synchronization
A major structural challenge in client-side apps is keeping decoupled UI components in sync. EcoTrack AI uses a centralized state object to ensure that whenever an activity is logged:
*   The global carbon balance updates instantly.
*   The Chart.js micro-analytics canvas destroys and re-renders to reflect the new data without page reloads.
*   The slide-in notification system captures the state delta to push immediate user feedback.

---

## Assumptions

To ensure a smooth, high-fidelity user experience within a client-side environment, the following engineering and environmental assumptions were made:
*   Static Emission Coefficients: Carbon multipliers are standardized based on average global environmental data models (e.g., average passenger vehicle emissions calculated at roughly 0.41 kg CO2e per mile).
*   24-Hour Reset Cycle: The localized state assumes a standard single-day tracking loop, where balances are evaluated against a fixed daily budget target rather than rolling cross-week deficits.
*   Local Volatile Storage: The application assumes a sandbox environment where state is held in runtime memory for demonstration purposes (can be easily wired to localStorage or an API database layer in production).
*   Offsetting: Habit optimization rewards (offsets) are assumed to have an immediate, direct subtractive relationship with that day's gross carbon emissions.

---

##  How the Solution Works

The application operates entirely on the client side as a high-performance sandbox environment.

```pascal
[User Input/Action] 
       │
       ▼
[State Core Engine] ──(Emissions Coefficients)──► [Recalculate Budget & Balances]
       │                                                      │
       ├──► [UI Reactivity: Tailwind .dark Layer]             ├──► [Update Activity Log Stream]
       └──► [Canvas Update: Re-instantiate Chart.js]         └──► [Trigger Slide-in Toast Alert]


