# 🌿 Domain: Crop Taxonomy & Cataloging

This document outlines the classification hierarchy and bilingual cataloging mechanism used in the Pragya Crop Advisory Platform.

---

## 1. Classification Hierarchy

The crop catalog is organized into a two-level hierarchy designed for intuitive navigation on mobile screens:

```mermaid
flowchart TD
    CAT[Crop Category / Type: rb2_croptype\n(Cereals, Pulses, Oilseeds, Cash Crops)]
    
    CAT --> CROP1[Crop 1: Wheat / गेहूं\n(rb2_crop)]
    CAT --> CROP2[Crop 2: Rice / धान\n(rb2_crop)]
    CAT --> CROP3[Crop 3: Maize / मक्का\n(rb2_crop)]
```

---

## 2. Supported Crop Categories (`rb2_croptype`)

| Category Code | English Nomenclature | Hindi Nomenclature (हिंदी) | Representative Crops |
| :--- | :--- | :--- | :--- |
| `cereal` | Cereals & Millets | अनाज एवं मोटा अनाज | Wheat, Rice, Maize, Bajra |
| `pulse` | Pulses & Legumes | दलहन | Gram (Chana), Lentil (Masoor), Pigeon Pea (Arhar) |
| `oilseed` | Oilseeds | तिलहन | Mustard, Soybean, Groundnut |
| `cashcrop` | Commercial / Cash Crops | नकदी फसलें | Sugarcane, Cotton, Jute |
| `vegetable` | Vegetables | सब्जियां | Potato, Tomato, Onion |

---

## 3. Localization Attributes

Every crop entity contains dual-language indexing:

- **Slug / Identifier:** Fixed alphanumeric code (e.g. `wheat`, `rice`) used as the immutable cross-table foreign key.
- **Display Name:** Localized name dynamically queried based on the active client locale (`Wheat` for English, `गेहूं` for Hindi).
- **Icon / Visual Asset:** Visual thumbnail reference enabling quick visual recognition for low-literacy farmers.
