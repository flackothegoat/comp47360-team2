# TEAM 2 Business Plan
### 1. App Name and One Sentence Description

App Name: Tablé

Description: A mobile and web-based marketplace application that connects consumers (diners) with nearby restaurants to offer real-time reservation availability based on live location data, transit modes and user preferences.

### 2. Problem: What, Who, Why

- What problem are you solving: Diners frequently waste time physically checking restaurant availability or navigating overcrowded areas, while restaurants simultaneously lose potential walk-in customers due to perceived busyness or lack of dynamic queue visibility.
    
- Who has this problem: Spontaneous urban diners, tourists navigating unfamiliar neighborhoods, and mobility-impaired individuals (EDI focus) who require guaranteed accessible and uncrowded seating environments.
    
- Why it is important: Existing platforms heavily prioritize reservations made days in advance. There is a significant market gap for a tool that empowers walk-in customers with real-time crowd predictions, reducing friction in urban dining and enhancing accessibility.
    

### 3. Solution: How

How you plan to address this problem: Tablé will ingest historical and dynamic OpenTable structured datasets alongside NYC Open Data. By training time-series machine learning models, the app will forecast peak dining hours and current busyness levels for specific restaurants. Furthermore, a Generative AI chatbot ("Dining Copilot") will be integrated to offer personalized recommendations based on real-time and predicted occupancy.

### 4. Target Users and Competitors

Target Users: Tech-savvy food enthusiasts, office workers seeking quick lunch spots, and users prioritizing sensory-friendly or physically accessible environments.

Competitors: Yelp Waitlist, Resy, and standard OpenTable applications. Tablé differentiates by predicting future walk-in busyness rather than just showing static reservation slots.

### 5. Architecture and Technology Stack

- Frontend: Web client built via React.js (Next.js for SSR); Mobile cross-platform client deployed via React Native (Expo framework).
    
- Backend API Gateway & Microservices: Node.js + Express handling api-gateway, reservations-service, and marketplace-service (flash deals). Live occupancy data streamed via Node.js WebSockets (realtime-service). ML confidence scores served asynchronously via Python FastAPI (ml-pipeline).
    
- Data Layer: Relational user and restaurant metadata structured in PostgreSQL (Google Cloud SQL managed instance); Real-time status caches held in Redis (Google Cloud Memorystore); Time-series historical trends logged in BigQuery / TimescaleDB.
    
- Deployment & Cloud Infrastructure: Containerized serverless environments running on Google Cloud Run or managed GKE Autopilot clusters to eliminate operations overhead for a 6-developer team.
    
- External APIs: Google Maps API (Geolocation & Transit ETA), Firebase (Cloud Messaging), and Stripe integration for simulated deposit charges.
    

### 6. Development Plan: Timeline, Milestones, Risks and Mitigations

Timeline & Milestones:

- Intro & Sprint 1: Design Thinking ideation, Google Stitch interface mockups, API definitions, and dataset exploration.
    
- Sprint 2: Deployment of Next.js and Expo framework skeletons, core Node.js routing setup, and database initialization.
    
- Sprint 3: Integration Phase (MVP). Connecting the FastAPI machine learning inference results in the active backend services.
    
- Sprint 4: Integration of the OpenAI API chatbot, usability evaluation loops, and system optimization.
    
- Sprint 5: Final artifact polish, public presentation demo preparation, and final research paper completion.
    

Risks and Mitigations:

- Risk 1: Technical complexity in orchestrating multiple Node.js microservices within a small team.  
    Mitigation: Implement clear JSON schema interface contracts and leverage monorepo structures early in Sprint 1.
    
- Risk 2: Inability to capture live production slots via real-time production endpoints.  
    Mitigation: Simulate dynamic traffic metrics by feeding historical OpenTable dataset batches sequentially.
    

  

### 7. Budget Specification

Monitoring budget performance remains the responsibility of the Product & UX Lead using daily timesheets. In alignment with real student project constraints, tasks have been decomposed into technical features with a mandatory 30% safety buffer for collaboration and debugging.

|Feature / Task|Time Est.<br><br>(hrs)|+ Buffer (30%)|Total Time|Hourly Rate<br><br>(€/hr)|Human Cost|Tools / Services|Service Cost|Total Cost|
|---|---|---|---|---|---|---|---|---|
|1. UI/UX Prototyping & Stitch Flow|8|+2.4 hrs|10.4 hrs|€30/hr|€312.00|Google Stitch|€0.00|€312.00|
|2. OpenTable EDA & FastAPI ML Pipeline|15|+4.5 hrs|19.5 hrs|€30/hr|€585.00|Scikit-learn / FastAPI|€0.00|€585.00|
|3. Node.js Express Gateway & Logic Setup|12|+3.6 hrs|15.6 hrs|€30/hr|€468.00|Node.js / ws module|€0.00|€468.00|
|4. PostgreSQL SQL & Time-series Config|8|+2.4 hrs|10.4 hrs|€30/hr|€312.00|GCP Cloud SQL & Cache|€20.00|€332.00|
|5. Web Framework Implementation (Next.js)|15|+4.5 hrs|19.5 hrs|€30/hr|€585.00|React.js / Next.js|€0.00|€585.00|
|6. Mobile App Integration (React Native)|18|+5.4 hrs|23.4 hrs|€30/hr|€702.00|Expo / Core Framework|€0.00|€702.00|
|7. Gen-AI & OpenAI Token Integration|10|+3.0 hrs|13.0 hrs|€30/hr|€390.00|OpenAI API Allocation|€20.00|€410.00|
|8. System Testing & Cross-Component Fixes|12|+3.6 hrs|15.6 hrs|€30/hr|€468.00|Jest / Automation tests|€0.00|€468.00|
|9. Cloud Run Deployment & Store Setup|6|+1.8 hrs|7.8 hrs|€30/hr|€234.00|Google Cloud Run / Stores|€134.00|€368.00|
|TOTAL|98|+29.4 hrs|127.4 hrs|-|€3,822.00|-|€174.00|€4,996.00|
