# ⚙️ BizSafer Infrastructure  
## Production-Grade API Core (Backend)

This repository serves as a **credibility anchor**, documenting the production-grade backend infrastructure architecture used for the **BizSafer** platform.

This is a **functional blueprint**, designed to demonstrate industrial-grade **API reliability, data integrity, and automated orchestration** for modern Laravel applications.

The backend is architected to provide high-performance administrative capabilities while maintaining strict security controls for data at rest and in transit.

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

### Orchestrated Endpoints

- **Admin Panel & Dashboard**  
  https://panel.bizsafer.com  
  *PHP 8.3 + Laravel 11 + Filament*

- **Public API Gateway**  
  Primary interface for frontend applications:  
  https://panel.bizsafer.com/api/v1/

---

## 🛠️ Technical Stack & Expertise

### Containerization & Orchestration
- Docker & Docker Compose
- Multi-stage builds for optimized PHP-FPM images (Opcache enabled)
- Isolated MySQL 8.0 container with persistent volume management

### CI/CD Automation
- GitHub Actions for automated testing, linting, and zero-downtime deployments
- Automated database migrations integrated into the deployment pipeline

### Performance & Security
- PHP 8.3 JIT and Opcache tuning for high-throughput API responses
- Cloudflare WAF rules for SQL Injection (SQLi) and XSS mitigation
- Hardened Nginx with security headers (HSTS, CSP, X-Content-Type-Options)

---

## 🔄 Reliability & SRE Strategy

**Target Availability:** 99.9%

### Automated Health Gates
Deployments are finalized only after successful probes of:

```
/api/v1/health
```

### Dual-Layer Rollback

**Automated Rollback**
- Instant reversion to the last stable Docker image if migrations or post-deployment checks fail

**Manual Emergency Rollback**
- GitHub Actions `workflow_dispatch`
- Human-led recovery of API and database state in under 60 seconds

---

## 🚀 Deployment Workflow

1. **Test & Audit (CI)**  
   Automated unit tests (`php artisan test`), static analysis, and dependency vulnerability scanning

2. **Build**  
   Parallel multi-stage Docker builds using PHP 8.3-FPM for optimized runtime execution

3. **Deploy (CD)**  
   SSH-based deployment using GitHub Secrets:
   - `PROD_HOST`
   - `PROD_USER`
   - `PROD_SSH_KEY`

4. **Verification**  
   Post-deployment API health probes  
   Automated cleanup of legacy containers

---

## 👤 Ownership

**Lead Engineer:** Md. Kamruzzaman  
**Role:** Cloud & DevOps Engineer | SRE  

LinkedIn: https://www.linkedin.com/in/4kamruzzaman

---

## 📌 Project Purpose

- Represents real production standards for backend API engineering
- Serves as a technical showcase of high-availability, secure server-side architectures
- Demonstrates reliable, automated database and API operations at scale
- Every automation path follows a strict **production-first** mindset
