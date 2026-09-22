# 🔄 Diagram: Stage-Wise Crop Advisory Lifecycle Flow

Represents the complete agronomic timeline and decision stages supported by the Pragya Crop Advisory engine from pre-sowing to post-harvest.

```mermaid
flowchart TD
    START([🌾 Season Planning]) --> C1[1. Climate & Weather Check\nrb2_climate & rb2_weather]
    C1 --> C2[2. Soil Testing & Suitability\nrb2_soil]
    C2 --> C3[3. Variety Selection\nrb2_variety]
    C3 --> C4[4. Field & Land Preparation\nrb2_land]
    C4 --> C5[5. Seed Treatment & Inoculation\nrb2_treatment]
    C5 --> C6[6. Scientific Sowing / Planting\nrb2_sowing & rb2_sowing_2]
    
    subgraph GrowthCycle["🌱 Vegetative & Reproductive Growth Management"]
        C6 --> G1[7. Optimal Nutrient & Fertilizer Dosage\nrb2_nutrient_optimal & rb2_nutrient_optimal_2]
        G1 --> G2[8. Critical Stage Irrigation\nrb2_irrigation]
        G2 --> G3[9. Weeding & Intercultural Operations\nrb2_interculture & rb2_plant_weed_control]
        G3 --> G4[10. Disease & Pest Diagnosis (IPM)\nrb2_plant_disease_pest + rb2_plant_measure]
    end

    G4 --> H1[11. Harvesting Signs & Maturity\nrb2_harvesting]
    H1 --> H2[12. Post-Harvest Storage & Market Prep\nrb2_harvesting]
    H2 --> END([💰 Maximized Farmer Yield & Profit])
```
