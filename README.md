# 🤖 morobotics.de — German Robotics Ecosystem Map

> A researcher-grade, interactive map of Germany's robotics companies, startups, scaleups, and research labs. Built to grow from a static prototype into a living intelligence platform for the robotics community.

[![Entities](https://img.shields.io/badge/Entities-25-blue)](companies.json)
[![Stage](https://img.shields.io/badge/Stage-1%20Prototype-orange)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)]()

---

## What Is This?

Germany has one of the world's deepest robotics ecosystems — spanning world-class research institutes (DLR, Fraunhofer, DFKI), globally recognized corporates (KUKA, Continental), and a fast-growing wave of AI-native startups and spinouts. But this ecosystem is fragmented across databases that weren't built for researchers: Crunchbase is investor-facing, LinkedIn is recruiter-facing, and academic databases ignore the industry side entirely.

It maps the full ecosystem using vocabulary and signals that researchers actually care about:

- Which companies trace back to which university labs?
- Who received EU Horizon or BMBF funding?
- What robotics subdisciplines (SLAM, manipulation, HRI) is each entity working in?
- Who is actively hiring right now?

[Website](https://morobotics.github.io/robotics-map/)

---

## Features

| Feature | Description |
|---|---|
| 🗺️ **Interactive Map** | Leaflet.js + OpenStreetMap, no API key required |
| 🔍 **Full-text Search** | Search across name, city, tech keywords, research domains |
| 🏷️ **Category Filters** | Industrial · AI · Logistics · Exoskeleton · Medical · Research Lab |
| 📊 **Stage Filters** | Startup · Scaleup · Corporate · Spinout · Research Lab |
| 💼 **Hiring Toggle** | Instantly surface entities actively recruiting |
| 🏛️ **Grant Tracking** | EU Horizon and BMBF grant data per entity |
| 🧬 **Lab Lineage** | Founding university lab traced for every spinout |
| 📦 **Marker Clustering** | Auto-clusters dense cities (Munich, Berlin, Stuttgart) |
| 📱 **Mobile Responsive** | Works on all screen sizes |
| ⚡ **Zero Dependencies** | Single HTML file, runs offline, no build step |

---

## Data Schema

Every entity in `companies.json` follows this structure:

```json
{
  "id": "franka-robotics",
  "name": "Franka Robotics",
  "city": "Munich",
  "state": "Bavaria",
  "lat": 48.1451,
  "lng": 11.5580,
  "category": "Industrial",
  "stage": "Spinout",
  "founded": 2017,
  "website": "https://franka.de",
  "tagline": "Collaborative robot arms with fine-grained force control for research & industry.",
  "tech_keywords": ["collaborative robots", "force control", "torque sensing", "ROS"],
  "research_domains": ["manipulation", "haptics", "learning from demonstration"],
  "founding_lab": "TU Munich — Chair of Robotics, Artificial Intelligence and Real-time Systems",
  "notable_people": ["Sami Haddadin (Founder)"],
  "partnerships": ["TU Munich", "DLR"],
  "eu_bmbf_grants": ["BMBF — Robotic Research Lab 2018"],
  "open_positions": true,
  "funding_stage": "Series B",
  "icon": "🤖"
}
```

### Field Reference

| Field | Type | Description |
|---|---|---|
| `id` | string | Unique URL-safe slug |
| `name` | string | Official entity name |
| `city` / `state` | string | Location within Germany |
| `lat` / `lng` | float | Coordinates for map marker |
| `category` | enum | `Industrial` `AI` `Logistics` `Exoskeleton` `Medical` `Research Lab` |
| `stage` | enum | `Startup` `Scaleup` `Corporate` `Spinout` `Research Lab` |
| `founded` | int | Year of founding |
| `website` | string | Full URL with https:// |
| `tagline` | string | One-sentence researcher-facing description |
| `tech_keywords` | string[] | Specific technologies used or developed |
| `research_domains` | string[] | Robotics subdisciplines (manipulation, SLAM, HRI, etc.) |
| `founding_lab` | string \| null | University lab that spawned the entity |
| `notable_people` | string[] | Key founders, directors, or researchers |
| `partnerships` | string[] | Notable academic and industry partners |
| `eu_bmbf_grants` | string[] | EU Horizon / BMBF project names and years |
| `open_positions` | boolean | Whether entity is actively hiring |
| `funding_stage` | string | Investment or funding status |
| `icon` | emoji | Map marker emoji |

---

## Adding New Entities

1. Open `companies.json` in any text editor
2. Copy an existing entry as a template
3. Fill in all fields — use `null` for unknown strings, `[]` for unknown arrays
4. Get coordinates: right-click any location on [Google Maps](https://maps.google.com) → click the coordinates shown
5. Save — the map reflects changes on refresh

### Best Sources for New Entities

| Source | What you'll find |
|---|---|
| [EXIST Startup Funding](https://www.exist.de) | University spinouts with EXIST grants |
| [BMBF Förderdatenbank](https://www.foerderdatenbank.de) | All BMBF-funded projects by keyword |
| [EU CORDIS](https://cordis.europa.eu) | EU Horizon robotics projects with German partners |
| [Handelsregister](https://www.handelsregister.de) | New GmbH registrations — search "Robotik" |
| [automatica Munich](https://automatica-munich.com) | Verified German robotics exhibitor lists |
| [Crunchbase](https://crunchbase.com) | Germany + Robotics filter for funded startups |
| arXiv `cs.RO` | German-affiliated papers → trace authors to their labs |
| [Semantic Scholar API](https://api.semanticscholar.org) | Free API for systematic paper/author search |

---

## Roadmap

### ✅ Stage 1 — Static but Smart (Current)
- [x] Hand-curated dataset of 25 German robotics entities
- [x] Interactive map with category, stage, and hiring filters
- [x] Researcher-relevant fields: founding lab, grants, research domains
- [x] Deployed on GitHub Pages

### 🔄 Stage 2 — Semi-Automated Pipeline
- [ ] Python scrapers for arXiv, EU CORDIS, and Handelsregister
- [ ] FastAPI backend serving data via REST
- [ ] SQLite database replacing the JSON file
- [ ] Weekly automated checks for new open positions

### 🧠 Stage 3 — AI Enrichment Layer
- [ ] LLM-powered company classification from website text
- [ ] Auto-extraction of tech keywords and research domains
- [ ] Weekly digest email for subscribed researchers
- [ ] Lab-to-spinout lineage graph visualization

### 🌐 Stage 4 — Community & Graph
- [ ] Researcher-contributed data with review workflow
- [ ] Academic citation network visualization
- [ ] Export API for bibliometric research
- [ ] Expand coverage to DACH region (Austria, Switzerland)

---

## Acknowledgements

- [Leaflet.js](https://leafletjs.com) — open source mapping
- [OpenStreetMap contributors](https://openstreetmap.org/copyright) — map tile data
- The German robotics research community — for building things worth mapping