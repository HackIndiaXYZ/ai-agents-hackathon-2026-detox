<![CDATA[# 🏥 AYUVANT — AI-Powered Smart Pharmacy & Healthcare Supply Ecosystem

> **Team DETOX** · HackIndia AI Agents Hackathon 2026

---

## 💡 The Problem We Are Solving

Every year in India, **thousands of patients** suffer because their local pharmacy ran out of a critical medicine — not because the medicine doesn't exist, but because **no one predicted the demand in time**.

**The reality today:**
- 🔴 A chemist in Zone A has 500 units of Azithromycin sitting idle, while a chemist 3 km away in Zone B has zero stock and patients waiting.
- 🔴 Seasonal outbreaks (dengue, flu, COVID waves) spike medicine demand overnight — but pharmacies only realize *after* they run out.
- 🔴 When a brand-name drug is unavailable, pharmacists have no quick way to find a therapeutically equivalent generic substitute with the same active salts.
- 🔴 There is no system to track whether a patient's medicine purchases are escalating (e.g., moving from mild painkillers to heavy antibiotics) — an early warning sign of worsening health.

**The root cause?** India's pharmacy supply chain is **reactive, siloed, and non-intelligent**. Each pharmacy operates as an isolated unit with no demand forecasting, no inter-pharmacy coordination, and no patient-level intelligence.

---

## ✅ Our Solution — AYUVANT

**AYUVANT** is a complete, AI-powered pharmacy intelligence platform that transforms how medicines are managed, predicted, distributed, and tracked at the local level.

### What AYUVANT Does (In Simple Terms):

| Capability | What It Means |
|------------|---------------|
| 📦 **Manages Inventory** | Pharmacists add medicine batches with expiry dates, quantities, and dosage forms. The system tracks everything and alerts before stock runs low or expires. |
| 🧠 **Predicts Shortages Before They Happen** | A local ML model learns from every sale — which medicine, which zone, which day, which month — and forecasts what will run out next week or next month. |
| 🗺️ **Maps Demand by Geography** | The area around a pharmacy is divided into 2km × 2km grid zones. Each zone is color-coded by demand intensity so the pharmacist can see which neighborhoods need what. |
| 📰 **Detects Outbreaks from News** | Monitors simulated news feeds, Google Trends, and government health bulletins. If dengue cases spike in a region, AYUVANT warns the pharmacist to stock up on relevant medicines. |
| 🤖 **Answers Pharmacist Questions** | An AI Q&A assistant lets the pharmacist ask: *"Which medicine will I run out of?"*, *"Which zone needs what?"*, *"In how many days will I need to restock?"* — and gets data-driven answers. |
| 🔄 **Transfers Stock Between Pharmacies** | If Pharmacy A has surplus and Pharmacy B has a shortage, AYUVANT recommends and tracks a peer-to-peer stock transfer with a full lifecycle (Requested → Approved → In Transit → Delivered). |
| 💊 **Recommends Generic Alternatives** | When a brand-name drug is unavailable, AYUVANT finds alternatives with matching active salts, scores them on therapeutic equivalence (salt match, dosage form, strength, category), and compares prices. |
| 📝 **Collects Pharmacist Feedback** | After every generic substitution, a 6-question structured form captures efficacy, patient concerns, price sensitivity, and pharmacist recommendation — feeding back into the AI to improve future suggestions. |
| 👤 **Tracks Patient Health Over Time** | Patients are registered by mobile number. Every purchase builds a timeline. The system classifies their health trajectory as Improving / Stable / Concerning / Escalating and raises flags for dangerous patterns. |
| 📊 **Generates Network-Wide Insights** | Aggregates data across all modules into dashboards: substitution success rates, batch repeat rates, top medicine pairs, seasonal patterns, and network transfer volumes. |

---

## 🏗️ System Architecture — Three Progressive Modules

AYUVANT is built as **three interconnected modules**, each adding a layer of intelligence:

```
┌─────────────────────────────────────────────────────────────┐
│                    AYUVANT ECOSYSTEM                        │
│                                                             │
│  ┌─────────────┐  ┌──────────────┐  ┌────────────────────┐ │
│  │   PART 1    │  │    PART 2    │  │      PART 3        │ │
│  │  Inventory  │──│  AI + Zones  │──│  Network + Patient │ │
│  │  & Sales    │  │  & Predict   │  │  & Distribution    │ │
│  └─────────────┘  └──────────────┘  └────────────────────┘ │
│        │                 │                    │             │
│        ▼                 ▼                    ▼             │
│   Medicine DB      ML Forecasts      Transfer Routing      │
│   Batch CRUD       Zone Heatmaps     Salt-Based Alts       │
│   Stock Alerts     News Intel        Patient Timelines      │
│   Sales Logger     AI Q&A Bot        Feedback Analytics     │
└─────────────────────────────────────────────────────────────┘
```

---

## 📦 Part 1 — Core Pharmacy Platform

> *The operational foundation — managing what's on the shelf today.*

### Features:

**1. Medicine Batch Entry System**
- Pharmacists enter: Batch Number, Medicine Name, Dosage Form (Tablet/Syrup/Inhaler/Cream/etc.), Dosage Strength, Quantity, Manufacturing Date, Expiry Date.
- Medicine names auto-suggest from a master database of real Indian medicines with salt compositions.
- Dosage strengths dynamically load based on the selected medicine type.

**2. Inventory Dashboard**
- Real-time stat cards: Total Batches, Total Units in Stock, Expiring Soon count.
- Full-text search across medicine names and batch numbers.
- Visual batch cards with color-coded expiry indicators (green = safe, yellow = expiring soon, red = expired).

**3. Stock & Expiry Monitoring**
- Automatically flags batches approaching expiry date.
- Tracks low-stock conditions against configurable thresholds.
- Persistent data — survives browser refresh via `localStorage`.

**4. Module Switcher**
- A unified navigation bar at the top lets pharmacists seamlessly switch between Part 1 (Inventory), Part 2 (AI Intelligence), and Part 3 (Smart Distribution).

---

## 🧠 Part 2 — AI Intelligence & Zone Map System

> *Predicting tomorrow's shortages using today's sales data.*

### Features:

**5. Medicine Sale Recording with Zone Tracking**
- When a medicine is sold, the pharmacist records: Medicine Name, Batch Number, and the Buyer's Zone Number.
- This zone-tagged sales data is the fuel for all predictions.

**6. Geospatial Zone Grid System (2km × 2km)**
- The geographic area around the pharmacy is divided into a grid of 2km × 2km squares.
- Each square = one zone. The zone number is derived from GPS coordinates:
  ```
  zone_x = floor(longitude / grid_size)
  zone_y = floor(latitude / grid_size)
  zone_id = derived from average coordinates of that square
  ```
- The pharmacist's map view shows their central zone + up to 10 surrounding zones in 360°.
- Zones are color-coded by demand intensity (red = high demand, green = low).

**7. Local ML Demand Prediction Engine**
- Runs **entirely offline in the browser** — no server, no cloud, no API calls.
- Trained on the pharmacy's own historical sales data.
- Learns patterns by:
  - **Month** — which months have higher demand for which medicines.
  - **Day of Week** — which weekdays see spikes.
  - **Zone** — which geographic zones have recurring needs.
- Generates **weekly and monthly forecasts**: "You will likely run out of Paracetamol in Zone 4 within 6 days."
- **Self-improving**: Every new sale automatically refines the model. The more data, the sharper the predictions.

**8. Outbreak News Intelligence**
- Monitors simulated news feeds, Google Trends signals, and government health bulletins.
- If a disease surge is detected (e.g., dengue outbreak in nearby zones), the system pushes proactive alerts to stock up on relevant medicines.

**9. Smart Notification System**
- Push-style notifications warning about:
  - Upcoming demand spikes (from ML predictions).
  - Which medicine, in which zone, by when.
  - Actionable: "Fill supply of Azithromycin before Thursday."

**10. AI Q&A Assistant (Pre-fixed Questions)**
- Pharmacists select from intelligent preset questions:
  - *"Is there any medicine needed?"* → Lists medicines running low or predicted to run out.
  - *"Which zone around requires which medicine?"* → Zone-wise breakdown of demand.
  - *"What is the probability — when and after how many days will a medicine be required?"* → Date/time predictions for specific medicines.
- The AI responds with data-driven, quantified answers from the prediction model.

---

## 🌐 Part 3 — Smart Distribution & Patient Intelligence

> *Connecting pharmacies into a collaborative network and tracking patient wellness.*

This is a **6-tab dashboard** with the following capabilities:

### Features:

**11. Inter-Pharmacy Stock Transfer Network**
- Simulates a network of 6 nearby pharmacies, each with their own stock levels, zone, distance, and coordinates.
- **AI-Powered Transfer Scoring**: When a medicine is short, the system ranks nearby pharmacies by:
  - Surplus stock available
  - Physical distance
  - Local demand score (weighted AI scoring)
- **Full Transfer Lifecycle**: `Requested` → `Approved` → `In Transit` → `Delivered` — each step timestamped and tracked.
- Pharmacists can search for a medicine and instantly see which neighbor has it in surplus.

**12. Salt-Based Alternative Recommendation Engine**
- When a specific brand is out of stock, the engine searches the entire medicine database for generics with matching active salt compositions.
- **Therapeutic Match Score** (weighted algorithm):

  | Factor | Weight |
  |--------|--------|
  | Active Salt Match | 50% |
  | Medicine Category | 20% |
  | Dosage Form | 15% |
  | Strength Similarity | 15% |

- **Price Comparison**: Shows whether the alternative is cheaper, same price, or more expensive than the original.
- **Quick Sell**: A "Sell This" button lets the pharmacist immediately sell the substitute and triggers a feedback form.

**13. Pharmacist Feedback Collection & AI Learning**
- After every generic substitution, a structured 6-question feedback form is presented:

  | # | Question | Input Type |
  |---|----------|------------|
  | 1 | Was the patient informed about the substitution? | Yes / No |
  | 2 | Rate the alternative's effectiveness | 5-star rating |
  | 3 | What concerned the patient? | Multi-select chips (Price, Brand trust, Side effects, etc.) |
  | 4 | Would you recommend this substitute again? | 1–10 slider |
  | 5 | Patient's price sensitivity | Single-select (Accepted / Hesitant / Refused) |
  | 6 | Additional observations | Free text |

- **AI Learning Loop**: All feedback is aggregated into insights — average satisfaction score, recommendation rate, top concern reasons with ranked bar charts. This data improves future alternative suggestions.

**14. Patient Health Tracker**
- **Registration**: Patients register via mobile number (with optional name, age, gender). Each gets a unique `PAT-XXXXX` ID.
- **Purchase Timeline**: A vertical timeline showing every medicine purchase — medicine name, batch, quantity, date — creating a medical purchase history.
- **Health Trajectory Classification**: Based on purchase patterns, each patient is classified as:
  - 🟢 **Improving** — buying less medication over time, or shifting to milder medicines.
  - 🔵 **Stable** — consistent, expected purchase patterns.
  - 🟡 **Concerning** — increasing frequency or shifting categories.
  - 🔴 **Escalating** — dangerous patterns like moving from painkillers to antibiotics to steroids.
- **Health Flags**: Automatic alerts for:
  - Frequent purchases of the same medicine (possible dependency or worsening condition).
  - Category escalation (e.g., OTC → Rx → controlled substances).
  - Multi-category purchases in short timeframes.

**15. Pattern Analysis Dashboard**
- **Batch Repeat Rate**: How often specific batches are re-purchased.
- **Medicine Seasonality**: Which medicines spike in which months.
- **Patient Trajectory Overview**: Aggregated view of all patient health trajectories with category filtering.

**16. Network-Wide Insights Dashboard**
- Aggregated statistics across all modules:
  - Total substitutions made, success rate gauge (SVG-rendered).
  - Top medicine pairs (original → substitute).
  - Network transfer volumes and routes.
  - Feedback sentiment analysis.

---

## 🗄️ Master Dataset & Data Pipeline

AYUVANT is powered by a **comprehensive pharmacy master dataset** (`pharmacy_master_dataset.json`) containing:

| Data Category | Contents |
|---------------|----------|
| **Diseases** | Disease names, ICD codes, categories |
| **Symptoms** | Symptom names, severity levels, linked disease IDs |
| **Medicines** | Brand names, types (Tablet/Syrup/Inhaler/etc.), OTC/Rx classification, linked disease IDs |
| **Salt Compositions** | Active pharmaceutical ingredients with linked medicine IDs |
| **Dosage Strengths** | Organized by dosage form type (Tablet, Syrup, Injection, etc.) with medicine ID mappings |
| **Side Effects** | Effect descriptions, severity ratings, linked medicine IDs |
| **Usage Guidelines** | Administration instructions by dosage form type |
| **Suspicious Health Issues** | Flag patterns (e.g., "patient buying controlled substances frequently"), actions to take |

### Data Compiler (`build/transform-dataset.js`)

A Node.js script that reads the master JSON dataset and generates two optimized JavaScript files for the browser:

- **`clinical-intelligence.js`** — Diseases, symptoms, disease-medicine maps, side effects, dosage strengths, usage guidelines, suspicious health issues.
- **`medicines.js`** — Full medicine catalog with parsed active salts, strengths, units, generic names, therapeutic classes, and pre-computed alternative medicine IDs.

---

## 🎨 Design System — AYUVANT Futuristic Dark

Every screen is built with a custom **futuristic dark theme** designed for extended pharmacist use:

| Element | Design |
|---------|--------|
| **Background** | Deep dark (`#0E0E13`) with animated floating glow orbs and a subtle CSS grid pattern |
| **Cards** | Glassmorphism — frosted glass panels with 20% opacity, 12px backdrop-blur, and 1px semi-transparent borders |
| **Primary Accent** | Electric Cyan `#00E5FF` — used for active states, input focus glows, AI highlights |
| **Secondary Accent** | Vibrant Purple `#7C4DFF` — secondary actions, warning states |
| **Success Accent** | Neon Green `#00E676` — successful operations, healthy stock, approved transfers |
| **Error** | Warm Red `#FF716C` — expired batches, critical alerts, escalation flags |
| **Typography** | **Sora** (bold headers), **Inter** (body text), **Space Grotesk** (labels, metrics, monospace badges) |
| **Buttons** | Gradient fills (Cyan → Purple) with outer glow on hover |
| **Animations** | Smooth CSS transitions, pulse dots for live status, slide-up modals, auto-dismiss toasts |
| **Layout** | Mobile-first responsive design with 12px border-radius on all components |

---

## 💾 How Data Is Stored

AYUVANT runs **100% client-side** with no backend server required. All data persists in the browser's `localStorage`:

| Storage Key | Module | What It Stores |
|-------------|--------|----------------|
| `ayuvant_inventory` | Part 1 | All medicine batches with quantities, dates, dosage info |
| `ayuvant_sales_history` | Part 1 + 2 | Every sale record with medicine name, batch, zone, timestamp |
| `ayuvant_pharmacy_network` | Part 3 | Simulated nearby pharmacy stock levels and metadata |
| `ayuvant_transfers` | Part 3 | Active and completed inter-pharmacy transfer records |
| `ayuvant_feedback` | Part 3 | All pharmacist feedback responses (pending + completed) |
| `ayuvant_patients` | Part 3 | Patient profiles, purchase timelines, and health trajectories |

---

## 🚀 How to Run

No installations, no dependencies, no server. Just a browser.

### Step 1: Clone
```bash
git clone https://github.com/HackIndiaXYZ/ai-agents-hackathon-2026-detox.git
cd ai-agents-hackathon-2026-detox
```

### Step 2: Open Any Module

| Module | File to Open | What You'll See |
|--------|-------------|-----------------|
| **Part 1** — Inventory | `part1/index.html` | Dashboard with batch entry form. Add medicines, track stock, see expiry alerts. |
| **Part 2** — AI Intelligence | `part2/index.html` | Zone maps, ML predictions, news intelligence, notification feed, AI Q&A console. |
| **Part 3** — Distribution & Patients | `part3/index.html` | 6-tab dashboard: Transfers, Alternatives, Feedback, Patients, Patterns, Insights. |

> **Tip**: Use the **module switcher** (⬡ AYUVANT dropdown) in the top-left corner of any module to navigate between Parts 1, 2, and 3 seamlessly.

### Step 3: Try These Flows

1. **Add a medicine batch** (Part 1) → **Sell it with a zone** (Part 2) → **Watch the ML model learn** (Part 2) → **Ask the AI when you'll run out** (Part 2).
2. **Search for a medicine** (Part 3, Alternatives tab) → **See generic substitutes ranked by salt match** → **Sell a substitute** → **Fill the feedback form** → **See AI learning update**.
3. **Register a patient** (Part 3, Patients tab) → **Record purchases** → **View their health timeline** → **Check if they're flagged as Escalating**.

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | Pure HTML5, Vanilla JavaScript (ES6+), CSS3 |
| **ML Engine** | Custom in-browser prediction model (no external libraries) |
| **Data Layer** | Browser `localStorage` (fully offline, no server) |
| **Dataset** | Relational JSON master dataset with Node.js compiler |
| **Design** | Custom CSS design system with glassmorphism, neon glows, and micro-animations |
| **Fonts** | Google Fonts (Sora, Inter, Space Grotesk) |
| **Icons** | Material Icons Round |

---

## 📁 Repository Structure

```
ai-agents-hackathon-2026-detox/
├── README.md                          ← You are here
├── LICENSE                            ← MIT License
├── pharmacy_master_dataset.json       ← Master relational dataset
├── build/
│   └── transform-dataset.js           ← Dataset → JS compiler
├── context/                           ← Product specs & design docs
│   ├── project-overview.md
│   ├── design-system.md
│   ├── part1-core-platform/
│   │   ├── overview.md
│   │   └── feature-batch-entry.md
│   └── part2-ai-intelligence/
│       ├── overview.md
│       ├── feature-ai-qa.md
│       ├── feature-notifications.md
│       └── feature-zone-map.md
├── part1/                             ← Core Pharmacy Platform
│   ├── index.html
│   ├── index.css
│   └── app.js
├── part2/                             ← AI Intelligence & Zone Maps
│   ├── index.html
│   ├── index.css
│   └── app.js
└── part3/                             ← Smart Distribution & Patients
    ├── index.html
    ├── index.css
    ├── app.js
    ├── data/
    │   ├── clinical-intelligence.js
    │   └── medicines.js
    └── modules/
        ├── pharmacy-network.js
        ├── alternatives.js
        ├── feedback.js
        └── patient-tracker.js
```

---

## 👥 Team DETOX

Built with ❤️ for **HackIndia AI Agents Hackathon 2026**

| Member | Contact |
|--------|---------|
| **Anshul Prajapati** | anshulprajapati2220@gmail.com |
| **Disha** | Disha19j@gmail.com |

---

> *"The best time to stock a medicine is before anyone needs it."* — AYUVANT
]]>
