COD:: 07_PROMPT_ENGINEERING.PURPOSE TTL=90z

## Scop

Această pagină definește rolul stratului `07_PROMPT_ENGINEERING` în arhitectură: stabilește convențiile, standardele și limitele pentru designul prompturilor și pentru modul în care sunt orchestrate interacțiunile cu modelele de limbaj, astfel încât sistemul să fie predictibil, sigur și ușor de extins.

Toate regulile din acest strat trebuie să fie coerente cu:

- `architecture/01_CONSTITUTION/RULE.TRUTH`
- `architecture/01_CONSTITUTION/STYLE.NOEMOJI`

și să respecte ordinea de citire și aplicare definită în `architecture/07_PROMPT_ENGINEERING/ORDER.READ`.

## Ce intră aici

- Definirea tipurilor de prompturi și a pattern-urilor canonice folosite în sistem (de exemplu: task, critic, evaluator).
- Convenții de structură pentru prompturi: ton, adresare, delimitatori, instrucțiuni metacognitive.
- Reguli pentru cum se exprimă constrângerile din `architecture/01_CONSTITUTION/RULE.TRUTH` în textul prompturilor.
- Reguli pentru asigurarea conformității cu `architecture/01_CONSTITUTION/STYLE.NOEMOJI` în toate prompturile.
- Standarde pentru clarificarea rolurilor în conversație (sistem, ghid, operator, utilizator) la nivel de prompt.
- Heuristici acceptate pentru dezambiguizare, recapitulare și verificare internă în cadrul unui schimb de mesaje.
- Pattern-uri de orchestrare a mai multor apeluri de model în același flux (de exemplu: draft → critic → refine), la nivel de design de prompt.
- Limite explicite pentru ceea ce are voie să promită sau să presupună un prompt în numele sistemului.

## Out of scope

- Implementarea tehnică a rutării, a chain-urilor sau a orchestration logic (se acoperă în alte straturi de sistem).
- Politici de memorie pe termen lung sau cache de conversație (vezi straturile din `architecture/02_MEMORY_OS`).
- Politici comerciale, de preț sau pachete de produs (vezi `architecture/05_VALUE_STACK/PRICING`).
- Detalii de UI/UX pentru interfețele de chat sau operator (se definesc în straturile de operațiuni, de exemplu `architecture/08_OPERATIONS/DELIVERY.CHAT`).
- Orice reguli care ar contrazice sau dilua constrângerile din `architecture/01_CONSTITUTION/RULE.TRUTH` sau `architecture/01_CONSTITUTION/STYLE.NOEMOJI`.