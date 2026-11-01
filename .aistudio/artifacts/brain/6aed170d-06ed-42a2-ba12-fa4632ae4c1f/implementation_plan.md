# Strict Alignment with John Hull Chapter 14: Monte Carlo Formula & Path Simulation

Align the mathematical formulas, text callouts, and simulation descriptions across the standalone A3 poster (`poster.html`, `public/poster.html`) and the web application (`index.html`) strictly with John Hull Chapter 14 (*Wiener Processes and Itô's Lemma*) and the lecturer's slides (Pages 27–32). Specifically, replace the European call option pricing formula ($\hat{C} = e^{-rT} \frac{1}{N} \sum \max(S_T - K, 0)$)—which belongs to Black-Scholes / Chapter 21—with John Hull Chapter 14's authentic discrete stepping equations ($\Delta S = \mu S \Delta t + \sigma S \epsilon \sqrt{\Delta t}$ and Table 14.1's weekly stepper $\Delta S = 0.00288 S + 0.0416 S \epsilon$).

---

## User Review & Critical Decisions

> [!IMPORTANT]
> **Summary of Textbook & Slide Grounding (John Hull Chapter 14 vs. Chapter 21)**
> In John Hull Chapter 14 and the lecturer's lecture slides (Slides 27–32), Monte Carlo is introduced purely as **discrete-time path simulation for stock prices**, defined by:
> 1. **Equation 14.8 & Slide 27, 30**: $\Delta S = \mu S \Delta t + \sigma S \epsilon \sqrt{\Delta t}$
> 2. **Equation 14.10, Slide 30, and Table 14.1**: $\Delta S = 0.00288 S + 0.0416 S \epsilon \quad (\text{where } \mu=0.15, \sigma=0.30, \Delta t=1/52)$
> 3. **Equation 14.19 & Slide 42**: Lognormal terminal distribution $\ln S_T \sim \phi\left(\ln S_0 + (\mu - \frac{1}{2}\sigma^2)T, \sigma^2 T\right)$
> 
> The European call option pricing formula ($\hat{C} = e^{-rT} \frac{1}{N} \sum \max(S_T - K, 0)$) belongs to Chapter 21 (Option Valuation by Simulation) and never appears in Chapter 14 or Dr's Wiener process slides. It will be replaced with Hull's authentic discrete stepping formula and Table 14.1 path sampling.

- **Confirmed Decision 1**: In the A3 Poster (`poster.html` and `public/poster.html`), replace the Monte Carlo column equation $\hat{C} = e^{-rT}\frac{1}{N}\sum \max(S_T-K, 0)$ with $\Delta S = \mu S \Delta t + \sigma S \epsilon \sqrt{\Delta t}$ and Table 14.1 weekly parameters ($\Delta S = 0.00288 S + 0.0416 S \epsilon$).
- **Confirmed Decision 2**: In the A3 Poster Showcase 3, update text descriptions from "option pricing" to discrete path simulation and lognormal distribution verification.
- **Confirmed Decision 3**: In `index.html`, verify that all 4 stations remain 100% faithful to Hull Chapter 14: Station 4 already implements John Hull Table 14.1 weekly stepping and multi-path lognormal fan; update Flip Card 4 back copy to remove option pricing references and emphasize Hull's discrete stepping and probability distribution.

---

## 1. Overview & Core Concept

