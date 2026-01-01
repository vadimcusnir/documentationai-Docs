COD:: role=MEMORY_OS-ORDER.READ + activates=when-file-opened + invoked-when=cold-start-or-reset + TTL=stable

## Scop

Acest fișier definește **ordinea minimă și obligatorie de citire / invocare** pentru stratul MEMORY\_OS la cold-start sau reset.

## Ordine strictă de cold-start

La primul load, reset sau re-initializare explicită a MEMORY\_OS, sistemul TREBUIE să citească exact în această ordine:

1. `architecture/00_README_SYSTEM.md`  
2. `architecture/02_MEMORY_OS/ORDER.READ.md` (acest fișier)  
3. `architecture/02_MEMORY_OS/MCP-Σ_GRAMMAR.md`  

Niciun alt fișier NU este permis în faza de cold-start.

## Comportament permis cu cele 3 fișiere

Dacă TOATE cele 3 fișiere sunt disponibile și coerente, MEMORY\_OS TREBUIE să poată, exclusiv pe baza lor:

- să aplice toate limitele de memorie și protocol definite în `MCP-Σ_GRAMMAR.md`,
- să respecte subordonarea față de `architecture/00_README_SYSTEM.md`,
- să REFUZE orice acces la zone de carantină.

Orice comportament care necesită alte fișiere pentru a fi sigur este INTERZIS la cold-start.

## Reguli de carantină

Este absolut INTERZIS pentru MEMORY\_OS să invoce, citească sau să ceară orice resursă sub:

- `architecture/09_QUARANTINE/*`

Sunt interzise și orice aliasuri, montaje sau endpoint-uri MCP care rezolvă în arborele de carantină.

Dacă este solicitat accesul la carantină, MEMORY\_OS TREBUIE să răspundă printr-un REFUZ clar, bazat pe această politică ORDER.READ.

## Comportament la lipsa datelor

Dacă ORICARE dintre cele 3 fișiere obligatorii:

- `architecture/00_README_SYSTEM.md`
- `architecture/02_MEMORY_OS/ORDER.READ.md`
- `architecture/02_MEMORY_OS/MCP-Σ_GRAMMAR.md`

lipsește, este corupt sau inconsistent, atunci MEMORY\_OS TREBUIE să:

- intre într-un mod minim și sigur, și
- returneze `ERR.NO_DATA` sau să refuze executarea oricărei acțiuni care ar depăși informația disponibilă.