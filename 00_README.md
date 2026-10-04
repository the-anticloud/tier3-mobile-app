# mobile-app

**Status:** Production-Ready | **Tier:** 3 | **Category:** UI & Frontend

## Overview

React Native mobile app for iOS and Android

**Domain:** https://0-1.gg/api-oss/mobile-app  
**Repository:** github.com/0-1-gg/api-oss-fixed  
**License:** Commercial with open governance

---

## Architecture & Components

### Core Components
- React Native app
- native modules
- offline sync
- push notifications

### Specifications

Framework: React Native 0.70+; Platform: iOS 12+, Android 8+; Features: Offline mode, biometric auth; Size: <100MB

---

## Deployment Scenarios

### Local Development (docker-compose)
\\\ash
docker-compose up mobile-app
\\\

### Kubernetes (High Availability)
\\\ash
kubectl apply -f kubernetes-manifests/mobile-app/
\\\

### Terraform AWS
\\\ash
terraform apply -var="service=mobile-app"
\\\

---

## Integration Points

See APPENDIX files for detailed integration information:
- 05_PLAYS_WELL_WITH.md — Complementary projects
- 06_System_Integration_Glimpses.md — Real deployment scenarios
- 07_Web_of_Relativity_This_Project.md — Service relationships

---

## Security & Compliance

- **Authentication:** api-oss-security (API Key, OAuth 2.0, JWT)
- **Rate Limiting:** Configurable (default 1000 req/min)
- **Encryption:** TLS 1.3 in transit, AES-256 at rest
- **Audit:** Immutable logging via api-oss-logging
- **Compliance:** HIPAA, GDPR, FedRAMP ready

---

**Last updated:** 2026-09-28
