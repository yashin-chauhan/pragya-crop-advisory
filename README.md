# 🌾 Pragya Crop Advisory — Bilingual AgriTech Intelligence & Operating Platform

> **A high-performance, bilingual (Hindi & English) agricultural advisory operating system and REST API engineered for Pragya NGO to empower rural smallholder farmers.**

[![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4?logo=php&logoColor=white)](https://www.php.net/)
[![Laravel](https://img.shields.io/badge/Laravel-10.x-FF2D20?logo=laravel&logoColor=white)](https://laravel.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.x-4479A1?logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Architecture](https://img.shields.io/badge/Architecture-RESTful_API-brightgreen)](https://restfulapi.net/)
[![Domain](https://img.shields.io/badge/Domain-AgriTech_&_NGO-orange)](https://pragya.org/about-us)
[![Localization](https://img.shields.io/badge/Localization-Hindi_|_English-blue)](https://pragya.org/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red)](#-license--notice)

---

## 📌 Notice
*This is a public technical showcase repository documenting the architecture, domain design, and technical decisions of the **Pragya Crop Advisory Platform**. The production deployment and core client assets remain proprietary.*

---

## 💡 The Problem

Smallholder farmers in rural India face critical challenges in accessing timely, scientific, and actionable agronomy guidance:

- **Regional & Language Barrier:** Most modern agricultural research is documented in technical English, leaving vernacular Hindi-speaking rural farmers disconnected from vital agronomic practices.
- **Fragmented Advisory Datasets:** Information regarding soil preparation, optimal fertilizer dosage (NPK ratios), seed treatment, and climate requirements is scattered across disconnected government portals and physical pamphlets.
- **Crop Disease & Pest Outbreaks:** Pests and fungal infections cause devastating crop yield losses when farmers lack immediate, step-by-step biological and chemical treatment guidance.
- **Unscientific Stage-Wise Practices:** Sub-optimal irrigation timing, incorrect sowing methods, and erratic weather patterns severely reduce harvest productivity and soil health.

---

## 🚀 The Solution: Pragya Crop Advisory

Developed for **[Pragya NGO](https://pragya.org/about-us)** (an international non-governmental organization working on sustainable development and grassroots empowerment), the **Pragya Crop Advisory Platform** bridges this gap by delivering scientific, stage-by-stage agronomic intelligence to farmers via a mobile-first digital ecosystem.

1. **Native Bilingual Agronomy Engine:** Complete crop lifecycle recommendations translated and structured seamlessly in both **Hindi (हिंदी)** and **English**.
2. **End-to-End Crop Lifecycle Modeling:** 12+ dedicated agronomy modules covering climate prerequisites, soil analysis, seed selection, land preparation, fertilizer schedules, irrigation milestones, and post-harvest preservation.
3. **Integrated Pest Management (IPM) & Disease Diagnostic Engine:** Direct linkage between plant disease identification and multi-stage corrective chemical/organic measures.
4. **Mobile-First REST API Layer:** High-speed Laravel 10 backend transforming massive relational datasets into lightweight, indexed JSON contracts for native mobile applications.
5. **Dynamic UI & Taxonomy Mapping:** Dynamic heading engine allowing mobile apps to render localized navigation tabs without requiring mobile app binary updates.

---

## 🏗️ System Architecture at a Glance

```mermaid
flowchart TD
    subgraph Clients["📱 Client & Consumer Layer"]
        MOB["📱 Farmer Mobile Application (Android / iOS)"]
        WEB["🌐 Field Officer Web Portal (PHP Legacy)"]
    end

    subgraph Gateway["🛡️ Gateway & Security Layer"]
        CORS["CORS & Route Guards"]
        AUTH["Sanctum Token Layer (Optional Auth)"]
    end

    subgraph CoreEngine["⚙️ Laravel 10 API Core Engine"]
        ROUTER["API Router (/api/v1)"]
        CTRL["HomeController (Agronomy Aggregator)"]
        
        subgraph Services["Core Engine Modules"]
            TAX["Taxonomy & Category Mapper"]
            AGRO["Crop Lifecycle Engine"]
            IPM["Plant Protection & Disease Joiner"]
            LOC["Bilingual Localization Normalizer"]
            HEAD["Dynamic Heading Engine"]
        end
    end

    subgraph Storage["🗄️ Relational Database (MySQL)"]
        T_CROP["rb2_crop / rb2_croptype"]
        T_AGRI["rb2_climate / rb2_soil / rb2_variety / rb2_land"]
        T_STAGE["rb2_sowing (1 & 2) / rb2_nutrient (1 & 2) / rb2_irrigation"]
        T_PEST["rb2_plant_weed_control / rb2_plant_disease_pest / rb2_plant_measure"]
        T_HEAD["headings (Dynamic Navigation Tabs)"]
    end

    Clients --> Gateway
    Gateway --> ROUTER
    ROUTER --> CTRL
    CTRL --> Services
    Services --> Storage
```

---

## 🧩 Core Platform Components

| Subsystem | Primary Tech Stack | Description |
|---|---|---|
| **Backend REST API** | Laravel 10.x, PHP 8.1+, MySQL | High-throughput RESTful API delivering localized JSON payloads with multi-table relational joins. |
| **Mobile Application** | Cross-Platform / Native Mobile | Native farmer mobile app with offline advisory caching, vernacular UI, and dynamic tab navigation. |
| **Web Portal** | Core PHP 8, Responsive CSS | Desktop knowledge portal utilized by field agronomists in village kiosks and training centers. |
| **Dynamic Taxonomy** | Eloquent ORM, MySQL | Dynamic category and navigation heading engine decoupling mobile layout from app releases. |

---

## 🛡️ Key Engineering Highlights

### 1. Composite Relational Joins for Plant Protection
Crop disease and pest management requires linking symptoms (`rb2_plant_disease_pest`) with actionable treatment measures (`rb2_plant_measure`). The backend executes multi-table composite joins, bundling complex remedies into unified single-request payloads to minimize mobile data roundtrips on rural 2G/3G networks.

### 2. Strict Bilingual Localization Invariants
All endpoints enforce strict locale boundaries (`['english', 'hindi']`), mapping queries dynamically to language-partitioned database tables while ensuring Devanagari Unicode (`utf8mb4`) fidelity.

### 3. Dynamic Taxonomy Decoupling
By abstracting navigation headers into dynamic database models, agricultural extension teams can reorder, add, or refine advisory sections without requiring app store updates.

### 4. Global Catch-All Fallback Invariant
All unmapped routes return structured JSON error envelopes, preventing HTML stack traces on mobile clients during unexpected API calls.

---

## 📚 Technical Documentation Index

Explore the comprehensive technical design documents:

- 🏛️ **[System Architecture](ARCHITECTURE.md)** — In-depth component breakdowns and communication patterns
- ⚙️ **[Tech Stack Rationale](TECH_STACK.md)** — Architectural justification for chosen technologies
- 📊 **[Database ERD](diagrams/database-erd.md)** — Complete Entity Relationship Diagram across all `rb2_*` tables
- 🏗️ **[System Architecture Diagram](diagrams/system-architecture.md)** — Visual topology of ingress, backend, and storage
- 🔄 **[Crop Lifecycle Flow](diagrams/crop-lifecycle-flow.md)** — End-to-end 12-stage agricultural decision tree
- 🚀 **[Deployment Topology](diagrams/deployment-topology.md)** — Nginx, PHP-FPM, MySQL, and Cloudflare configuration
- 🌾 **[Agronomy Domain Model](docs/domain/agronomy-model.md)** — 12+ scientific agronomy stages and data models
- 🌿 **[Crop Taxonomy](docs/domain/crop-taxonomy.md)** — Crop classification, categories, and bilingual catalogs
- 🐛 **[Pest & Disease IPM](docs/domain/pest-disease-ipm.md)** — Symptom-to-measure diagnostic linkage
- 🌦️ **[Climate & Weather Engine](docs/domain/climate-weather-engine.md)** — Climatic baselines and rainfall guidance
- 🔌 **[API Design Standards](docs/engineering/api-design.md)** — REST contracts, response envelopes, and error handling
- 🌐 **[Bilingual Localization](docs/engineering/bilingual-localization.md)** — Language routing and Devanagari character handling
- 🔗 **[Composite Relational Joins](docs/engineering/composite-relational-joins.md)** — Multi-table query aggregation architecture
- 🛠️ **[Deployment Guide](docs/engineering/deployment.md)** — Nginx virtual host, PHP-FPM pool, and release commands
- 📱 **[Product Overview](docs/product/overview.md)** — Product vision and user personas
- 📲 **[Mobile App Specifications](docs/product/mobile-app.md)** — User flows and screen contracts
- 🌐 **[Web Portal Specifications](docs/product/web-portal.md)** — Field officer desktop portal design
- 📑 **[Dynamic Advisory Taxonomy](docs/product/advisory-taxonomy.md)** — Database-driven mobile UI navigation engine

---

## 🔌 API Interface Specifications & Contracts

### 1. Crop Categories (Types)
*Retrieves all registered crop families with localized nomenclature and visual assets.*

- **Endpoint:** `GET /api/croptype/{ln}`
- **Parameters:** `ln` $\rightarrow$ `en` | `hi`
- **Response Contract:**
```json
[
  {
    "type_name": "Cereals (अनाज)",
    "type_code": "cereal",
    "image": "cereal_icon.png"
  },
  {
    "type_name": "Pulses (दलहन)",
    "type_code": "pulse",
    "image": "pulse_icon.png"
  }
]
```

---

### 2. Crop Catalog by Category
*Retrieves all crops listed under a given category code for the specified language.*

- **Endpoint:** `GET /api/cropslist/{ln}/{type}`
- **Parameters:** `ln` $\rightarrow$ `english` | `hindi`, `type` $\rightarrow$ category code (e.g. `cereal`)
- **Response Contract:**
```json
[
  {
    "id": 1,
    "crop_id": "wheat",
    "crop_name": "Wheat (गेहूं)",
    "croptype_code": "cereal",
    "lang": "hindi",
    "image": "wheat.jpg"
  }
]
```

---

### 3. Dynamic Advisory Headings
*Provides dynamic tab headings allowing the mobile client to render localized UI sections dynamically.*

- **Endpoint:** `GET /api/detail-headings/{ln}`
- **Parameters:** `ln` $\rightarrow$ `english` | `hindi`
- **Response Contract:**
```json
[
  { "id": 1, "name": "जलवायु (Climate)", "tab": "climate", "lang": "hindi" },
  { "id": 2, "name": "मिट्टी (Soil)", "tab": "soil", "lang": "hindi" },
  { "id": 3, "name": "उन्नत किस्में (Varieties)", "tab": "variety", "lang": "hindi" },
  { "id": 4, "name": "पौध संरक्षण (Plant Protection)", "tab": "plant_protection", "lang": "hindi" }
]
```

---

### 4. Topic-Specific Crop Advisory
*Retrieves deep agronomic intelligence for a specific crop and advisory dimension.*

- **Endpoint:** `GET /api/details/{topic}/{ln}/{crop_id}`
- **Supported Topics:** `climate`, `soil`, `variety`, `land`, `treatment`, `sowing`, `nutrient`, `irrigation`, `interculture`, `plant_protection`, `harvesting`, `weather`
- **Multi-Dataset Composite Response (Example for `plant_protection`):**
```json
{
  "data": [
    {
      "crop_id": "wheat",
      "weed_control": "Apply Isoproturon 75% WP @ 1.0 kg a.i./ha in 500-600 litres of water...",
      "lang": "english"
    }
  ],
  "data2": [
    {
      "crop_id": "wheat",
      "category": "disease",
      "disease_name": "Yellow Rust (पीला रतुआ)",
      "activity": "Foliar Spray",
      "timing": "At first appearance of symptoms",
      "agent": "Propiconazole 25% EC (Tilt)",
      "rate": "0.1% (1 ml per litre of water)"
    }
  ],
  "data3": [
    {
      "crop_id": "wheat",
      "category": "pest_control",
      "pest_name": "Aphids (माहू)",
      "activity": "Chemical Spray",
      "timing": "When aphid population crosses ETL",
      "agent": "Imidacloprid 17.8% SL",
      "rate": "1 ml in 3 litres of water"
    }
  ]
}
```

---

## 🗄️ Relational Database Schema Overview

| Table Name | Entity Description | Key Fields |
| :--- | :--- | :--- |
| `rb2_croptype` | Crop family categories | `type_code`, `type_name`, `hindi`, `image` |
| `rb2_crop` | Registered crops master | `crop_id`, `crop_name`, `croptype_code`, `lang` |
| `rb2_climate` | Climatic requirements | `crop_id`, `temperature_range`, `rainfall_req`, `lang` |
| `rb2_soil` | Soil type & pH conditions | `crop_id`, `soil_type`, `ph_range`, `lang` |
| `rb2_variety` | Recommended seed varieties | `crop_id`, `variety_name`, `duration`, `yield_potential`, `lang` |
| `rb2_land` | Tillage & seedbed preparation | `crop_id`, `ploughing_method`, `soil_treatment`, `lang` |
| `rb2_treatment` | Seed treatment protocols | `crop_id`, `chemical_treatment`, `bio_fungicide`, `lang` |
| `rb2_sowing` / `_2` | Sowing time, spacing & depth | `crop_id`, `sowing_time`, `row_spacing`, `seed_rate`, `lang` |
| `rb2_nutrient_optimal` | NPK & fertilizer recommendations | `crop_id`, `nitrogen`, `phosphorus`, `potassium`, `zinc`, `lang` |
| `rb2_irrigation` | Critical watering milestones | `crop_id`, `critical_stages`, `irrigation_methods`, `lang` |
| `rb2_interculture` | Weeding & hoeing operations | `crop_id`, `intercultural_operations`, `lang` |
| `rb2_plant_disease_pest` | Diseases & pest catalog | `crop_id`, `category`, `symptom`, `count`, `lang` |
| `rb2_plant_measure` | Corrective chemical & organic agents | `crop_id`, `category`, `activity`, `agent`, `rate`, `count`, `lang` |
| `rb2_harvesting` | Maturity indicators & storage | `crop_id`, `harvest_signs`, `moisture_content`, `storage`, `lang` |
| `rb2_weather_rainfall` | Rainfall patterns & advisories | `crop_id`, `monthly_rainfall`, `forecast_advisory`, `lang` |
| `headings` | Dynamic navigation taxonomy | `name`, `tab`, `lang` |

---

## 👨‍💻 Author & Engineering Profile

**Yashin Chauhan**  
*Full Stack & Backend Software Engineer*

- **GitHub:** [@yashin-chauhan](https://github.com/yashin-chauhan)
- **LinkedIn:** [Yashin Chauhan](https://www.linkedin.com/)
- **RentKhata Showcase:** [yashin-chauhan/rentkhata](https://github.com/yashin-chauhan/rentkhata)

---

## 📄 License & Notice
This architecture and documentation showcase is licensed under the [MIT License](LICENSE). The underlying production deployment and client assets remain proprietary.
