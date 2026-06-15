# 🏥 AYUVANT — AI-Powered Smart Pharmacy & Healthcare Supply Ecosystem

Welcome to the official repository for team **DETOX** at **HackIndia AI Agents Hackathon 2026**. 

**AYUVANT** is an AI-powered smart pharmacy and healthcare supply ecosystem designed to solve the critical challenges of medicine distribution, stockouts, demand forecasting, and patient health tracking.

---

## 🌟 Key Features

### 📦 Part 1: Core Pharmacy Platform (Foundation)
* **Complete Medicine Database**: Store details such as brand names, categories, batches, expiry dates, and supplier information.
* **Inventory Management (CRUD)**: Create, read, update, delete, and search medicines efficiently.
* **Purchase & Sales Records**: Detailed ledger of all financial and inventory transactions.
* **Stock & Expiry Monitoring**: Smart alerts for low stock levels, overstocking, and near-expiry drugs.
* **Owner Dashboard**: Core analytical overview for pharmacy owners.

### 🧠 Part 2: AI Intelligence & Smart Supply Chain
* **Zone-Wise Analytics**: Real-time demand tracking with visual heatmaps to identify regional health trends.
* **AI Demand Prediction**: Machine learning algorithms forecasting demand based on historical sales.
* **News-Based Intelligence**: Sentiment and outbreak detection from local news, Google Trends, and government updates.
* **Smart Autonomous Ordering**: Auto-suggest and automatically compile orders matching predicted needs.
* **Supplier Management**: Bid comparison, delivery tracking, and logistics optimization.

### 🌐 Part 3: Smart Distribution & Patient Intelligence
* **Inter-Pharmacy Stock Transfer**: Peer-to-peer stock transfers between neighboring pharmacies based on proximity and AI surplus ranking.
* **Salt-Based Alternative Recommender**: Intelligent generic substitute matching using a weighted score of active salts, strength, dosage form, and price.
* **Pharmacist Feedback Engine**: AI-assisted post-sale verification and feedback analysis to learn user behavior and substitute success rates.
* **Patient Health Tracker**: Profile-based purchase history timelines, disease escalation alerts, and patient health trajectory forecasting.
* **Network-Wide Insights**: Interactive dashboards for repeat rates, batch tracking, and seasonality.

---

## 📁 Repository Structure

```text
ai-agents-hackathon-2026-detox/
├── LICENSE
├── README.md                      # This main document
├── pharmacy_master_dataset.json   # Seed dataset for pharmacy database
├── build/                         # Automation & dataset transformers
│   └── transform-dataset.js
├── context/                       # In-depth product spec files
│   ├── project-overview.md
│   ├── design-system.md
│   ├── part1-core-platform/
│   └── part2-ai-intelligence/
├── part1/                         # Part 1 Codebase (HTML, CSS, JS)
│   ├── index.html
│   ├── index.css
│   └── app.js
├── part2/                         # Part 2 Codebase (HTML, CSS, JS)
│   ├── index.html
│   ├── index.css
│   └── app.js
└── part3/                         # Part 3 Codebase (HTML, CSS, JS)
    ├── index.html
    ├── index.css
    ├── app.js
    ├── data/
    │   └── medicines.js
    └── modules/
        ├── pharmacy-network.js
        ├── alternatives.js
        ├── feedback.js
        └── patient-tracker.js
```

---

## 🛠️ Tech Stack & Design System

* **Frontend**: Pure HTML5, Vanilla JavaScript (ES6+), and CSS3. No framework dependencies for speed and deployment ease.
* **Styling & Theme**: **AYUVANT Futuristic Dark** theme utilizing:
  * Glassmorphism & backdrop-blur filters
  * Neon Accent Colors:
    * Primary: `#00E5FF` (Electric Cyan)
    * Secondary: `#7C4DFF` (Vibrant Purple)
    * Tertiary: `#00E676` (Neon Green)
  * Custom Typography (Sora + Inter + Space Grotesk via Google Fonts)
* **Data Layer**: Pure client-side persistence with `localStorage` (fully functional without a server).

---

## 🚀 Getting Started / How to Run

To run and test the application, clone the repository locally and open any of the parts in your web browser:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/HackIndiaXYZ/ai-agents-hackathon-2026-detox.git
   cd ai-agents-hackathon-2026-detox
   ```

2. **Run Part 1 (Core Platform)**:
   * Double-click `part1/index.html` or open it with your browser.

3. **Run Part 2 (AI Intelligence)**:
   * Double-click `part2/index.html` or open it with your browser.

4. **Run Part 3 (Smart Distribution & Patient Tracker)**:
   * Double-click `part3/index.html` or open it with your browser.

*Note: All three parts store their respective states in your browser's local storage (`localStorage`). To reset the simulated data at any time, clear your browser cache or run `localStorage.clear()` in the browser console.*

---

## 👥 The Team — DETOX
Submitting for the HackIndia AI Agents Hackathon 2026.
* **Anshul Prajapati**
* **Disha**
