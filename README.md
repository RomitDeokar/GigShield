# 🛡️ GigShield
### AI-Powered Parametric Income Protection for Zepto/Blinkit Delivery Partners

> *"If your zone goes down, your income doesn't."*

## 1. Problem Statement

India's Q-Commerce delivery partners — working for platforms like **Zepto, Blinkit, and Swiggy Instamart** — operate in hyper-local micro-zones, completing 10-minute deliveries within a 2–3 km radius of dark stores. This tight operational model makes them uniquely vulnerable:

- A **single rainfall event** can shut down an entire zone for hours
- **Extreme heat or AQI spikes** trigger platform-level worker safety suspensions
- **Local curfews or dark store closures** instantly cut off their pickup points
- Workers lose **20–30% of monthly income** during such disruptions with zero safety net

Unlike food delivery workers who can operate across a wider area, Q-Commerce partners are **zone-locked** — if their micro-zone is disrupted, they cannot simply shift to another area. They bear the full financial loss with no recourse.

**Currently, no insurance product addresses this gap.**

---

## 2. Our Solution

**GigShield** is an AI-enabled parametric income protection platform built exclusively for Q-Commerce delivery partners. 

### How It's Different from Traditional Insurance

| Traditional Insurance | GigShield |
|---|---|
| Worker files a claim manually | Claims triggered automatically |
| Payout takes days/weeks | Payout in under 60 seconds |
| Coverage based on incident proof | Coverage based on objective data triggers |
| City-level weather assessment | **Micro-zone** (dark store radius) assessment |
| Fixed premiums | **AI-adjusted weekly premiums** per zone risk |

### Core Principle — Parametric Insurance

GigShield does **not** insure health, life, accidents, or vehicle damage. It insures **lost income** caused by external, objectively measurable disruptions. When a trigger threshold is breached and sustained, payouts happen automatically — no claim form, no adjuster, no waiting.

---

## 3. Persona & Scenarios

### Target Persona
**Q-Commerce Delivery Partner** — A gig worker employed by Zepto, Blinkit, or Swiggy Instamart, operating within a fixed micro-zone (typically a 2–3 km radius around a dark store), completing 15–25 deliveries per day, earning approximately ₹600–₹1,200/day.

### Real-World Scenarios

---

**Scenario 1 — Heavy Monsoon Rain (Most Common)**

> Ravi is a Zepto delivery partner operating in the HSR Layout zone, Bangalore. At 2 PM on a Tuesday, rainfall intensifies to 20mm/hr. After 10 minutes of sustained rain, GigShield's trigger monitor detects the breach. Ravi's GPS confirms he is inside the zone, and his app shows 2 completed deliveries in the last 30 minutes (he was actively working). His claim is auto-approved. ₹600 is credited to his UPI account before he even gets home.

---

**Scenario 2 — Hazardous AQI (Delhi Winter)**

> Priya works for Blinkit in the Dwarka zone, Delhi. In November, the AQI spikes to 340 (Hazardous). Blinkit suspends outdoor operations in the zone. GigShield detects the breach via WAQI API. Since Priya had been active that morning, her claim is auto-validated. She receives ₹600 for the lost afternoon shift — without filing anything.

---

**Scenario 3 — Dark Store Closure (Platform Signal)**

> Arjun's Zepto dark store in Koramangala unexpectedly closes for 4 hours due to a local strike. GigShield receives the simulated platform closure signal for Zone KOR-02. All 31 active workers in the zone who were logged in and active are auto-triggered for a payout. Zero manual intervention.

---

**Scenario 4 — Fraud Attempt (Blocked)**

> Vikram tries to claim a payout during a rainfall event, but his GPS shows he is 8 km outside the zone, and his app shows zero deliveries in the last 30 minutes. The fraud checker assigns him a score of 0.25 (below the 0.75 threshold). His claim is flagged for review and blocked from auto-payout.

---

## 4. Application Workflow

### Worker-Facing Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                        WORKER JOURNEY                           │
└─────────────────────────────────────────────────────────────────┘

1. ONBOARDING
   ├── Register with mobile number (OTP verification)
   ├── Select platform: Zepto / Blinkit / Swiggy Instamart
   ├── Zone auto-detected based on nearest dark store
   └── Basic profile: avg daily hours, shift pattern

        ↓

2. POLICY PURCHASE
   ├── AI calculates zone risk score (0.0 → 1.0)
   ├── Three weekly plans displayed with adjusted premiums:
   │     Basic Shield  — ₹49/week  — ₹300/disruption day
   │     Pro Shield    — ₹99/week  — ₹600/disruption day
   │     Elite Shield  — ₹149/week — ₹1,000/disruption day
   ├── Worker selects plan and pays via UPI/Razorpay
   └── Policy active for 7 days from Sunday midnight

        ↓

