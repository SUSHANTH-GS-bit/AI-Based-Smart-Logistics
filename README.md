Al-Based Smart Logistics and Accessibility Intelligence Platform for North Eastern Region (NER)
Tagline: "Connecting Every Route. Predicting Every Risk. Delivering Beyond Boundaries."
Target Region: North Eastern States of India (Assam, Arunachal Pradesh, Meghalaya, Manipur, Mizoram, Nagaland, Tripura, Sikkim)

1. Executive Summary & Problem Context
The North Eastern Region (NER) of India experiences acute supply chain bottlenecks driven by:

Catastrophic Landslides & Mudflows: Fragile young Himalayan geology with slopes > 25° prone to sudden shear failures.
Monsoonal Deluges & Flash Floods: Rainfall exceeding 100-200mm in 24 hours inundating valley culverts and river approaches.
Micro-Climates & Cloud Cover: Rapid elevation changes (from 50m plains to 3,500m mountain passes) causing dense fog and zero visibility.
Connectivity Shadow Zones: Deep gorges and valleys lacking 4G/cellular signal, leaving drivers cut off from traditional navigation platforms.
High Inefficiencies: Up to 35% empty return trips (deadheading) due to lack of multi-modal freight aggregation.
NER-LINK is a technology prototype engineered to solve these challenges through an integrated system: AI Geotechnical Risk Prediction + Risk-Aware Dynamic GIS Routing + Multi-Modal Aggregation + Offline-First Sync + Bhashini Vernacular AI + SMS Fallback.

2. Key Capabilities & Architectural Innovations
1. Dynamic Accessibility & Risk-Aware Route Optimizer
Replaces naive shortest distance algorithms with the Risk-Aware Route Score:

Route Score
=
(
Landslide Safety
×
0.35
)
+
(
Terrain Gradient
×
0.25
)
+
(
IMD Weather Safety
×
0.20
)
+
(
Road Condition
×
0.20
)
Route Score=(Landslide Safety×0.35)+(Terrain Gradient×0.25)+(IMD Weather Safety×0.20)+(Road Condition×0.20)
Generates multi-corridor comparisons:

Route A (Direct Highway): E.g. NH-13 direct (186 km, 5h 20m, Safety: 22/100, CRITICAL Landslide Hazard).
Route B (Engineered Mountain Bypass - Recommended): Via Bomdila bypass & tunnel (204 km, 5h 45m, Safety: 87/100, Verified all-weather concrete).
Route C (Valley Riverine Arc): (221 km, 6h 10m, Safety: 94/100, Circuitous low-slope path).
2. AI Terrain Risk Prediction Engine
Modular machine learning architecture simulating XGBoost and Random Forest pipelines trained on Geological Survey of India (GSI) historical landslide inventories:

Inputs: Slope angle (°), Elevation (m), 24h Cumulative Rainfall (mm), Soil Saturation Index (%), River Proximity, and Historical Slides.
Outputs: Composite Landslide Probability, Flash Flood Inundation Probability, and 6h / 12h / 24h risk horizon forecasts.
3. Smart Return Load Optimization ("Empty Trip Elimination")
When a freight vehicle arrives or nears its destination, NER-LINK automatically scans an adjustable radius for available cargo requests.

E.g., arriving in Guwahati finds 3 return cargo requests within 18 km: 850 kg Agricultural Cold Produce bound for Shillong, yielding an extra ₹8,400 and eliminating empty fuel waste.
 4. Offline-First Architecture & SMS Fallback
Operates under three connectivity states: ONLINE,LIMITED,OFFLINE.
Caches road networks, downloaded maps, driver assignments, and offline forms locally using LocalStorage/IndexedDB.
Logs GPS pings and hazard reports offline with a real-time Pending Sync: X updates queue that synchronizes upon network restoration.
Simulates SMS Fallback dispatching GSM/USSD emergency rerouting alerts when internet connectivity is completely lost.
 5. Vernacular AI Assistant ("NER Voice Assist")
