# 🛡️ BizSafer Production Infrastructure
## Full-Stack Orchestration & SRE Lab

This repository documents the **production-first infrastructure architecture** used to operate the **BizSafer** platform.  
The system is designed and maintained by a **solo lead engineer** with an explicit focus on **reliability, security, and automated recovery**.

The environment supports **4+ live services** with multi-domain routing, high availability, and fail-safe deployment strategies.

---

## 🏗️ Repository Structure

```text
├── .github/workflows/
│   ├── deploy.yml        # Automated CI/CD pipeline with health gates
│   └── rollback.yml      # Manual emergency rollback workflow
├── frontend/             # React + Vite + Tailwind
│                          # Production path: /var/www/bizsafer
├── backend/              # Laravel + Filament + MySQL
│                          # Production path: /var/www/bizsafer-panel
├── nginx/
│   └── conf.d/
│       ├── frontend.conf # Nginx config for www.bizsafer.com
│       └── backend.conf  # Nginx config for panel.bizsafer.com
├── docker-compose.yml    # Multi-service container orchestration
└── README.md             # Master SRE & infrastructure documentation
```

---

## 🌐 Network & Domain Architecture

The BizSafer ecosystem is orchestrated behind a hardened **Nginx reverse proxy**, integrated with Cloudflare edge protection.

### Production Endpoints

- **Frontend Application**  
  https://www.bizsafer.com  
  *React + Vite + Node.js + Backend API*

- **Backend / Admin Panel**  
  https://panel.bizsafer.com  
  *PHP 8.3 + Laravel + Filament*

- **Public API**  
  https://panel.bizsafer.com/api/v1/

---

## 🛠️ Technical Stack

### Containerization & Orchestration
- Docker
- Docker Compose
- Private service networking
- Immutable image-based deployments

### CI/CD Automation
- GitHub Actions
- Zero-downtime deployments
- Automatic rollback on failed health checks

### Infrastructure
- DigitalOcean droplets
- SSH-based deployment
- Automated server hardening

### Edge Security
- Cloudflare WAF
- DDoS mitigation
- Origin IP cloaking
- Hardened Nginx security headers

---

## 🔄 Reliability & SRE Strategy

**Uptime Target:** 99.9%

### Automated Health Gates
- Health endpoint: `/api/v1/health`
- Traffic finalized only after successful checks

### Dual-Layer Rollback

**Automated Rollback**
- Instant reversion on failed deployments

**Manual Emergency Rollback**
- `workflow_dispatch` trigger
- Recovery time under 60 seconds

---

## 🚀 Deployment Workflow

1. **Build**  
   Parallel multi-stage Docker builds

2. **Audit**  
   Vulnerability scanning of Docker layers

3. **Deploy**  
   SSH-based deployment using GitHub Secrets

4. **Verification**  
   Production health checks and cleanup

---

## 👤 Ownership

**Lead Engineer:** Md. Kamruzzaman  
**Role:** Cloud & DevOps Engineer | SRE  
**Platform:** https://www.bizsafer.com

---

## 📌 Notes

- This is a real production system, not a demo
- Stability is prioritized over novelty
- Every automation path includes a failure escape hatch
- Security and recovery are first-class concerns
