# ⚙️ BizSafer Infrastructure  
## Production-Grade API Core (Backend)

This repository serves as a **credibility anchor**, documenting the production-grade backend infrastructure architecture used for the **BizSafer** platform. It is a **functional blueprint** designed to demonstrate industrial-grade **API reliability, data integrity, and automated orchestration**.

---

## 🏗️ Repository Structure (Backend-Focused)

```text
├── .github/workflows/
│   ├── deploy.yml         # Backend CI/CD pipeline with testing & health gates
│   └── rollback.yml       # Manual emergency rollback workflow
├── app/                   # Laravel 11 + Filament + PHP 8.3 source
├── docker/                # Multi-stage Dockerfiles for PHP-FPM
├── nginx/
│   └── backend.conf       # Nginx config for panel.bizsafer.com
├── docker-compose.yml     # Backend & database orchestration
└── README.md              # Infrastructure & API documentation
```

---

## 🌐 Network & Core Architecture
The BizSafer backend is delivered through a hardened **Nginx reverse proxy** and protected by **Cloudflare’s global edge network**.
- **Admin Panel & Dashboard**: https://panel.bizsafer.com (PHP 8.3 + Laravel 11 + Filament).
- **Public API Gateway**: Primary interface for frontend applications via `/api/v1/`.

## 🛠️ Technical Stack & Expertise
- **Containerization:** Multi-stage builds for optimized PHP-FPM images with Opcache enabled.
- **Orchestration:** Isolated MySQL 8.0 container with persistent volume management.
- **Security:** Cloudflare WAF rules for SQLi/XSS mitigation and hardened Nginx security headers (HSTS, CSP).

## 🔄 Reliability & SRE Strategy
**Target Availability:** 99.9%
- **Automated Health Gates:** Deployments are finalized only after successful probes of `/api/v1/health`.
- **Dual-Layer Rollback:** Includes instant automated reversion and a manual `workflow_dispatch` that restores production state in **under 60 seconds**.

---

## 👤 Ownership
- **Lead Cloud & DevOps Engineer (Solo):** Md. Kamruzzaman
- **Venture:** BizSafer | Independent Technical Venture
- **LinkedIn:** [https://www.linkedin.com/in/4kamruzzaman](https://www.linkedin.com/in/4kamruzzaman)
