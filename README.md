# DevOps Assignment – Reverse Proxy with Health Checks

## 🚀 Project Overview

This project demonstrates a simple DevOps setup using Docker Compose with:
- Nginx as a reverse proxy
- Two backend services:
  - **Service 1 (Golang)**
  - **Service 2 (Python Flask)**

Health checks are configured for both services. Nginx handles path-based routing to each backend.

---

## ⚙️ Setup Instructions

1. Clone the repository:
```bash
git clone https://github.com/AdityaGarasangi/DPDzero-Devops-Assignment.git
cd DPDzero-Devops-Assignment
```

2. Build and run:
```bash
 docker-compose up --build
```

3. Access services in your browser:
   * Go Service (Service 1/ping): `http://localhost:8080/service1/ping`
   * Go Service (Service 1/hello): `http://localhost:8080/service1/hello`
   * Python Service (Service 2/ping): `http://localhost:8080/service2/ping`
   * Python Service (Service 2/hello): `http://localhost:8080/service2/hello`

---

## 🌐 How Routing Works
 * Routing rules is defined in `nginx.conf`
 * Nginx listens on port 8080 and forwards requests based on the URL path:
    * `/service1/*` → routed to service_1 (Golang app on port 8001)
    * `/service2/*` → routed to service_2 (Python app on port 8002)
 * Nginx strips the path prefix using `proxy_pass`

## 🎯 Bonus Implemented
 * ✅ Health checks for both services via Docker:
    * Golang: http://localhost:8001/ping
    * Python: http://localhost:8002/ping
 * ✅ Logs of successful health check responses:
    * Python auto-logs `/ping` requests every 10s via health check.
    * Golang logs `/ping` only when explicitly requested (manual logging with `log.Println()`).
 * ✅ Clean, modular Docker setup
 * ✅ Reverse proxy via Nginx with path-based routing

---

## Logs
Logs showing both service_1 (Golang) and service_2 (Python) responding to `/ping` requests:
![logs](./screenshot/logs.png)
