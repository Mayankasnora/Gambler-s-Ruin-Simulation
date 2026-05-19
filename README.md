<div align="center">

<svg width="860" height="180" viewBox="0 0 860 180" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="bgGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0a0a0f;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#1a0a2e;stop-opacity:1" />
    </linearGradient>
    <linearGradient id="goldGrad" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#c9a84c" />
      <stop offset="50%" style="stop-color:#f5d27a" />
      <stop offset="100%" style="stop-color:#c9a84c" />
    </linearGradient>
    <filter id="glow">
      <feGaussianBlur stdDeviation="3" result="coloredBlur"/>
      <feMerge>
        <feMergeNode in="coloredBlur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>
    <filter id="softGlow">
      <feGaussianBlur stdDeviation="6" result="coloredBlur"/>
      <feMerge>
        <feMergeNode in="coloredBlur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>
  </defs>

  <!-- Background -->
  <rect width="860" height="180" fill="url(#bgGrad)" rx="12"/>

  <!-- Animated random walk line -->
  <polyline id="walk" points="30,90" fill="none" stroke="#c9a84c" stroke-width="1.5" opacity="0.4"/>

  <!-- Animated walk paths (pre-computed random walk) -->
  <polyline points="30,90 50,78 70,92 90,68 110,82 130,56 150,74 170,88 190,62 210,80 230,50 250,70 270,88 290,60 310,76 330,94 350,65 370,82 390,55 410,75 430,95 450,62 470,80 490,52 510,72 530,90 550,58 570,78 590,95 610,62 630,82 650,48 670,70 690,88 710,55 730,78 750,95 770,60 790,82 810,50 830,72"
    fill="none" stroke="#c9a84c" stroke-width="1.8" opacity="0.35" stroke-dasharray="820" stroke-dashoffset="820">
    <animate attributeName="stroke-dashoffset" from="820" to="0" dur="3.5s" begin="0s" fill="freeze" calcMode="linear"/>
  </polyline>

  <!-- Ruin boundary lines -->
  <line x1="30" y1="120" x2="830" y2="120" stroke="#e05252" stroke-width="1" stroke-dasharray="6,4" opacity="0.5"/>
  <line x1="30" y1="40" x2="830" y2="40" stroke="#52e09a" stroke-width="1" stroke-dasharray="6,4" opacity="0.5"/>

  <!-- Labels -->
  <text x="836" y="124" font-family="monospace" font-size="9" fill="#e05252" opacity="0.8">RUIN</text>
  <text x="836" y="44" font-family="monospace" font-size="9" fill="#52e09a" opacity="0.8">WIN</text>

  <!-- Dice icons (simple) -->
  <g transform="translate(38, 20)" opacity="0.6">
    <rect width="20" height="20" rx="3" fill="none" stroke="#c9a84c" stroke-width="1.2"/>
    <circle cx="6" cy="6" r="1.8" fill="#c9a84c"/>
    <circle cx="14" cy="14" r="1.8" fill="#c9a84c"/>
    <circle cx="14" cy="6" r="1.8" fill="#c9a84c"/>
    <circle cx="6" cy="14" r="1.8" fill="#c9a84c"/>
    <animateTransform attributeName="transform" type="rotate" from="0 48 30" to="360 48 30" dur="8s" repeatCount="indefinite"/>
  </g>

  <!-- Coin flip circles -->
  <g>
    <circle cx="800" cy="30" r="12" fill="none" stroke="#f5d27a" stroke-width="1.5" opacity="0.7">
      <animate attributeName="rx" values="12;2;12" dur="1.6s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.7;0.3;0.7" dur="1.6s" repeatCount="indefinite"/>
    </circle>
    <text x="800" y="35" text-anchor="middle" font-family="monospace" font-size="11" fill="#f5d27a" opacity="0.8">$</text>
  </g>

  <!-- Main Title -->
  <text x="430" y="108" text-anchor="middle" font-family="Georgia, serif" font-size="38" font-weight="bold" fill="url(#goldGrad)" filter="url(#softGlow)" letter-spacing="2">
    Gambler's Ruin
    <animate attributeName="opacity" values="0;1" dur="1s" begin="0.5s" fill="freeze"/>
  </text>

  <!-- Subtitle -->
  <text x="430" y="135" text-anchor="middle" font-family="monospace" font-size="13" fill="#9d8ec9" letter-spacing="4">
    SIMULATION
    <animate attributeName="opacity" values="0;1" dur="1s" begin="1.2s" fill="freeze"/>
  </text>

  <!-- Blinking cursor -->
  <rect x="592" y="121" width="8" height="2" fill="#9d8ec9">
    <animate attributeName="opacity" values="1;0;1" dur="1s" repeatCount="indefinite"/>
  </rect>

  <!-- Bottom decorative bar -->
  <rect x="160" y="158" width="540" height="2" fill="url(#goldGrad)" opacity="0.6" rx="1">
    <animate attributeName="width" from="0" to="540" dur="2s" begin="1s" fill="freeze"/>
    <animate attributeName="x" from="430" to="160" dur="2s" begin="1s" fill="freeze"/>
  </rect>