Designed around the Digital India Bhashini API architecture.
Full voice input, speech recognition, and Text-to-Speech (TTS) synthesis.
Supports 8 regional languages:
English
हिन्दी (Hindi)
অসমীয়া (Assamese)
বাংলা (Bengali)
মৈতৈলোন্ (Meitei / Manipuri)
Mizo ṭawng (Mizo)
Ka Ktien Khasi (Khasi)
Nagamese (Naga Creole)
6. Interactive SIH Emergency Demo Scenario
A 7-stage automated presentation runner demonstrating a realistic logistics emergency: NORMAL → WEATHER ALERT → RISK PREDICTION → ROAD BLOCKAGE → AI REROUTING → SAFE NAVIGATION → SMART RETURN LOAD.

3. Technology Stack
Backend: Python 3.13, FastAPI, Uvicorn, Pydantic, Starlette.
Frontend: Responsive Single-Page Application (SPA), Vanilla CSS (Tactical Dark Command Center with Glassmorphism, CSS tokens, micro-animations), Modular ES6 JavaScript.
Mapping & GIS: Leaflet.js 1.9.4, OpenStreetMap, CartoDB Dark Matter tiles.
Database Architecture: PostgreSQL 15+ with PostGIS spatial extensions, Redis caching schemas (backend/database/schema.sql).
NLP / Voice: Web Speech API (SpeechRecognition & SpeechSynthesis) + Bhashini Gateway adapter.
4. Project Structure
SIH HACKATHON/
├── backend/
│   ├── data/
│   │   └── ner_gis_data.py         # 8 NER states, highways, risk polygons, vehicles, weather
│   ├── database/
│   │   └── schema.sql              # Production PostgreSQL + PostGIS DDL schema
│   ├── services/
│   │   ├── ai_risk_engine.py       # ML XGBoost/Random Forest simulated risk engine
│   │   ├── route_optimizer.py      # Risk-Aware Dijkstra/A* multi-path calculator
│   │   ├── freight_matcher.py      # Multi-modal freight & Smart Return Load engine
│   │   ├── bhashini_service.py     # Vernacular NLP assistant & 8-language translator
│   │   └── offline_sync.py         # Offline reconciliation & batch ingestion
│   ├── main.py                     # FastAPI REST API Gateway & static router
│   └── schemas.py                  # Pydantic request & response validation models
├── frontend/
│   ├── css/
│   │   └── style.css               # Modern tactical command center design system
│   ├── js/
│   │   ├── map.js                  # Leaflet GIS engine, moving vehicles, hazard markers
│   │   ├── routing.js              # Route optimization, safety scoring, turn-by-turn nav
│   │   ├── ai_assistant.js         # Vernacular voice assist & Web Speech API TTS
│   │   ├── offline.js              # Offline-first queue & SMS fallback simulator
│   │   ├── sih_demo.js             # 7-step presentation scenario runner & timeline
│   │   └── app.js                  # State manager, role switcher, KPI animations
│   └── index.html                  # Single Page Application HTML shell
├── run_server.py                   # Single-command application launcher
└── README.md                       # Comprehensive documentation
5. Getting Started & Running Locally#
Prerequisites#
Python 3.10+ installed
Modern Web Browser (Chrome, Edge, Firefox)
Step 1: Install Dependencies
python -m pip install fastapi uvicorn pydantic
Step 2: Launch the Platform
python run_server.py
Step 3: Access the Application
Open your web browser and navigate to:

Interactive Command Platform: http://localhost:8000
Interactive Swagger REST API Docs: http://localhost:8000/docs
Alternative ReDoc API Specs: http://localhost:8000/redoc
6. Demonstration Guide for Hackathon Evaluators
When presenting to judges, follow this flow:

