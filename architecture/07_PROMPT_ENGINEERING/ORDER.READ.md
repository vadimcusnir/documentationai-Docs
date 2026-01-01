COD:: architecture/07_PROMPT_ENGINEERING/ORDER.READ.md TTL=90z

## ORDER.READ :: 07_PROMPT_ENGINEERING

Secvență de citire și reguli dure pentru lucrul cu standardele de prompting din blocul `07_PROMPT_ENGINEERING`. Respectă întotdeauna ordinea și regulile de mai jos înainte de orice modificare.

### 1. Ordinea de citire aplicată

1. Citește manifestul global:
   1.1. `architecture/00_MANIFEST/ORDER.READ`  
   1.2. `architecture/00_MANIFEST/NON_NEGOTIABLES`
2. Citește constituția:
   2.1. `architecture/01_CONSTITUTION/RULE.TRUTH`  
   2.2. `architecture/01_CONSTITUTION/STYLE.NOEMOJI`  
   2.3. `architecture/01_CONSTITUTION/CORE.VOICE`
3. Citește regulile OS relevante:
   3.1. `architecture/02_MEMORY_OS/ORDER.READ`  
   3.2. `architecture/02_MEMORY_OS/MCP-Σ_GRAMMAR`  
   3.3. `architecture/02_MEMORY_OS/TTL_POLICY`  
   3.4. `architecture/02_MEMORY_OS/DECISION.LEDGER`
4. Citește fluxurile operaționale:
   4.1. `architecture/08_OPERATIONS/DELIVERY.CHAT`
5. Abia apoi citești și modifici documentele din `architecture/07_PROMPT_ENGINEERING`.

Nicio modificare de prompt sau de pattern nu este validă dacă această secvență nu a fost parcursă integral.

### 2. Reguli dure pentru orice prompt

1. Aplică fără excepție `RULE.TRUTH`: nu inventezi date, nu completezi goluri fără a le marca explicit ca incerte sau necunoscute.
2. Aplică fără excepție `STYLE.NOEMOJI`: nu folosești emoji în niciun prompt, răspuns de exemplu sau descriere de pattern.
3. Nu introduci niciun pattern nou de prompt (de sistem, de user sau de chain-of-thought) fără:
   - documentare dedicată în `architecture/07_PROMPT_ENGINEERING`; și
   - actualizarea referințelor din `architecture/00_MANIFEST/ORDER.READ` și, dacă este cazul, din `architecture/02_MEMORY_OS`.
4. Nu modifici semantica unui pattern existent fără să:
   - descrii clar schimbarea, motivul și impactul;  
   - sincronizezi exemplele de utilizare din toate fișierele care îl referențiază.
5. Nu invoci direct subsisteme rezervate și nu trimiți prompt-uri în carantină manual; folosești doar fluxurile și interfețele descrise în `architecture/02_MEMORY_OS` și `architecture/08_OPERATIONS/DELIVERY.CHAT`.
6. Orice prompt care ocolește `RULE.TRUTH` sau `STYLE.NOEMOJI` este invalid și trebuie corectat înainte de utilizare sau testare.

### 3. Procedură de actualizare pentru standardele de prompt

1. Confirmă zona arhitecturală:
   - voce și adevăr: `architecture/01_CONSTITUTION/*`  
   - memorie și persistență: `architecture/02_MEMORY_OS/*`  
   - operațiuni conversaționale: `architecture/08_OPERATIONS/DELIVERY.CHAT`
2. Identifică toate afirmațiile factuale din prompt și validează-le față de surse interne sau instructaj explicit. Dacă nu poți justifica o afirmație, marcheaz-o ca nevalidată sau trateaz-o ca `ERR.NO_DATA`.
3. Curăță stilul de orice element care încalcă `STYLE.NOEMOJI` sau `CORE.VOICE`. Înlocuiește simboluri sau abrevieri opace cu formulări clare.
4. Dacă introduci sau modifici un pattern:
   - descrie scopul, intrările, ieșirile și limitele de utilizare;  
   - oferă cel puțin un exemplu canonic de utilizare;  
   - actualizează toate fișierele de orchestrare care îl folosesc.
5. Dacă modificarea nu poate fi realizată fără presupuneri nejustificate, oprește modificarea și marchează situația conform `ERR.NO_DATA`.

### 4. Gestionarea lipsei de informație :: ERR.NO_DATA

În contextul prompt engineering, lipsa de informație este întotdeauna tratată explicit ca `ERR.NO_DATA`, nu prin ghicire sau completare tacită.

Când datele necesare nu sunt disponibile:

- Declari explicit starea `ERR.NO_DATA` în analiza ta internă sau în comentariile de lucru.
- Precizezi ce anume lipsește:
  - parametri de intrare (de exemplu, roluri, constrângeri de timp sau cost);  
  - surse de adevăr acceptate;  
  - exemple pozitive sau negative;  
  - dependențe de alte subsisteme.
- Enumeri datele minime necesare pentru a continua proiectarea prompt-ului în conformitate cu `RULE.TRUTH` și `STYLE.NOEMOJI`.
- Formulezi întrebări concrete către utilizator sau către proprietarul de sistem, astfel încât răspunsurile să poată închide `ERR.NO_DATA` fără ambiguități.

Un răspuns corect în prezența lipsei de informație conține, în mod tipic:

1. Semnalarea clară a stării `ERR.NO_DATA`.  
2. Listarea elementelor de informație lipsă.  
3. Cererea explicită a informațiilor necesare pentru a finaliza prompt-ul în limitele arhitecturii existente.