- **What It Does**: Synchronizes mathematical content across the web application and exhibition poster so that every formula, variable definition, and interactive simulation strictly reflects the syllabus of John Hull Chapter 14 (*Wiener Processes and Itô's Lemma*) and the lecturer's slides.
- **Target Audience / Persona**: Kulliyyah of Science (IIUM) Mathematical Sciences students and exhibition judges evaluating academic fidelity against Chapter 14.
- **Key Value**: Guarantees zero exam confusion or syllabus mismatch by eliminating out-of-scope option pricing formulas and reinforcing Hull's discrete Euler stepping ($\Delta S = \mu S \Delta t + \sigma S \epsilon \sqrt{\Delta t}$) and Table 14.1 numerical mechanics.

---

## 2. User Experience & Visual Design

### Key Modifications in the Poster (`poster.html` & `public/poster.html`)
1. **Row 3 (Maths & Novelty - Block 4, Equation 3)**:
   - **Old**:
     $$\hat{C} = e^{-rT} \frac{1}{N} \sum \max(S_T - K, 0)$$
     *"Runs our live 252-day multi-path canvas engine... to price European call options in real time."*
   - **New**:
     $$\Delta S = \mu S \Delta t + \sigma S \epsilon \sqrt{\Delta t}$$
     $$(\text{Hull 14.10: } \Delta S = 0.00288 S + 0.0416 S \epsilon)$$
     *"Discretizes continuous GBM across discrete intervals ($\Delta t = 1/52$ weekly or $1/252$ daily). Samples random standard normal draws $\epsilon \sim \mathcal{N}(0, 1)$ to model John Hull Table 14.1 stock price trajectories."*
2. **Row 2 (Real App Interface Showcases - Showcase 3)**:
   - Header badge: `John Hull Table 14.1 ($S_0=\$100$)`
   - Legend badges: `Discrete Steps ΔS` • `Dashed Drift S₀e^(μt)` • `Lognormal Fan`
   - Description: *"Simulates discrete multi-path market trajectories across a 1-year horizon starting at $S_0 = \$100$, demonstrating how weekly discrete increments ($\Delta t = 1/52$) fan out to verify the continuous lognormal distribution."*

### Key Modifications in the Web App (`index.html`)
1. **Intro Station Flip Card 4 (Back)**:
   - Update text: *"Nobody can predict a single path. By simulating multiple paths using John Hull's discrete steps $\Delta S = \mu S \Delta t + \sigma S \epsilon \sqrt{\Delta t}$, we reveal the full lognormal probability distribution of future asset prices."*
2. **Station 4 (Monte Carlo Lab)**:
   - Maintain full fidelity to John Hull Table 14.1: initial price $S_0 = 100$, weekly drift rate $0.15 \times \frac{1}{52} = 0.00288$, volatility factor $0.30 \times \sqrt{\frac{1}{52}} = 0.0416$, and interactive stepping through weeks 1 to 10 with live formula state display.

---

## 3. Key Product Decisions & Trade-Offs

- **Decision 1: Removal of European Call Option Pricing Formula**:
  - *Chosen Approach*: Replace $\hat{C} = e^{-rT}\frac{1}{N}\sum \max(S_T-K, 0)$ with $\Delta S = \mu S \Delta t + \sigma S \epsilon \sqrt{\Delta t}$ and Table 14.1 formula $\Delta S = 0.00288 S + 0.0416 S \epsilon$.
  - *Why*: The user explicitly stated that option pricing was never taught in Dr's slides or in Hull Chapter 14. Chapter 14 solely covers Wiener processes, Itô's lemma, and discrete simulation of stock prices. Option pricing is covered much later in Chapter 21 / Black-Scholes.
  - *Alternatives Considered*: Keeping option pricing as an "advanced extension" was rejected because the user specifically requested removing non-Chapter-14 formulas to prevent academic discrepancies during exhibition grading.

- **Decision 2: Standalone Poster Preservation**:
  - *Chosen Approach*: Maintain `poster.html` and `public/poster.html` as independent, self-contained exhibition artifacts while keeping `index.html` clean for GitHub repository publishing.
  - *Why*: Matches user request #9 to make the poster standalone so the repository is cleanly structured for GitHub and GitHub Pages deployment.

---

## 4. Technical Architecture & Data Strategy

```
┌────────────────────────────────────────────────────────────────────────┐
│                   JOHN HULL CHAPTER 14 FORMULA SYSTEM                  │
└────────────────────────────────────┬───────────────────────────────────┘
                                     │
           ┌─────────────────────────┼─────────────────────────┐
           ▼                         ▼                         ▼
   ┌───────────────┐         ┌───────────────┐         ┌───────────────┐
   │   Station 1   │         │   Station 2   │         │   Station 3   │
   │ Gen. Wiener   │         │  Itô Process  │         │   GBM Stock   │
   │ dx = a dt     │         │ (dz)² = dt    │         │ dS = μS dt    │
   │    + b dz     │         │ dG curvature  │         │    + σS dz    │
   └───────────────┘         └───────────────┘         └───────────────┘
                                                               │
                                                               ▼
                                                       ┌───────────────┐
                                                       │   Station 4   │
                                                       │  Monte Carlo  │
                                                       │  ΔS = μS Δt   │
                                                       │    + σS ε √Δt │
                                                       │ (Table 14.1)  │
                                                       └───────────────┘
```

### Component & File Mapping:
- `/poster.html` & `/public/poster.html`:
  - Equation 3 block: Replace option formula with Hull Eq 14.8 & 14.10.
  - Showcase 3 footer: Update badge & caption to Table 14.1 discrete stepping and lognormal fan.
- `/index.html`:
  - Myth vs Fact Flip Card 4: Update text to remove option pricing reference.
  - Station 4: Confirm discrete weekly and daily time-step modes ($\Delta t = 1/52, 1/252$), Table 14.1 stepper, and lognormal distribution verification.

---

## 5. Verification Plan

1. **Formula Audit**:
   - Verify zero occurrences of $\hat{C} = e^{-rT} \dots$ in `poster.html`, `public/poster.html`, and `index.html`.
   - Verify KaTeX rendering of $\Delta S = \mu S \Delta t + \sigma S \epsilon \sqrt{\Delta t}$ and $\Delta S = 0.00288 S + 0.0416 S \epsilon$.
2. **Build & Compilation**:
   - Run `compile_applet` to ensure syntax is clean.
   - Run `npm run build` to confirm `dist/index.html` and `dist/poster.html` are generated without errors.
3. **Responsive Visual Check**:
   - Confirm poster layout in print mode (`@media print` A3 portrait 297mm x 420mm) and screen preview.
   - Confirm flip cards on mobile and tablet continue to flip cleanly without mirroring or overflow.