3. ACTIVE COVERAGE
   ├── Worker continues working normally
   ├── GigShield monitors zone every 5 minutes (background)
   └── Worker dashboard shows: active plan, zone risk, weekly earnings protected

        ↓

4. DISRUPTION DETECTED
   ├── Trigger monitor detects threshold breach in worker's zone
   ├── Waits for 10 minutes of sustained breach (false positive protection)
   ├── Fraud validation runs automatically:
   │     GPS inside zone radius (Haversine check)
   │     Activity score ≥ 1 delivery in last 30 min
   │     App logged in within 10 min of trigger
   │     No duplicate claim for this event
   └── Score ≥ 0.75 → AUTO APPROVED

        ↓

5. PAYOUT
   ├── Razorpay/UPI transfer initiated (mock in demo)
   ├── SMS notification sent: "₹600 credited — Rainfall disruption, HSR Zone"
   └── Worker dashboard updates: Protection Timeline + Weekly Protected total
```

### Admin / Insurer Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                       ADMIN DASHBOARD                           │
└─────────────────────────────────────────────────────────────────┘

Risk Map         → Leaflet + OSM map showing all zones
                   colored Red / Orange / Green by live risk level

Live Feed        → Real-time stream of disruption events and claims
                   "Zone HSR-01 | Rainfall 19mm/hr | 34 claims | ₹20,400"

Analytics        → Loss ratios, weekly payout trends, zone-wise breakdown

7-Day Forecast   → Predicted disruption risk per zone for next 7 days
                   (rolling average from 90-day historical data)

Risk Simulator   → Sliders for Rainfall / AQI / Active Workers
                   → Live output: Affected Workers | Estimated Payout | Loss Ratio

Fraud Console    → Flagged claims with per-check explainability
                   
```

---

## 5. Weekly Premium Model

### Why Weekly?

Zepto/Blinkit partners operate week-to-week — they receive platform payouts weekly, their active zones can change weekly, and their financial planning horizon is a single week. A weekly premium model aligns directly with how they think about money.

### Pricing Structure

| Plan | Weekly Premium | Max Payout/Day | Coverage Hours |
|---|---|---|---|
| Basic Shield | ₹49/week | ₹300 | 6 hrs/day |
| Pro Shield | ₹99/week | ₹600 | 10 hrs/day |
| Elite Shield | ₹149/week | ₹1,000 | 14 hrs/day |

### AI-Adjusted Dynamic Pricing

The base premium is adjusted ±30% by the AI risk model based on zone-level features:

```
Final Premium = Base Premium × (1 + 0.3 × (risk_score − 0.5))

Examples:
  HSR Layout, Bangalore (flood-prone, high AQI history)
    risk_score = 0.8 → adjustment = +9% → Pro Shield = ₹108/week

  Whitefield, Bangalore (historically dry zone)
    risk_score = 0.2 → adjustment = −9% → Pro Shield = ₹90/week
```

**Risk Score Inputs** (fed to XGBoost model):
- Zone rainfall frequency over last 90 days
- Zone average AQI score
- Historical flood/waterlogging incidents
- Worker's average daily shift hours
- Current month (monsoon season weighting)

The AI-adjusted price is shown to the worker on the policy screen with full transparency: *"Your zone risk score: 0.74 — Premium adjusted to ₹108/week"*

---

## 6. Parametric Triggers

> **These are Q-Commerce specific triggers.** Unlike food delivery, Zepto/Blinkit workers are zone-locked. Even one of these triggers halts ALL deliveries in the affected micro-zone.

### Trigger Table

| Trigger | Parameter | Data Source | Threshold | Sustained? |
|---|---|---|---|---|
| Heavy Rain | Rainfall mm/hr | OpenWeatherMap API | > 15 mm/hr | 10 minutes |
| Extreme Heat | Temperature °C | OpenWeatherMap API | > 43°C | 10 minutes |
| Severe AQI | Air Quality Index | WAQI API (free) | > 300 (Hazardous) | 10 minutes |
| Flash Flood Alert | IMD-style alert | Mocked JSON feed | Alert issued | Instant |
| Dark Store Closure | Platform signal | Simulated API | Closure flag | Instant |
| Local Curfew | Govt alert | Mocked event trigger | Curfew issued | Instant |

### False Positive Protection

Q-Commerce delivery windows are 10 minutes. A 2-minute rain spike should not trigger payouts. GigShield requires **10 minutes of sustained threshold breach** before any claim is created.

```
Poll every 5 minutes
First breach detected → start timer
If breach persists at next poll (10 min elapsed) → TRIGGER
If breach clears before 10 min → RESET (no claim)
```

This design decision shows real insurance thinking, not just API integration.

---

## 7. AI/ML Integration Plan

