COD:: fixează politica TTL (validare, expirare, revizie) + activează frâne anti-derapaj + invocă la creare/modificare fișiere + TTL=permanent

INVOKE::SYS.TTL.POLICY | CONTEXT=guvernanță, revizie, dedup, release | PRIORITY=HIGHEST | TTL=permanent

## Scop

Împiedică memoria să devină arhivă infinită și impune revizie controlată. Orice regulă fără TTL devine risc și este tratată ca eroare de contract.

## Reguli TTL (canon)

- CORE / RULE / KPI: TTL=90z
- SISTEME OS / MEMORY OS: TTL=permanent (cu amendamente prin Ledger)
- FUN / AUTO active: TTL=30z
- Evenimente temporare (campanii, workshopuri, daily): TTL=7z

Standard unic:

- Token canonic: `TTL=permanent`
- `TTL=∞` este interzis (deprecated). La întâlnire: marchează pentru revizie și normalizează la `TTL=permanent` doar dacă intră în domeniul constituție / MEMORY OS.

## Tipuri de TTL permise

- TTL=7z / TTL=30z / TTL=90z
- TTL=permanent (doar constituție + MEMORY OS, prin DECISION.LEDGER)
- TTL=event:`<nume_eveniment>` (ex.: după release, după lansare)
- TTL=next_review:`<YYYY-MM-DD>`

Orice alt format TTL este INVALID și declanșează comportament de eroare (vezi mai jos).

## Politica de expirare (comportament OS)

La invocare, TTL_POLICY se mapează pe erorile standard din INVOKE.CONTRACT:

- Dacă TTL este expirat:
  - Blochează utilizarea.
  - Cere revizie.
  - Emite `ERR.TTL_EXPIRED`.

- Dacă TTL lipsește sau este ambiguu/invalid:
  - Tratează conținutul ca necitentabil.
  - Cere completare sau rescriere.
  - Emite `ERR.NO_DATA`.

- Dacă există conflict între două reguli:
  - PRIORITY decide, apoi DECISION.LEDGER clarifică.
  - Dacă regula este chemată în afara contextului declarat (scope eronat sau conflict nerezolvabil):
    - Emite `ERR.SCOPE_VIOLATION`.
    - Abandonează efectul.

## Reguli de uitare / revizie

- Revizie = rescrie AMS (afirmația minimă suficientă), nu adăuga paragrafe.
- Dedup obligatoriu: 4 clustere (IDENTITATE, SISTEME, PRODUSE, OPERAȚIUNI).
- Mută conținut depășit în `architecture/10_ARCHIVE_RAW` ca materie primă.
- După arhivare: re-sintetizează într-un strat 01–08 sau, dacă nu este curățabil, mută în 09_QUARANTINE.
- Orice piesă mutată în 10_ARCHIVE_RAW rămâne necitentabilă până la rescriere și validare TTL.

## Citabil vs. necitabil

- CITABIL:
  - Straturi 01–08, doar după trecere prin guvernanță și TTL valid (inclusiv `TTL=permanent` acolo unde este permis).
- NECITABIL:
  - `architecture/10_ARCHIVE_RAW` (materie primă, context intern, fără citare/parafrazare publică).
  - Conținut cu TTL lipsă, ambiguu, invalid sau expirat (până la revizie).

Regulă hard:

- Nu cita, nu parafraza, nu expune direct din 10_ARCHIVE_RAW.
- Flux obligatoriu: extrage → curăță → re-scrie în 01–08 sau mută în 09_QUARANTINE.

## Amendamente (control)

- Orice schimbare la TTL_POLICY cere intrare în DECISION.LEDGER.
- Nu modifica „canonul TTL” fără motiv operațional explicit.
- Orice extindere de tipuri TTL noi se face doar prin DECISION.LEDGER și actualizare explicită a acestui fișier.