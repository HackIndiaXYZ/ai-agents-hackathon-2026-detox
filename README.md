# 🏥 AYUVANT — AI-Powered Smart Pharmacy & Healthcare Supply Ecosystem

Welcome to the official repository for team **DETOX** at the **HackIndia AI Agents Hackathon 2026**. 

**AYUVANT** is an intelligent, autonomous healthcare logistics and pharmacy management system. By combining local machine learning forecasting, news sentiment tracking, geospatial demand mapping, and peer-to-peer distribution, AYUVANT minimizes medication stockouts and optimizes localized healthcare supply chains.

---

## 🔮 Project Vision & Core Challenge

Traditional healthcare supply chains are reactive, leading to local medicine shortages (e.g., during seasonal disease outbreaks) or wasteful overstocking. 

**AYUVANT** resolves this by introducing an **intelligent, agentic dashboard** for pharmacists and distributors that predicts demands before they occur, routes excess stock from nearby pharmacies, recommends therapeutically equivalent generic alternatives, and tracks individual patient recovery patterns.

---

## 📁 System Architecture & Directory Layout

```text
ai-agents-hackathon-2026-detox/
├── LICENSE                        # Open-source MIT License
├── README.md                      # This main document
├── pharmacy_master_dataset.json   # Full relational dataset (diseases, symptoms, meds, salts)
├── build/                         # Dataset automation & parsing scripts
│   └── transform-dataset.js       # Node.js script mapping dataset to clinical JS databases
├── context/                       # In-depth product specification and design specifications
│   ├── project-overview.md        # Core vision and module maps
│   ├── design-system.md           # Tokens, palettes, typography guidelines
│   ├── part1-core-platform/       # Specifications for Part 1 features
│   │   ├── overview.md
│   │   └── feature-batch-entry.md
│   └── part2-ai-intelligence/     # Specifications for Part 2 AI & map features
│       ├── overview.md
│       ├── feature-ai-qa.md
│       ├── feature-notifications.md
│       └── feature-zone-map.md
├── part1/                         # Part 1 Codebase (Core operations foundation)
│   ├── index.html                 # UI layout for inventory & day-to-day CRUD
│   ├── index.css                  # UI theme & layout styling
│   └── app.js                     # CRUD logic & basic dashboard wiring
├── part2/                         # Part 2 Codebase (AI forecasting & zone map)
│   ├── index.html                 # Grid maps, AI Q&A panel, notification feeds
│   ├── index.css                  # Custom styling for grids & news feeds
│   └── app.js                     # Local ML prediction loop, self-improving logs, Q&A answers
└── part3/                         # Part 3 Codebase (Network transfers & patient intelligence)
    ├── index.html                 # 6-tab dashboard: Transfers, Alts, Feedback, Patients, Patterns, Insights
    ├── index.css                  # Full component layouts & dynamic render class states
    ├── app.js                     # System orchestrator, tab switching, and event binding
    ├── data/                      # Auto-generated clinical databases
    │   ├── clinical-intelligence.js
    │   └── medicines.js
    └── modules/                   # Decoupled domain models
        ├── pharmacy-network.js    # Stock transfer routing & proximity algorithms
        ├── alternatives.js        # Salt composition matching & price comparison engine
        ├── feedback.js            # Pharmacist feedback analytics and AI learning updates
        └── patient-tracker.js     # Patient registration, purchase timeline, & health trajectory flags
```

---

## 🚀 Architectural Modules & Deep-Dive Features

### 📦 Part 1: Core Pharmacy Platform (The Foundation)
The base operational layer for day-to-day pharmacy management:
* **Medicine Database**: Cataloging brand names, generic formulations, active ingredient salts, expiry dates, batch codes, and supplier data.
* **Inventory Dashboard & CRUD**: Standardized forms to add, edit, search, and delete medication stock.
* **Stock & Expiry Monitor**: Proactive monitoring that tags batches as "near-expiry" or "low-stock" based on thresholds.
* **Operational Logging**: Tracks sales transactions and incoming orders.

### 🧠 Part 2: AI Intelligence & Zone Map System
Extends Part 1 data into predictive and geospatial analytics:
* **Geospatial Zone Grid (2km × 2km)**:
  * The physical map is segmented into discrete squares representing a localized zone.
  * **Zone Coordinate Mapping Formula**:
    $$\text{Zone}_x = \lfloor \frac{\text{Longitude}}{\text{Grid Size}} \rfloor, \quad \text{Zone}_y = \lfloor \frac{\text{Latitude}}{\text{Grid Size}} \rfloor$$
  * Resolves any patient/purchaser GPS location into a zone identifier.
  * **Surrounding Grid View**: Renders the central chemist zone and up to 10 surrounding grids, color-coded by demand intensity to assist with delivery routes.
* **Local ML Demand Prediction**:
  * An offline, lightweight model running in the browser using historical sales data.
  * Recognizes demand peaks by **Month**, **Day of the week**, and **Zone**.
  * **Self-Improving Loop**: Learns dynamically from every recorded sale to refine weekly and monthly forecasts.
