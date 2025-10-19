# 🍊 Modeling Mold Growth on an Orange: A Multi-Agent Simulation in NetLogo 3D

**Authors:**  
Cesare Maria Dalbagno · Francesco Fumagalli · Nikhil Yadav · Rosalie Priol · Jess Severijns  
Tilburg University, Cognitive Science and Artificial Intelligence Department  

---

## 🧩 Project Overview

This project explores **mold growth dynamics on an orange** under varying environmental and packaging conditions, using a **multi-agent simulation built in NetLogo 3D**.  
By combining biologically inspired modeling with environmental parameters, we aim to understand how **temperature, humidity, packaging shape, and material** influence mold development — providing insights relevant to **food sustainability and waste reduction**.

---

## 🌍 Research Motivation

How can we better understand and mitigate food spoilage caused by mold?  
Fungal growth is a major contributor to food waste and is highly sensitive to micro-environmental conditions such as **temperature, humidity, and packaging permeability**.  
Our goal was to design a model that balances **realism and computational simplicity**, enabling controlled experimentation with these variables in silico.

---

## 🎯 Research Question

> *What is the effect of packaging shape and material in simulated fridge vs. room environments on mold growth in a multi-agent-based model of an orange?*

### Sub-questions
1. How does **packaging shape** (cube, cuboid) affect mold growth in fridge environments?  
2. How does **packaging material** (paper, plastic) affect mold growth in fridge environments?  
3. How does packaging shape affect mold growth in room environments?  
4. How does packaging material affect mold growth in room environments?

---

## 🧠 Model Description

The simulation represents:
- A **3D orange** consisting of *skin*, *flesh*, and *air patches*.  
- **Humidity droplets** modeled via a **Diffusion-Limited Aggregation (DLA)** process.  
- **Mold nuclei** that sprout on the orange surface depending on local humidity and temperature.  
- **Hyphae agents** that penetrate the fruit’s interior and expand probabilistically.  
- **Packaging** (cube or cuboid, plastic or paper) that modifies air flow and moisture dynamics.

### Key Fixed Parameters

| Parameter | Default | Description |
|------------|----------|-------------|
| `orange-size` | 10 | Radius of the simulated orange |
| `max_skin_humidity` | 50 | Saturation threshold of surface humidity |
| `spread_speed` | 35 | Rate at which mold spreads |
| `spore-stickiness` | 50 | Resistance of spores to low humidity |
| `num_hyphae` | 24 | Hyphae spawned per mold nucleus |
| `max_depth` | 4 | Maximum hyphae penetration depth |

---

## 🔬 Simulation Method

The model was executed via **NetLogo BehaviorSpace**, simulating multiple environmental and packaging configurations.

**Independent variables:**
- **Temperature:** 5 °C (Fridge) / 20 °C / 35 °C (Room)
- **Humidity:** 25% / 50% / 75%
- **Packaging:** None / Cube / Cuboid
- **Material:** Paper / Plastic

Each condition was run 40 times and evaluated for the percentage of orange patches colonized by mold (presence of hyphae).

---

## 📈 Analysis and Results

A **logistic growth model** was fitted to the mold coverage data:

\[
N(t) = \frac{d}{1 + e^{b(t - e)}}
\]

where:  
- *b* = growth steepness  
- *d* = saturation value  
- *e* = inflection point (onset delay)

**Findings:**
- Mold grew fastest with **no packaging** and at **room temperature (20–35 °C)**.  
- **Plastic packaging** delayed and limited mold growth compared to **paper**.  
- **Cuboid packaging** allowed more mold spread than **cube** due to increased air exposure.  
- **Fridge environments** drastically reduced overall mold growth (Cohen’s *d* = 0.98).  

These results align with biological expectations from the literature, confirming the model’s ecological plausibility.

---

## 🧰 How to Run the Model

### Requirements
- [NetLogo 3D (version 6.3+)](https://ccl.northwestern.edu/netlogo/)
- Sufficient 3D rendering capability (for visualization of agents)

### Steps
1. Clone this repository:
   ```bash
   git clone https://github.com/<yourusername>/molding-orange-simulation.git
   cd molding-orange-simulation
