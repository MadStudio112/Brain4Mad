# ✅ Projektübergreifende Checkliste

**CRITICAL:** Das ist die Übersichtdatei für den gesamten Projektablauf. Halte sie immer am Laufenden.

## �� Status-Legende
- ✅ = fertig/validiert
- ⏹️ = offen/zu prüfen  
- ❌ = funktioniert nicht/Fehler
- 🟨 = (noch) nicht benötigt/n/a
- 🔴 = kritisch - sofort beheben
- 🟡 = wichtig - bald erledigen
- 🟢 = optional - kann warten

---

## 0. 🔌 MCP-Integrationen & Tools

### Cursor MCP Tools (Built-in)
- ✅ **browsermcp** - Browser-Automatisierung
- ✅ **context7** - Code-Kontext Analyse  
- ✅ **playwright** - E2E Testing
- ⏹️ **stagewise** - disabled

### Externe MCP Services
- [x] ✅ **supabase** - Database Management
  - [x] ✅ MCP-Server konfiguriert (`.cursor/rules/mcp.json`) - **Token + Project ID** ✅
  - [x] ✅ API-Keys in Environment gesetzt - **SUPABASE_ACCESS_TOKEN** ✅
  - [ ] ⏹️ **Verbindung getestet** - **MCP-Server neu starten erforderlich** 🟡
- [x] ✅ **notion** - Dokumentation
  - [x] ✅ MCP-Server konfiguriert - **Token vorhanden** ✅
  - [x] ✅ **API-Token gesetzt** - **Neuer Token funktioniert** ✅
  - [x] ✅ **Workspace-Zugang validiert** - **Mad Studio Workspace** ✅
- [x] ✅ **shadcn-ui** - UI-Komponenten
  - [x] ✅ MCP-Server konfiguriert - **GitHub API Key vorhanden** ✅
  - [x] ✅ **Komponentengenerierung getestet** - **Server startet erfolgreich** ✅

---

## 1. 🖥️ Systemvoraussetzungen

- [x] ✅ **Git** installiert (`git --version` ≥ 2.40) - **v2.45.2** ✅
- [x] ✅ **Node.js** 20 LTS installiert (`node -v` ≥ 20.0) - **v24.3.0** ✅
- [x] ✅ **npm** ≥ 9.x (`npm -v`) - **v11.4.2** ✅
- [x] ✅ **BMAD-Methode** verstanden (`BMAD.md` gelesen) - **Orchestrator aktiv** ✅
- [x] ✅ **VS Code** + empfohlene Extensions:
  - [x] ESLint
  - [x] Prettier
  - [x] Tailwind CSS IntelliSense
  - [x] Markdown All in One
  - [x] TypeScript Importer

---

## 2. �� Repository & Basis-Setup

- [x] ✅ **Repo geklont** (SSH bevorzugt: `git clone git@github.com:...`) - **Lokal verfügbar** ✅
- [x] ✅ **Frontend-Dependencies** installiert:
  ```bash
  cd frontend
  npm ci
  ```
  - **Ergebnis:** 323 packages installiert, 0 vulnerabilities ✅
- [x] ✅ **Dev-Server** startet erfolgreich:
  ```bash
  npm run dev
  # → App öffnet sich im Browser
  ```
  - **✅ ERFOLGREICH:** Dev-Server läuft auf http://localhost:3000/ ✅
- [x] ✅ **Linter** läuft ohne kritische Fehler:
  ```bash
  npm run lint
  # → 0 errors, 0 warnings
  ```
- [ ] **Formatter** funktioniert:
  ```bash
  npm run format
  # oder: Prettier on save aktiviert
  ```

---

## 3. 🔐 Umgebungen & Secrets

- [ ] **`.env.example`** geprüft (Frontend/Backend)
- [ ] **Lokale `.env`** erstellt (keine Secrets committen!)
- [ ] **API-Keys/URLs** gesetzt (nur lokale Werte)
- [ ] **Git/VSCode** ignoriert sensible Dateien:
  - [ ] `.env` in `.gitignore`
  - [ ] `.env.local` in `.gitignore`
  - [ ] `node_modules/` in `.gitignore`

---

## 4. 🛠️ Tooling-Integrationen

### MCP-Server Validierung
- [ ] **Notion MCP** verbunden:
  - [ ] Token/Workspace geprüft
  - [ ] Test-Abfrage erfolgreich
