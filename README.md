<div align="center">

# গ্রAम-আरবাनisation
### *(Gram-Urbanisation)* — Smart villages, built from scraps.

**Greenathon 2K26 • The Assembly of God Church School, Park Street**
**Event: G-INVENT**
**Presented by APEEJAY SCHOOL, PARK STREET**

**PARTHIB BANERJEE • LAKSHANG DAS • ABHIMAT CHATTERJEE**

*“Innovate to Mitigate: Engineering a Cleaner Tomorrow”*

🌐 **Live site:** [gramurbanisation.vercel.app](https://gramurbanisation.vercel.app)

</div>

---

## 📖 About the project

**গ্রAम-আरবাनisation** (Gram-Urbanisation) is a working miniature smart village that shows how low-cost engineering can solve three everyday rural problems:

| Problem | Our module |
|---|---|
| 💧 Unfair water sharing and tanks running dry | **Water ATM** |
| 🗑️ Unsegregated waste that gets dumped or burned | **BIN-BIN** |
| ☀️ Solar panels losing power to bad angles and dust | **PanelFlower** |

The name blends **Bengali (গ্রাম, "village")**, **Hindi/Devanagari** and **English** — bringing urban-level smart technology to the *gram* (village). The whole structure is built mostly from **recycled cardboard, bottles and scrap**.

### Why it matters
- **600 million** Indians face high-to-extreme water stress, and about **2 lakh** die every year due to inadequate access to safe water *(NITI Aayog, Composite Water Management Index)*.
- Rural India generates an estimated **0.3–0.4 million tonnes** of solid waste per day, mostly with no bins, collection or segregation.
- Typical solar panels convert only **~15–20%** of sunlight, and dust and pollution can cut output in parts of India by **17–25%** *(Duke University & IIT Gandhinagar study)*.

---

## 🧩 The three modules

### 1. 💧 Water ATM — demand- and availability-based water distribution
A large main tank feeds two smaller house tanks through two pumps. The system checks how much water is **available**, listens to each house's **demand**, and shares water in equal, measured turns.

**How it works**
1. HC-SR04 ultrasonic sensor measures the water level in the main tank.
2. Each house raises a demand (button / Blynk app).
3. The ESP32 queues requests and alternates turns when both houses ask.
4. A relay switches the pump on to deliver an equal dose.
5. Low-water cut-off pauses distribution to protect the tank and pumps.
6. Live level, requests and status are monitored and controlled through the **Blynk IoT interface**.

**Components:** large main tank • 2 small house tanks • 2 × 3–9V pumps • 2 × single-channel relays • pipes • HC-SR04 ultrasonic sensor • ESP32 • request buttons • Blynk IoT interface

### 2. 🗑️ BIN-BIN — ESP32-CAM biodegradable / non-biodegradable sorting bin
A conveyor belt carries trash to BIN-BIN, where an ESP32-CAM classifies each item and a servo-driven flap drops it into the right compartment.

**How it works**
1. Conveyor belt carries the trash forward.
2. ESP32-CAM captures the item.
3. It is classified as **Biodegradable** or **Non-Biodegradable**.
4. A servo tilts the flap left or right.
5. The item drops into the correct compartment.

**Components:** conveyor belt • DC geared motor • L298N motor driver • ESP32-CAM • flap servo • two-compartment bin • recycled cardboard body

### 3. 🌻 PanelFlower — LDR sun-tracking, self-cleaning solar panel
Like a sunflower, PanelFlower turns to face the sun. Single-axis tracking like this can raise output by around **25–30%**, and an automatic wiper keeps dust off.

**How it works**
1. Two LDRs (separated by a divider) sense light on each side.
2. The Arduino Nano compares the left and right readings.
3. An MG90S servo tilts the panel towards the brighter side.
4. An SG90 servo sweeps a sponge wiper across the panel on a routine.

**Components:** 69 × 66 mm solar panel • 2 LDRs + divider • MG90S tilt servo • SG90 wiper servo • Arduino Nano • cardboard tower

---

## 🏗️ System architecture

```
 WATER ATM                  BIN-BIN                    PANELFLOWER
 ─────────                  ───────                    ───────────
 HC-SR04 ─┐                 Camera                     2 × LDR
 Buttons ─┤                   │                           │
          ▼                   ▼                           ▼
        ESP32 ──► Blynk     ESP32-CAM                 Arduino Nano
          │                   │                           │
   2 × Relays                 ├─► L298N ─► Conveyor       ├─► MG90S (tilt)
          │                   └─► Flap servo              └─► SG90 (wiper)
   2 × Pumps
```

**Three brains, one village.** Each module runs independently, so a fault in one never stops the others. Logic and motor power are kept on separate low-voltage supplies.

---

## 🛠️ Tech stack

| Area | Tools |
|---|---|
| Microcontrollers | ESP32, ESP32-CAM, Arduino Nano |
| IoT | Blynk IoT (ESP32 Wi-Fi) |
| Sensors | HC-SR04 ultrasonic, LDRs, camera |
| Actuators | Pumps via relays, MG90S & SG90 servos, DC geared motor via L298N |
| Programming | Arduino IDE (C/C++) |
| Website | Single-file HTML, CSS & JavaScript (inline SVG graphics), hosted on Vercel |
| Build materials | Recycled cardboard, bottles, scrap, hot glue |

---

## 🌍 UN Sustainable Development Goals

| SDG | How we contribute |
|---|---|
| **3** Good Health & Well-being | Safer water and less open burning of waste |
| **5** Gender Equality | Less time spent by women and girls fetching water |
| **6** Clean Water & Sanitation | Fair, measured, monitored water distribution |
| **7** Affordable & Clean Energy | Sun-tracking, self-cleaning solar panels |
| **9** Industry, Innovation & Infrastructure | Low-cost IoT and computer vision for villages |
| **10** Reduced Inequalities | Equal turns at the tank for every household |
| **11** Sustainable Cities & Communities | Smart rural development |
| **12** Responsible Consumption & Production | Segregation at source; model built from waste |
| **13** Climate Action | More solar output, less burnt waste |

---

## 🏘️ Real-world applications
- 🚰 Panchayat community water tanks
- 🏫 Village school waste corners
- 🏥 Solar-powered primary health centres
- 🏘️ Housing colonies and hostels
- 🍲 Mid-day meal kitchens
- 🌾 Small farms

---

## 🌐 Website

The project website is a **single `index.html` file** — all styles, scripts, graphics and team photos are embedded, so it needs no build step.

It includes interactive demos of all three modules, animated graphics, mascots (Boondi 💧, BIN-BIN 🤖, Sunny 🌻), SDG connections and team details.

### Run locally
Just open `index.html` in any browser.

### Deploy on Vercel
1. Push this repo to GitHub.
2. Go to [vercel.com](https://vercel.com) → **Add New → Project** → import the repo.
3. Keep the default settings and click **Deploy**.
4. Rename the project to `gramurbanisation` to get `gramurbanisation.vercel.app`.

### Repo structure
```
├── index.html   # complete website (single file)
└── README.md    # this file
```

---

## 👥 Team

| Member | Role |
|---|---|
| **Lakshang Das** | Introduction & Real-World Applications |
| **Parthib Banerjee** | Water ATM & BIN-BIN — Technical Lead |
| **Abhimat Chatterjee** | PanelFlower, SDGs & Impact |

### 🙏 Special thanks
- **Yusuf Nandarbarwala** — contributor
- Our teachers, friends and helpers at **Apeejay School, Park Street**
- The organisers of **Greenathon 2K26** at **The Assembly of God Church School, Park Street**

---

<div align="center">

*No villages were harmed in the making of this project. Several cardboard boxes were.* 📦

**Greenathon 2K26 • G-INVENT • Apeejay School, Park Street**

</div>
