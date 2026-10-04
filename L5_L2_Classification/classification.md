# L5 Narrow / L2 General Classification — mobile-app
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign mobile companion: local-first iOS/Android app for Anticloud status monitoring

## L5 Narrow
mobile-app specializes in sovereign mobile companion: local-first ios/android app for anticloud status monitoring within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means mobile-app is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B answers status queries from the mobile app: 'Is the AIOSS chain intact?' or 'What is current inference throughput?' — all via LAN WebSocket, no cloud relay.

## AIOSS Audit Relevance
Every mobile event (device ID + action + AIOSS chain query hash) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
GDPR Art. 25 (mobile app: no telemetry to app stores), CCPA