### Model 1 — Zone Risk Scorer (XGBoost)
- **Purpose:** Calculate zone-level risk score (0.0–1.0) to adjust weekly premiums
- **Features:** Rainfall history, AQI averages, flood incidents, seasonal patterns
- **Output:** Risk score visible to worker at policy purchase
- **Training data:** OpenWeatherMap historical data + synthetic zone disruption history

### Model 2 — Dynamic Premium Calculator
- **Purpose:** Apply risk score to base premium with ±30% adjustment range
- **Logic:** `final = base × (1 + 0.3 × (risk − 0.5))`
- **Shown to user:** Full transparency — risk score + adjustment % displayed

### Model 3 — Fraud Checker (Rule-Based + Scoring)
- **Purpose:** Validate every auto-claim before payout
- **Checks:**
  - GPS location validated via Haversine distance formula against zone radius
  - Activity score: deliveries completed in last 30 minutes (≥1 = active)
  - App session: last_seen timestamp within 10 minutes of trigger
  - Duplicate check: no existing claim for this worker + event ID
- **Score:** 4 checks → pass ≥ 3 of 4 (score ≥ 0.75) for auto-approval
- **Why explainable over black-box:** Every check shown in admin UI — judges and insurers see exactly why a claim was approved or flagged

### Model 4 — 7-Day Zone Risk Predictor
- **Purpose:** Admin dashboard shows next 7 days disruption forecast per zone
- **Method:** 90-day rolling average of disruption events per day-of-week
- **Output:** Risk label (High / Medium / Low) + score per day
- **Example:** "HSR Layout — Thursday: High Risk (0.74) — Monsoon pattern"

---

## 8. Tech Stack

### Frontend
| Tech | Purpose |
|---|---|
| React.js + Tailwind CSS | Worker app + Admin dashboard |
| Leaflet + OpenStreetMap | Zone risk heatmap (free, no API key) |
| Recharts | Analytics charts and loss ratio graphs |

### Backend
| Tech | Purpose |
|---|---|
| Node.js + Express | REST APIs for all core operations |
| PostgreSQL | Workers, policies, claims, zones, payouts |
| node-cron | 5-minute trigger polling scheduler |

### AI / ML
| Tech | Purpose |
|---|---|
| Python + scikit-learn | Risk scoring, fraud validation logic |
| XGBoost | Dynamic premium calculation |
| pandas + numpy | Historical data processing + 7-day forecasting |

### External APIs
| API | Purpose | Cost |
|---|---|---|
| OpenWeatherMap | Live weather + rainfall data per zone lat/lng | Free tier |
| WAQI API | Live AQI per zone coordinates | Free tier |
| Razorpay Test Mode | Simulated UPI payouts to workers | Free sandbox |
| Twilio (trial) / Mock | SMS notification on payout | Free trial |

### Infrastructure
| Tech | Purpose |
|---|---|
| Render / Railway | Hosting backend + frontend | Free tier |
| GitHub | Version control + submission repo | Free |

### Platform Choice — Web
We chose a **web platform** (PWA-enabled) over native mobile because:
- Workers can access it on any Android browser without a Play Store install
- Faster to build and demo within the 6-week timeline
- PWA enables add-to-homescreen for a near-native experience
- Admin dashboard is best experienced on desktop/tablet

---

## 9. Business Viability

### Unit Economics (1,000 Workers — Bangalore)

```
Weekly Premium Pool:
  1,000 workers × ₹99 average = ₹99,000/week

Monsoon Season Disruptions (Jun–Sep):
  ~3 events/week × ~150 affected workers × ₹500 avg payout
  = ₹2,25,000/week in payouts
  Loss Ratio = 2.27  →  Requires reinsurance above 1.5x

Off-Season (Oct–May):
  ~0.8 events/week × ~40 affected workers × ₹500 avg payout
  = ₹16,000/week in payouts
  Loss Ratio = 0.16  →  Highly profitable

Annual Per-Worker Economics:
  Premium collected:  ₹99 × 52 weeks  = ₹5,148
  Average claims:     ~₹1,800/year
  Net margin:         ~65% off-season / reinsured in-season
```

### Sustainability Strategy
- **Dynamic surge pricing** during monsoon season (+40% premium uplift)
- **Reinsurance layer** covers loss ratios above 1.5x
- **Zone-level risk differentiation** prevents adverse selection (risky zones priced higher)
- **Fraud detection** targets <5% fraudulent claim rate

---

## 10. Team

| Name | Role |
|---|---|
| Rian K Sinu | Frontend + UX |
| Romit Deokar | AI/ML Engineering |
| Vandanapu Saidhiraj | Full Stack Developer |
| Pragalbh Rai | Backend + DevOps |
| Manmohan Singh | Database |

**University:** SRM University
**Track:** Q-Commerce / Instant Delivery

---

##  Submission Links

- **GitHub Repository:** *(this repo)*
- **Demo Video (2 min):** [Link to be added]
- **Figma Wireframes:** [Link to be added]

---
