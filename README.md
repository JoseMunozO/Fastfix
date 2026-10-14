# Fastfix — Felanmälan (Frontend)

> Felanmälan samlar alla fel i en fastighet på ett ställe. Hyresgästen anmäler, förvaltaren fördelar, teknikern åtgärdar, och alla ser status hela vägen.

Projekt i kursen **Producera och leverera mjukvara**. Det här repot innehåller **frontend** (React + TypeScript). Backend (Spring Boot + PostgreSQL) finns i ett separat repo.

**Status:** Sprint 0 — uppstart och planering.

## Problemet

I dag anmäls fel ofta via telefon, mejl eller lappar i trapphuset. Ärenden glöms bort eller hamnar hos fel person, hyresgästen vet inte om någon har sett anmälan och förvaltaren saknar överblick.

## Lösningen

- Ett ställe där alla felanmälningar samlas.
- Varje ärende har en tydlig status och en historik.
- Rätt tekniker får rätt ärende.
- Hyresgästen följer sitt ärende utan att behöva ringa.

## Roller

| Roll | Kan |
|------|-----|
| **Hyresgäst** | Skapa felanmälan, välja kategori och rum, ange om huvudnyckel får användas, följa status |
| **Tekniker** | Se tilldelade ärenden, ändra status, markera ärendet som åtgärdat |
| **Förvaltare** | Hantera fastigheter, lägenheter och användare, tilldela ärenden, stänga ärenden |

## Ärendets statusflöde

```
Ny → Tilldelad → Pågår ⇄ Väntar → Åtgärdad → Stängd
```

**Kategorier:** VVS, El, Vitvaror, Ventilation, Lås och dörrar, Övrigt
**Prioritet:** Akut, Hög, Normal, Låg

## MVP

- Inloggning med roller (JWT)
- Hantera fastigheter och lägenheter
- Skapa felanmälan
- Lista "mina ärenden" per roll
- Tilldela tekniker
- Ändra status med historik

Därefter (Bör): kommentarer, bilduppladdning, filter och sök, översikt för förvaltaren och deploy. Hela prioriteringen finns i [projektförslaget](docs/mvp/projektforslag-felanmalan.md).

## Teknik

| Del | Teknik |
|-----|--------|
| Frontend (det här repot) | React 19, TypeScript, Vite, oxlint |
| Backend (separat repo) | Spring Boot, Spring Security + JWT |
| Databas | PostgreSQL |
| CI | GitHub Actions: lint, typkontroll och bygge |

## Kom igång

Krav: [Node.js](https://nodejs.org/) 24 (samma version som CI).

```bash
git clone https://github.com/JoseMunozO/Fastfix.git
cd Fastfix
git checkout staging
npm install
npm run dev
```

Appen startar på http://localhost:5173.

| Kommando | Gör |
|----------|-----|
| `npm run dev` | Startar utvecklingsservern |
| `npm run lint` | Kör oxlint |
| `npm run typecheck` | Kontrollerar typer med TypeScript |
| `npm run build` | Bygger för produktion |
| `npm run preview` | Förhandsvisar produktionsbygget |

Kör `npm run lint && npm run typecheck && npm run build` innan du öppnar en PR — samma kontroller körs i CI.

## Arbetsflöde

```
feature/<namn>  ──PR──▶  staging  ──PR──▶  main
```

- Skapa alltid din gren från `staging`.
- Direkt push till `main` och `staging` är blockerad.
- Varje PR granskas av minst en annan person och CI måste vara grönt.
- Dokumentation skrivs på svenska, commit-meddelanden och PR:er på engelska.

Mer information i [CONTRIBUTING.md](docs/CONTRIBUTING.md).

## Sprintplan

| Vecka | Sprint | Fokus |
|-------|--------|-------|
| 1–2 | 0 | Uppstart: gruppkontrakt, DoD, MVP, databasschema, grundstruktur |
| 3 | 1 | Inloggning och grunddata |
| 4 | 2 | Skapa ärenden |
| 5 | 3 | Hela flödet: tilldelning, status och historik |
| 6 | 4 | Kommunikation: kommentarer, bilder, filter och sök |
| 7 | 5 | Översikt, tester och deploy |
| 8 | — | Leverans och muntlig redovisning |

## Dokumentation

| Dokument | Innehåll |
|----------|----------|
| [Projektförslag](docs/mvp/projektforslag-felanmalan.md) | Bakgrund, roller, user stories, databasschema och risker |
| [User stories](docs/mvp/user-stories.md) | Ordnad backlog med acceptanskriterier, prioritet och storlek (utkast) |
| [Frontendplan](docs/mvp/frontend-plan.md) | Vyer per roll, mappstruktur, plan per sprint och öppna frågor |
| [Definition of Done](docs/dod/definition-of-done.md) | När en user story räknas som klar (utkast) |
| [Mockups](docs/mockups/) | Skisser av gränssnittet |
| [CONTRIBUTING.md](docs/CONTRIBUTING.md) | Grenar, regler och kommandon |