Brand & Mission:
Note the product identity: NER-LINK with its tagline "Connecting Every Route. Predicting Every Risk. Delivering Beyond Boundaries."
Switching Roles:
In the top right navbar, toggle between Driver, Vendor, and Admin to show role-tailored perspectives.
Launch the SIH Presentation Demo:
Click the prominent  Launch SIH Demo button in the top navbar.
Walk through the visual timeline:
Step 1 (Normal): Driver departs Guwahati for Tawang on NH-13.
Step 2 (Weather): IMD sensor detects 94.6mm rain deluge.
Step 3 (AI Risk): Landslide probability jumps to 88%.
Step 4 (Road Block): Landslide marker appears near Sela Pass.
Step 5 (AI Reroute): Dynamic Route Optimizer recommends Route B (Bomdila bypass).
Step 6 (Safe Path): Driver accepts reroute and navigation updates.
Step 7 (Return Cargo): Smart Return Load detects 3 nearby cargo loads in destination area (+₹8,400 revenue).
Live GIS Map Interaction:
Click on any moving vehicle marker to view driver details, payload, speed, and connectivity.
Click on the red landslide marker at Sela Pass to trigger the 1-click safe reroute.
Toggle GIS layers on and off in the top right floating overlay.
Vernacular AI Voice Assist:
Click the microphone icon in the bottom right corner.
Select a regional language (e.g. অসমীয়া (Assamese) or हिन्दी (Hindi)).
Click prompt chips like "Is the road to Tawang safe?" to hear synthetic voice TTS speech and view the translation.
Testing Offline Mode & SMS Fallback:
Click the green ONLINE pill in the top navbar to cycle to OFFLINE.
Observe the Offline Mode Activated banner and local cached operation.
Notice the simulated SMS Emergency Fallback alert received over cellular channels.
Cycle back to ONLINE to watch the automated synchronization reconciler update the server.
7. REST API Endpoints Overview#
Method	Endpoint	Description
GET	/api/health	System health check and component status
POST	/api/auth/login	Role-based authentication (Driver, Vendor, Admin)
GET	/api/map/gis-data	Full GIS spatial datasets for North Eastern states
GET	/api/vehicles/live	Moving vehicle telematics and GPS coordinates
POST	/api/route/optimize	Risk-Aware multi-corridor route calculator
POST	/api/risk/predict	AI Geotechnical Landslide & Flood Prediction
GET	/api/weather/current	IMD real-time weather stations in North East
GET	/api/cargo	Freight listings across regional cooperatives
POST	/api/cargo	Post new cargo and receive transport matches
POST	/api/matching/return-load	Geospatial return cargo search to prevent deadheading
POST	/api/assistant/query	Bhashini Vernacular AI query and translation
POST	/api/offline/sync	Ingest offline records after signal recovery
GET	/api/alerts	List active emergency alerts across regional highways
POST	/api/alerts	Admin broadcast emergency alert + SMS fallback
8. Platform Compliance Checklist#
 Dedicated branding: NER-LINK Dedicated branding: **NER-LINK** with authentic North Eastern context.
 Three verified user types: Driver, Vendor/Farmer/Trader, Admin/Logistics Operator.
 Leaflet + OpenStreetMap GIS covering Assam, Arunachal, Meghalaya, Manipur, Mizoram, Nagaland, Tripura, Sikkim.
 Risk-Aware Route Score formula prioritizing safety over naive shortest paths.
 Terrain Risk Prediction Engine analyzing slope, elevation, 24h rainfall, soil saturation, and 6h/12h/24h projections.
 Multi-modal freight aggregator covering trucks, mini trucks, shared freight, and Brahmaputra river barges (NW-2).
 Smart Return Load optimization discovering cargo near destination to eliminate empty return miles.
 Offline-First mode with LocalStorage caching, pending sync counter, and auto-sync.
 SMS Fallback simulation delivering mission-critical reroutes over GSM channels.
 Vernacular AI Assistant supporting 8 NER regional languages via Bhashini architecture + Web Speech API TTS.
 Interactive SIH Presentation Demo Scenario with visual timeline.
 PostgreSQL + PostGIS production database schema DDL script.
 Modern tactical command center design with high visual quality and responsiveness.
Tools & Technologies Used
Frontend: Web-based frontend for displaying logistics information, vehicle data, routes, incidents, GIS maps and ML-based results.
Backend: Python + FastAPI REST API backend.
Database: PostgreSQL for persistent storage of vehicles, locations, incidents and synchronization data.
ORM: SQLAlchemy for database models and communication between FastAPI and PostgreSQL.
GIS: GIS/GPS functionality for vehicle location tracking, route handling, geographical data and map-based logistics visualization.
Machine Learning (ML): ML service for risk prediction, using logistics/road-related data to support route and incident analysis.
Offline-First Sync: /api/sync for batch synchronization of offline records, including vehicle-location and incident data, with validation and idempotency/client-record handling.
CORS: FastAPI CORS middleware to allow the frontend to communicate with the backend.
Git & GitHub: Used for version control and collaboration; your backend work was merged with the team's GitHub repository.
Antigravity IDE: Used for development, testing and Git operations.
Python environment: Python 3.x with project dependencies maintained in requirements.txt.
