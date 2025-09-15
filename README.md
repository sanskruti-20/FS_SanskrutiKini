# FS_SanskrutiKini
Problem statement - Student Commute Optimizer

# 🎓 Student Commute Optimizer

##  Problem Definition
Many students commute individually to the same school or college, often traveling along overlapping or similar routes.  
This results in:
- Higher **travel costs** (fuel, tickets, etc.)
- **Traffic congestion** and parking problems near campuses
- Increased **carbon emissions** from multiple vehicles
- Missed opportunities for **social connections**

The **Student Commute Optimizer** is designed to solve this problem by:
- Allowing students to enter their **home location and destination**
- Detecting **overlapping or nearby travel routes**
- Suggesting **carpool or ride-sharing matches**
- Providing an in-app **anonymous chat system** using unique aliases

---

##  Benefits to Students
-  Cost Savings** – Share rides and reduce daily commuting expenses  
-  Convenience** – Optimized route matches reduce stress and parking issues  
-  Eco-Friendly** – Fewer vehicles mean lower carbon footprint and traffic congestion  
-  Safety & Privacy** – Students remain anonymous through unique aliases until they choose to share more  
-  Community Building** – Encourages peer connections and social bonding during commutes  

---

## Technology Stack

Since this is a **full-stack project**, the following technologies can be used:

### Frontend (Student-facing)
- **React.js** (Web) or **React Native** (Mobile) – modern, responsive user interface  
- **Mapbox GL / Leaflet.js** – interactive maps, routes, and nearby students  
- **Tailwind CSS / Material UI** – clean and responsive UI design  
- **Socket.IO (client)** – real-time chat and updates  

---

### Backend (System operations)
- **Node.js (Express / Fastify)** or **Python (FastAPI / Django REST)** – REST APIs and WebSocket endpoints  
- **Socket.IO (server)** – for chat and live event communication  
- **PostgreSQL + PostGIS** – relational database with geospatial queries for route matching  
- **Redis** – caching, session management, and quick geo lookups  
- **Routing Engine** – OSRM (self-hosted) or Mapbox/Google Directions API for route calculations  

---

### Authentication & Privacy
- **JWT (JSON Web Tokens)** – secure login/session handling  
- **Unique Alias Service** – ensures anonymous, unique usernames for students  

---

### Deployment & DevOps
- **Docker & Docker Compose** – containerized microservices  
- **Kubernetes (K8s)** – orchestration and scalability (future phase)  
- **NGINX / API Gateway** – reverse proxy, load balancing, SSL termination  
- **CI/CD with GitHub Actions** – automated build, test, and deploy pipeline  
- **Cloud Options** – AWS (RDS for Postgres, Elasticache for Redis, EKS for K8s), GCP, or Heroku for MVP  

---

### Optional Enhancements
- **Push Notifications** – Firebase Cloud Messaging (for mobile alerts)  
- **User Verification** – email/OTP login for secure onboarding  

---
## 🏗️ System Architecture (High-Level)

          +-------------------+
          |   🌐 Frontend     |
          | React.js / RN     |
          | (Map + Chat UI)   |
          +---------+---------+
                    |
                    v
          +-------------------+
          |  API Gateway /    |
          |   NGINX / LB      |
          +--+---+---+---+---+
             |   |   |   |
 ------------+   |   |   +------------
             |   |   |
             v   v   v
    +--------+  +--------+   +--------+
    | Auth   |  | Trip   |   | Match  |
    | Service|  | Service|   | Service|
    +--------+  +--------+   +--------+
         |           |            |
         |           |            |
         v           v            v
    +--------------------------------+
    |    PostgreSQL + PostGIS        |
    | (Users, Trips, Routes, Matches)|
    +--------------------------------+
                  ^
                  |
           +-------------+
           |  Routing    |
           | Engine      |
           | (OSRM/Maps) |
           +-------------+

    +--------------------+
    |   Chat Service     |
    | (Socket.IO / WS)   |
    +--------------------+
             |
             v
     +-----------------+
     |   Redis Cache   |
     | (Geo, Sessions) |
     +-----------------+

---
<img width="1507" height="583" alt="system architecture" src="https://github.com/user-attachments/assets/67d96a94-58b0-4b4d-ab97-4f66fbb3c50d" />

