# MQ6 Adressverwaltung – Projektkontext

## Anwendung
Browserbasierte Adressverwaltungs-Web-App als einzelne HTML-Datei.
Feldstruktur basiert auf dem T4-ERP-System der TETRA GmbH, Wachtberg.

## Dateien
- `Adressen_WebApp.html` – die Web-Anwendung (Vue 3 via CDN, Bootstrap 5)
- `Benutzerhandbuch_Adressen_WebApp.md` – Benutzerhandbuch (Deutsch)
- `Themenhandbuch_Adressen.txt` – konvertiertes Original-Handbuch der TETRA GmbH

## Tech Stack (aktuell)
- Vue 3 (CDN), Bootstrap 5, Bootstrap Icons
- Datenhaltung: `localStorage` (Key: `t4_adressen_v1`)
- Akzentfarbe: `#59191f`
- Keine Authentifizierung, kein Backend, kein Build-System

## Git & GitHub
- Repo: https://github.com/Henning1967/quada-adressen-webapp
- Arbeits-Branch: `feature/adressen-webapp`
- Offener PR: #1 (feat: T4-Adressverwaltung Web-App)
- Commits immer auf `feature/adressen-webapp`, nicht direkt auf `main`

## Geplante nächste Ausbaustufe (noch nicht begonnen)
- Frontend: Migration zu Vue 3 + Vite (npm-basiert)
- Backend: Node.js + Fastify + Prisma ORM
- Auth: Microsoft Entra ID SSO (MSAL.js)
- Datenbank: PostgreSQL
- Deployment: Azure oder Docker (On-Premises)
- Neues Repository anlegen für die Produktionsversion

## Arbeitsweise
- Vor größeren Änderungen immer `/plan` verwenden
- Commits auf Deutsch, beschreibend, mit Co-Authored-By Zeile
- Keine automatischen Pushes ohne Bestätigung
- Benutzerhandbuch bei Funktionsänderungen mitpflegen