* **Outbreak News Intelligence**: Pulls simulated local news, Google Trends, and public health updates to trigger warning indicators if a specific disease surges in a zone.
* **AI Q&A Chatbot**: A pharmacist console with preset questions:
  1. *“Is there any medicine needed?”* -> Lists low stock and high-probability out-of-stock items.
  2. *“Which zone around requires which medicine?”* -> Breaks down regional requirements.
  3. *“What is the probability on when/after how many days a medicine is required?”* -> Estimates days remaining before stock exhaustion.

### 🌐 Part 3: Smart Distribution & Patient Tracker (Intelligence Layer)
Integrates multiple pharmacies into a collaborative network and tracks patient wellness:
* **Inter-Pharmacy Stock Transfer**:
  * Simulates a network of 6 neighboring pharmacies.
  * **Transfer Recommendation Scoring Algorithm**: Ranks peer pharmacies based on a weighted index of surplus stock, distance, and local demand.
  * **Transaction Lifecycle**: Renders and tracks requests through states: `Requested` ➔ `Approved` ➔ `In Transit` ➔ `Delivered`.
* **Salt-Based Alternative Recommendation Engine**:
  * Searches for generic alternatives if a brand-name drug is out of stock.
  * **Therapeutic Matching Score**: Weighted at 50% Active Salt Match, 20% Category, 15% Dosage Form, and 15% Strength.
  * **Price Indexing**: Shows if the substitute saves the patient money (MRP comparison).
* **Pharmacist Feedback Loops & AI Insights**:
  * A 6-question structured feedback system collects data after generic substitutions (efficacy rating, patient concerns, price sensitivity, pharmacist recommendation).
  * Auto-aggregates feedback into charts and gauge metrics.
* **Patient Health Tracker & Trajectory Detection**:
  * Renders a vertical timeline of a patient's purchases by PAT-ID.
  * **Wellness Trajectory Classification**: Tags patients as `Improving`, `Stable`, `Concerning`, or `Escalating`.
  * **Health Flags**: Raises alert flags for escalation (e.g., patient buying Paracetamol for days, then transitioning to strong Antibiotics) or high-frequency purchases.

---

## 🎨 Design System & Visual Aesthetics

AYUVANT is styled with the **AYUVANT Futuristic Dark** design system:
* **Glassmorphism**: Translucent frosted panels with $20\%$ opacity background overlays, thin semi-transparent $1\text{px}$ outlines, and `backdrop-blur: 12px`.
* **Futuristic Glows & Micro-Animations**:
  * **Primary (Electric Cyan, `#00E5FF`)**: Glow outline for input focus, active tabs, and AI highlights.
  * **Secondary (Vibrant Purple, `#7C4DFF`)**: For auxiliary actions, warning alerts, and secondary cards.
  * **Tertiary (Neon Green, `#00E676`)**: For successful operations, normal stock, and approved transfers.
* **Typography**: Sora (Headers), Inter (Body copy), and Space Grotesk (Labels, mono metrics, and status badges).
* **Layouts**: Responsive, mobile-first cards and views utilizing smooth cubic-bezier CSS transitions.

---

## 💾 Local Storage Key Mapping

The system operates completely client-side. The following keys are used in `localStorage`:

| Key Name | Module | Purpose |
|----------|--------|---------|
| `ayuvant_inventory` | Part 1 | Stores medicine database and current stock volumes |
| `ayuvant_sales_history` | Part 1/2 | Tracks sold transactions with timestamps and zone coordinates |
| `ayuvant_pharmacy_network` | Part 3 | Keeps track of neighboring pharmacies and their local inventories |
| `ayuvant_transfers` | Part 3 | Records active and completed inter-pharmacy transfers |
| `ayuvant_feedback` | Part 3 | Stores structured pharmacist post-substitution feedback |
| `ayuvant_patients` | Part 3 | Tracks registered patient profiles and timeline events |

---

## 🚀 How to Run & Verify

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/HackIndiaXYZ/ai-agents-hackathon-2026-detox.git
   cd ai-agents-hackathon-2026-detox
   ```

2. **Run the Core Pharmacy Platform (Part 1)**:
   * Open `part1/index.html` directly in any browser. Try adding a medicine batch.

3. **Run the AI forecasting and Zone Map dashboard (Part 2)**:
   * Open `part2/index.html` in a browser. Try recording a sale with zone parameters and look at the demand map or ask the AI questions.

4. **Run the Distribution, Substitutes, and Patient Tracker (Part 3)**:
   * Open `part3/index.html` in a browser. Navigate through the 6 tabs to test stock transfers, look up alternatives, register patient profiles, and view insights.

---

## 👥 Authors — Team DETOX
Proudly built for **HackIndia 2026**:
* **Anshul Prajapati** (anshulprajapati2220@gmail.com)
* **Disha** (Disha19j@gmail.com)
