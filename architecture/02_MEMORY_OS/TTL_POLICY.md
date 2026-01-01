COD:: fixează politica TTL (validare, expirare, revizie) + activează frâne anti-derapaj + invocă la creare/modificare fișiere + TTL=permanent

INVOKE::SYS.TTL.POLICY | CONTEXT=guvernanță, revizie, dedup, release | PRIORITY=HIGHEST | TTL=permanent

## Scop
Împiedică memoria să devină arhivă infinită și impune revizie controlată. Orice regulă fără TTL devine risc.

## Reguli TTL (canon)
- CORE / RULE / KPI: TTL=90z
- SISTEME OS / MEMORY OS: TTL=permanent (cu amendamente prin Ledger)
- FUN / AUTO active: TTL=30z
- Evenimente temporare (campanii, workshopuri, daily): TTL=7z

## Tipuri de TTL permise
- TTL=7z / 30z / 90z
- TTL=permanent (doar constituție + memorie OS)
- TTL=event:<nume_eveniment> (ex: după release, după lansare)
- TTL=next_review:<YYYY-MM-DD>

## Politica de expirare (comportament OS)
La invocare:
- Dacă TTL este expirat → blochează utilizarea și cere revizie.
- Dacă TTL lipsește → tratează ca INVALID și cere completare.
- Dacă există conflict între două reguli → PRIORITY decide, apoi Ledger.

## Reguli de uitare / revizie
- Revizie = rescrie AMS (afirmația minimă suficientă), nu adăuga paragrafe.
- Dedup obligatoriu: 4 clustere (IDENTITATE, SISTEME, PRODUSE, OPERAȚIUNI).
- Mută conținut depășit în 10_ARCHIVE_RAW, apoi re-sintetizează într-un strat 01–08.

## Citabil vs. necitabil
- CITABIL: 01–08 (doar după trecere prin guvernanță și TTL valid)
- NECITABIL: 10_ARCHIVE_RAW (materie primă, context intern, fără citare/parafrazare publică)

Regulă hard:
- Nu cita, nu parafraza, nu expune direct din 10. Extrage → curăță → re-scrie în 01–08.

## Amendamente (control)
- Orice schimbare la TTL_POLICY cere intrare în DECISION.LEDGER.
- Nu modifica „canonul TTL” fără motiv operațional explicit.