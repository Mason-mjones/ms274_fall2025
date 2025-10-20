# 🌊 Model Project: Bathymetry Resolution Effects on Ocean Model Dynamics


##  Overview
This project investigates how **inaccurate or low-resolution bathymetry** alters the state of an ocean model — with a specific focus on how it affects **currents** within the model domain.

The **study area** is the **head of the Monterey Bay Submarine Canyon**, a region known for complex bathymetric structure and dynamic current systems.

---

##  Objectives
- Quantify the effect of bathymetric resolution on modeled ocean currents.  
- Compare model results using **5 m (USGS)** and **20 cm (custom)** bathymetric datasets.  
- Evaluate temporal and spatial differences in **temperature** and **current patterns**.

---

##  Methods

### Model Setup
Two numerical model runs will be performed:

| Model | Bathymetry Source | Resolution |
|--------|-------------------|-------------|
| Low-resolution | USGS | 5 m |
| High-resolution | Personal dataset | 20 cm |

Both simulations cover **the year 2000**, chosen because:
- Two of the five **largest significant wave height events** occurred that year.  
- It marks the first operational year of the **CDIP MOP model**, enabling cross-reference.

### Initial and Boundary Conditions
- **Initial Conditions:** ECCO Version 4.4 output for January 2000.  
- **Boundary & External Forcing:** Also derived from ECCO V4.4 datasets.

---

##  Analysis
- Generate a **temperature time series** at the canyon head for both models.  
- Compare differences over time to assess the impact of bathymetric resolution.  
- Visualize results by creating an **animation** of current differences between the two simulations.

---

##  Expected Outcomes
- Quantitative assessment of how bathymetry resolution affects modeled current structures.  
- Visual representation of current discrepancies under different bathymetric conditions.  
- Insights into **model sensitivity** to topographic detail in coastal and canyon environments.

---

