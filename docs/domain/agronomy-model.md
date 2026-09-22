# 🌾 Domain: Agronomy & Crop Lifecycle Model

This document outlines the domain design and data modeling for the 12+ scientific agronomy stages managed by the Pragya Crop Advisory Platform.

---

## 1. Domain Overview

Agronomy modeling represents the transition of raw agricultural research into structured, sequential guidance stages for rural smallholder farmers. Each stage addresses critical decisions influencing crop yield and resource conservation.

```mermaid
flowchart LR
    S1[Pre-Sowing & Soil] --> S2[Sowing & Nutrition]
    S2 --> S3[Crop Protection & Irrigation]
    S3 --> S4[Harvest & Post-Harvest]
```

---

## 2. Core Agronomy Dimensions

### 2.1 Climate & Soil Prerequisites (`rb2_climate`, `rb2_soil`)
- **Climate Parameters:** Optimal temperature ranges for germination, vegetative growth, and grain filling.
- **Soil Attributes:** Soil texture (Sandy Loam, Clay Loam, Alluvial), optimal pH levels ($6.0 - 7.5$), and drainage specifications.

### 2.2 Variety Selection & Land Preparation (`rb2_variety`, `rb2_land`)
- **Varieties:** High-Yielding Varieties (HYV), drought-tolerant seeds, maturity duration (days to harvest), and potential grain yield (quintals/hectare).
- **Land Preparation:** Deep ploughing, harrowing requirements, leveling, and farmyard manure (FYM) baseline integration.

### 2.3 Seed Treatment & Scientific Sowing (`rb2_treatment`, `rb2_sowing`, `rb2_sowing_2`)
- **Seed Treatment:** Biological agents (*Trichoderma*, *Rhizobium*) and chemical fungicides to prevent seed-borne pathogens.
- **Sowing Standards:** Line sowing vs broadcasting, row-to-row spacing ($20-22.5\text{ cm}$), plant-to-plant spacing ($10\text{ cm}$), and seed depth ($4-5\text{ cm}$).

### 2.4 Optimal Nutrient Management (`rb2_nutrient_optimal`, `rb2_nutrient_optimal_2`)
- **Macronutrients (NPK):** Nitrogen ($N$), Phosphorus ($P_2O_5$), and Potassium ($K_2O$) ratio scheduling across basal and top-dressing stages.
- **Micronutrients:** Zinc Sulfate ($ZnSO_4$), Boron, and organic bio-fertilizer dosages.

### 2.5 Water & Intercultural Operations (`rb2_irrigation`, `rb2_interculture`)
- **Critical Irrigation Milestones:** Crown Root Initiation (CRI), tillering, flowering, and grain milking stages.
- **Interculture:** Manual weeding windows, intercultural hoeing, and chemical weedicide application guidelines.

### 2.6 Harvesting & Storage (`rb2_harvesting`)
- **Maturity Indicators:** Visual cues (leaf yellowing, moisture drop).
- **Safe Storage:** Grain moisture thresholds ($\le 10-12\%$) and storage fumigation methods to prevent post-harvest weevil infestation.