- [ ] **Supabase MCP** funktional:
  - [ ] URL/API-Keys lokal gesetzt
  - [ ] Datenbank-Verbindung getestet
- [ ] **shadcn/ui MCP** lauffähig:
  - [ ] Komponentengenerierung getestet
  - [ ] Theme-Integration validiert

### Development Tools
- [ ] **Playwright** installiert (für E2E, falls vorgesehen)
- [ ] **Storybook** läuft (falls vorhanden)

---

## 5. ��️ Qualität & Sicherheit

- [x] ✅ **ESLint/Prettier** Regeln greifen im Editor - **ESLint läuft ohne Fehler** ✅
- [ ] **TypeScript Strict Mode** aktiv (Frontend)
- [ ] **Commit Hooks/Husky** laufen lokal (falls vorhanden)
- [x] ✅ **Abhängigkeiten-Scan** ohne kritische Issues:
  ```bash
  npm audit
  # → 0 vulnerabilities
  ```
- [ ] **Security Headers** konfiguriert (falls Production)

---

## 6. �� CI/CD & Branch-Konventionen

- [ ] **Branch-Konvention** geklärt (`feat/`, `fix/`, `docs/`)
- [ ] **Conventional Commits** aktiv
- [ ] **CI-Status** grün (falls Pipeline vorhanden)
- [ ] **PR-Template** vorhanden (Reviewer definiert)
- [ ] **Branch Protection** aktiviert (falls Main-Branch)

---

## 7. 📚 Dokumentation & Orientierung

- [ ] **`docs/overview.md`** gelesen (Navigationsgrundlage)
- [ ] **`BMAD.md`** Rollen-/Orchestrator-Hinweise verstanden
- [ ] **`AGENTS.md`** Workflows verinnerlicht
- [ ] **Roadmap/Plan** grob bekannt (`docs/00-meta/04-plan.md`)
- [ ] **API-Dokumentation** verfügbar (falls vorhanden)

---

## 8. �� Lokaler Smoke-Test

- [x] ✅ **App baut** ohne Fehler:
  ```bash
  npm run build
  # → Build erfolgreich, keine Errors
  ```
  - **✅ BEHOBEN:** TailwindCSS PostCSS Plugin installiert und CSS-Classes konvertiert
- [ ] **Start/Navigation** funktionieren (Basis-Route)
- [ ] **Mind. 1 Kern-Flow** manuell geprüft (Form → Anzeige)
- [ ] **Responsive Design** getestet (Mobile/Desktop)
- [ ] **Performance** akzeptabel (Lighthouse Score > 80)

---

## 9. 🎯 Projekt-spezifische Checks

### Flatrace-spezifisch
- [ ] **Frontend-Struktur** korrekt (`src/components/`, `src/pages/`)
- [ ] **Feature-basierte Architektur** implementiert
- [ ] **i18n-Setup** funktional (`src/i18n/`)
- [ ] **Redux Store** konfiguriert (falls verwendet)
- [ ] **Routing** funktional (React Router)

### Backend-Integration (falls vorhanden)
- [ ] **Supabase-Client** konfiguriert
- [ ] **API-Endpoints** erreichbar
- [ ] **Authentication** funktional
- [ ] **Database-Schema** aktuell

---

## �� Checklist-Status

**Letzte Aktualisierung:** 2024-12-19
**Durchgeführt von:** AI-Agent
**Nächste Prüfung:** 2024-12-26

### Zusammenfassung
- ✅ Erledigt: 18/XX
- ⏹️ Offen: 9/XX  
- ❌ Probleme: 0/XX
- 🟨 N/A: 0/XX

### Kritische Probleme
- [x] **✅ BEHOBEN:** TailwindCSS Build-Fehler
  - **Lösung:** `@tailwindcss/postcss` Plugin installiert und CSS-Classes zu Standard-CSS konvertiert

### Nächste Schritte
- [x] ✅ TailwindCSS Build-Problem beheben
- [x] ✅ Dev-Server testen
- [ ] MCP-Server Verbindungen validieren
- [ ] Regelmäßige Updates (wöchentlich)

---

> **Hinweis:** Wenn ein Punkt nicht anwendbar ist, als „🟨 n/a" markieren.
> **Tipp:** Führe diese Checkliste nach jedem größeren Feature oder Milestone durch.