</svg>

# Gambler's Ruin Simulation

> **🚧 Work in Progress** — Stochastic simulations to study the Gambler's Ruin problem and random walk behavior.

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Status](https://img.shields.io/badge/Status-In%20Progress-f5d27a?style=flat-square)](.)
[![License](https://img.shields.io/badge/License-MIT-52e09a?style=flat-square)](LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/Mayankasnora/Optimal-Stopping?style=flat-square&color=c9a84c)](.)

</div>

---

## 📖 Overview

The **Gambler's Ruin** is a classic problem in probability theory: a gambler starts with some initial capital and repeatedly bets, winning or losing $1 each round with a fixed probability. The game ends when the gambler either reaches a target fortune or goes **broke (ruin)**.

This project uses **stochastic simulations** in Python to:
- Compute empirical ruin probabilities across different starting capitals
- Analyze how the win probability `p` shifts expected outcomes dramatically
- Visualize random walk trajectories and absorption at boundaries
- Validate simulation results against closed-form analytical solutions

---

## 🎲 The Math Behind It

For a gambler starting with $k$ aiming for $N$, with win probability $p$ per round:

$$P(\text{ruin} \mid k) = \begin{cases} \dfrac{(q/p)^k - (q/p)^N}{1 - (q/p)^N} & p \neq \frac{1}{2} \\[10pt] 1 - \dfrac{k}{N} & p = \frac{1}{2} \end{cases}$$

where $q = 1 - p$.

---

## 🗂️ Project Structure

```
Gambler's-Ruin/
│
├── simulation/
│   ├── gambler_ruin.py       # Core simulation logic
│   ├── random_walk.py        # Random walk generator
│   └── analytics.py          # Statistical analysis & expected values
│
├── plots/
│   ├── ruin_probability.png  # Ruin prob vs initial capital
│   ├── walk_trajectories.png # Sample random walk paths
│   └── heatmap.png           # p vs k heatmap
│
├── notebooks/
│   └── exploration.ipynb     # Jupyter analysis notebook
│
├── tests/
│   └── test_simulation.py    # Validation against analytical results
│
├── requirements.txt
└── README.md
```

> **Note:** Structure is tentative and will evolve as the project develops.

---

## ⚙️ Installation

```bash
# Clone the repository
git clone https://github.com/Mayankasnora/Gambler-Ruin.git
cd Gambler-Ruin

# Install dependencies
pip install -r requirements.txt
```

**Requirements** *(planned)*:
- `numpy` — array ops & random number generation
- `matplotlib` / `seaborn` — plotting
- `scipy` — statistical distributions & validation
- `tqdm` — progress bars for long simulations

---

## 🚀 Usage

```python
# Coming soon — example usage will be added as simulation modules are built
from simulation.gambler_ruin import simulate_ruin

result = simulate_ruin(
    initial_capital=50,
    target=100,
    win_prob=0.48,
    num_trials=10_000
)

print(f"Empirical ruin probability: {result.ruin_prob:.4f}")
print(f"Expected game duration:     {result.avg_duration:.1f} rounds")
```

---

## 📊 Planned Experiments

- [ ] **Baseline**: Fair coin (`p = 0.5`) ruin probability vs. $k$
- [ ] **House edge**: Effect of `p < 0.5` (casino-style odds)
- [ ] **Capital sweep**: How doubling starting capital changes survival
- [ ] **Duration analysis**: Expected number of rounds before absorption
- [ ] **Martingale comparison**: Compare flat-betting vs. doubling strategy
- [ ] **Multi-player extension**: Ruin when competing against another gambler

---

## 📈 Key Findings

> Results will be populated as experiments are completed.

---

## 🤝 Contributing

This is a personal learning project, but suggestions and discussions are welcome. Feel free to open an issue if you spot something interesting or have ideas for extensions.

---

<div align="center">

<svg width="860" height="100" viewBox="0 0 860 100" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="footBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0a0a0f;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#1a0a2e;stop-opacity:1" />
    </linearGradient>
    <linearGradient id="goldGrad2" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#c9a84c" />
      <stop offset="50%" style="stop-color:#f5d27a" />
      <stop offset="100%" style="stop-color:#c9a84c" />
    </linearGradient>
  </defs>

  <rect width="860" height="100" fill="url(#footBg)" rx="12"/>

  <!-- Animated probability bars -->
  <g transform="translate(60, 20)">
    <!-- p=0.3 -->
    <rect x="0" y="50" width="12" height="0" fill="#e05252" rx="2" opacity="0.8">
      <animate attributeName="height" from="0" to="40" dur="1s" begin="0.2s" fill="freeze"/>
      <animate attributeName="y" from="50" to="10" dur="1s" begin="0.2s" fill="freeze"/>
    </rect>
    <!-- p=0.4 -->
    <rect x="20" y="50" width="12" height="0" fill="#e07852" rx="2" opacity="0.8">
      <animate attributeName="height" from="0" to="28" dur="1s" begin="0.4s" fill="freeze"/>
      <animate attributeName="y" from="50" to="22" dur="1s" begin="0.4s" fill="freeze"/>
    </rect>
    <!-- p=0.5 -->
    <rect x="40" y="50" width="12" height="0" fill="#c9a84c" rx="2" opacity="0.8">
      <animate attributeName="height" from="0" to="18" dur="1s" begin="0.6s" fill="freeze"/>
      <animate attributeName="y" from="50" to="32" dur="1s" begin="0.6s" fill="freeze"/>
    </rect>
    <!-- p=0.6 -->
    <rect x="60" y="50" width="12" height="0" fill="#7ab852" rx="2" opacity="0.8">
      <animate attributeName="height" from="0" to="10" dur="1s" begin="0.8s" fill="freeze"/>
      <animate attributeName="y" from="50" to="40" dur="1s" begin="0.8s" fill="freeze"/>
    </rect>
    <!-- p=0.7 -->
    <rect x="80" y="50" width="12" height="0" fill="#52e09a" rx="2" opacity="0.8">
      <animate attributeName="height" from="0" to="4" dur="1s" begin="1.0s" fill="freeze"/>
      <animate attributeName="y" from="50" to="46" dur="1s" begin="1.0s" fill="freeze"/>
    </rect>
    <text x="46" y="65" text-anchor="middle" font-family="monospace" font-size="7" fill="#9d8ec9">P(ruin) vs p</text>
  </g>

  <!-- Divider -->
  <line x1="190" y1="15" x2="190" y2="85" stroke="#3a2a5e" stroke-width="1"/>

  <!-- Center text -->
  <text x="430" y="42" text-anchor="middle" font-family="Georgia, serif" font-size="15" fill="url(#goldGrad2)" letter-spacing="1">
    "In the long run, the house always wins."
  </text>
  <text x="430" y="62" text-anchor="middle" font-family="monospace" font-size="10" fill="#9d8ec9">
    — Unless you understand the math.
  </text>
  <text x="430" y="82" text-anchor="middle" font-family="monospace" font-size="9" fill="#5a4a7e">
    Built by Mayank Asnora · Stochastic Simulations · Python
  </text>

  <!-- Divider right -->
  <line x1="670" y1="15" x2="670" y2="85" stroke="#3a2a5e" stroke-width="1"/>

  <!-- Animated coin right side -->
  <g transform="translate(760, 50)">
    <circle cx="0" cy="0" r="22" fill="none" stroke="#c9a84c" stroke-width="2" opacity="0.5">
      <animate attributeName="r" values="22;24;22" dur="2s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.5;0.8;0.5" dur="2s" repeatCount="indefinite"/>
    </circle>
    <text x="0" y="5" text-anchor="middle" font-family="serif" font-size="20" fill="#f5d27a" opacity="0.8">$</text>
    <animateTransform attributeName="transform" type="rotate" from="0 760 50" to="360 760 50" dur="10s" repeatCount="indefinite"/>
  </g>
</svg>

*🎲 Every random walk ends — the question is where.*

</div>
