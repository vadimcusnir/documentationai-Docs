COD:: 02_IDENTITY_ENGINE + identity schema + TTL=90z  
INVOKE:: See architecture/00_MANIFEST/PURPOSE before editing this layer

## Scop

02_IDENTITY_ENGINE definește cum este reprezentată, verificată și propagată identitatea în tot sistemul:

- Contract unificat pentru cine vorbește, în numele cui și cu ce limite.
- Aliniere între identitatea internă (pentru memorie și sisteme) și identitatea expusă utilizatorilor.
- Separarea clară între roluri, permisiuni și contexte de operare.

## Ce este 02_IDENTITY_ENGINE

- Strat de guvernanță pentru identitate, nu pentru conținut.
- Locul unde este descris cum se formează un "actor" recunoscut de sistem.
- Legătura dintre constituție (valori, reguli) și orice instanță concretă care operează sub aceste reguli.

## What goes here

- Definiții de tipuri de identitate (ex: core system, operator, end-user, integrator).
- Reguli de comutare de identitate între contexte (ex: debug vs. production).
- Contracte pentru cum este serializată identitatea către alte straturi (Memory OS, Systems OS, Operations).
- Politici de alias, pseudonime și mascare identitate acolo unde e necesar.
- Ghiduri pentru contribuții care introduc noi roluri sau noi canale de interacțiune.

## Out of scope

- Politici de TTL și expirare memorie (apar în architecture/02_MEMORY_OS/TTL_POLICY).
- Detalii de implementare a autentificării sau SSO (apar în docs de produs, nu în /architecture).
- Logica de preț, billing sau planuri (vezi architecture/05_VALUE_STACK/PRICING).
- Detalii operaționale de livrare (vezi architecture/08_OPERATIONS/DELIVERY.CHAT).

## Legături cu alte straturi

- Se sprijină pe principiile din [architecture/01_CONSTITUTION/CORE.VOICE](architecture/01_CONSTITUTION/CORE.VOICE) și [architecture/01_CONSTITUTION/RULE.TRUTH](architecture/01_CONSTITUTION/RULE.TRUTH).
- Joacă rol de punte între valori și memorie, împreună cu [architecture/02_MEMORY_OS/ORDER.READ](architecture/02_MEMORY_OS/ORDER.READ).
- Influentează felul în care sistemul se prezintă în fața utilizatorilor descris în straturile Systems OS și Operations.

## Next documents

- Citește ordinea de aplicare și priorități pentru acest strat în `architecture/02_IDENTITY_ENGINE/ORDER.READ` (același folder, document separat).