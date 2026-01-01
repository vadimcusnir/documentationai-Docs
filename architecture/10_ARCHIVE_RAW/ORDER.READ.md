COD:: architecture/10_ARCHIVE_RAW/ORDER.READ TTL=permanent

## Scop

`10_ARCHIVE_RAW` este stratul de arhivă pentru note brute, neverificate. Este exclus din orice flux orientat spre utilizator; servește doar pentru audit intern, reconstituiri și migrare controlată spre straturile superioare.

## Reguli de citire

1. Nu citi, nu cita și nu rezuma conținut din `10_ARCHIVE_RAW` în fluxuri orientate spre utilizator (chat, UI, livrabile).
2. Accesul este permis doar pentru:
   - audit intern;
   - migrare / refactor spre `09_QUARANTINE` sau `00-08`;
   - investigații tehnice documentate în `architecture/08_OPERATIONS` sau `architecture/02_MEMORY_OS`.
3. Orice utilizare directă în logica de decizie sau generare de răspunsuri către utilizator este interzisă.

## Convenții minime de fișier

Fiecare notă brută din `10_ARCHIVE_RAW` trebuie să înceapă cu un bloc de metadate minimale, în clar, pe primele linii, în ordinea:

- `source:` descriere scurtă a sursei (sistem, document, sesiune).
- `timestamp:` timp de colectare (ISO sau format stabilit în `architecture/02_MEMORY_OS/TTL_POLICY.md`).
- `provenance:` lanțul de proveniență (cum a ajuns aici, cine / ce l-a importat).
- `confidence:` evaluare scală documentată (de ex. low / medium / high sau 0-1, după ce este stabilit în `architecture/02_MEMORY_OS`).

Exemplu (schematic):

```text
source: ...
timestamp: ...
provenance: ...
confidence: ...
```

Restul conținutului brut urmează după acest bloc.

## Comportament obligatoriu la proveniență lipsă

Dacă un fișier sau o înregistrare din `10_ARCHIVE_RAW` nu are câmpul `provenance` sau acesta este gol / ambiguu:

- orice încercare de utilizare în fluxuri de sistem trebuie să fie tratată drept `ERR.NO_DATA`, conform `architecture/INVOKE.CONTRACT.md`;
- nu se permit inferențe ad-hoc ale provenienței direct din conținutul brut;
- nota trebuie fie completată printr-un proces de reconstrucție documentat, fie marcată explicit ca nereparabilă și lăsată în arhivă.

## Relația cu stratul de carantină (09_QUARANTINE)

- `09_QUARANTINE` rămâne strat de carantină; nu se invocă direct în fluxuri de producție.
- Niciun component critic nu poate depinde de `09_QUARANTINE` (vezi `architecture/00_MANIFEST/NON_NEGOTIABLES.md`).
- `10_ARCHIVE_RAW` este *în aval* de `09_QUARANTINE`: materialul de aici poate fi promovat doar după o etapă intermediară de curățare / refactor în `09_QUARANTINE` sau direct în straturi stabile, conform regulilor de mai jos.

## Proces de promovare

Promovarea datelor din `10_ARCHIVE_RAW` este întotdeauna explicită, documentată și reversibilă. Urmează acest flux, în ordine:

1. **Selecție și scop**

   - Identifică fișierul / grupul de fișiere țintă și scopul promovării (de ex. material de referință pentru `architecture/07_PROMPT_ENGINEERING` sau clarificare de politică pentru `architecture/01_CONSTITUTION`).
   - Notează intenția într-un jurnal de modificări (de ex. `architecture/CHANGELOG.md` sau un fișier local de lucru care va fi distilat ulterior).

2. **Verificare metadate minime**

   - Confirmă prezența și lizibilitatea câmpurilor: `source`, `timestamp`, `provenance`, `confidence`.
   - Dacă `provenance` lipsește sau este ambiguă:
     - tratează nota ca `ERR.NO_DATA` (vezi `architecture/INVOKE.CONTRACT.md`);
     - nu promova până când proveniența nu este reconstruită și documentată;
     - dacă reconstrucția e imposibilă, marchează nota drept nereutilizabilă și păstreaz-o doar ca istoric.

3. **Curățare și normalizare**

   - Elimină informații redundante, sensibile sau irelevante pentru stratul țintă.
   - Normalizează stilul și terminologia conform:
     - `architecture/01_CONSTITUTION/CORE.VOICE.md`;
     - `architecture/01_CONSTITUTION/STYLE.NOEMOJI.md`.
   - Clarifică orice ambiguități; dacă nu poți clarifica din surse sigure, marchează explicit ca necunoscut sau elimină din materialul care va fi promovat.

4. **Alegerea destinației**

   - Dacă materialul necesită încă verificări / revizuiri suplimentare, promite-l mai întâi în `architecture/09_QUARANTINE` (un fișier nou sau o secțiune marcată).
   - Dacă este deja curat, verificat și stabil:
     - promovează direct într-unul dintre straturile `architecture/00_MANIFEST` până la `architecture/08_OPERATIONS`, respectând structura existentă (de ex. PURPOSE, ORDER.READ, politici specializate).
   - Nu crea dependențe critice către `09_QUARANTINE`. Orice material esențial pentru runtime trebuie să ajungă într-un strat stabil.

5. **Documentarea promovării**

   - În noul fișier din stratul țintă, include o secțiune scurtă sau un comentariu care indică originea (referință către fișierele din `10_ARCHIVE_RAW`).
   - Actualizează, după caz:
     - `architecture/CHANGELOG.md` cu un rezumat al promovării;
     - orice registru de decizie relevant în `architecture/02_MEMORY_OS/DECISION.LEDGER.md`.

6. **Revizuire și închidere**

   - Asigură revizuirea de către cel puțin un alt contribuitor sau, pentru schimbări sensibile, aliniază cu regulile din `architecture/00_MANIFEST/ORDER.READ.md`.
   - Marchează în `10_ARCHIVE_RAW` faptul că materialul a fost promovat (de ex. adăugând o notă la finalul fișierului cu destinația și data), fără a șterge sursa brută.
   - Nu modifica retroactiv conținutul brut pentru a-l face să pară mai curat; orice corecție are loc în stratul țintă, nu în arhivă.

## Comportament în caz de erori de date

În orice flux intern care parcurge `10_ARCHIVE_RAW`:

- Ambiguitatea sau lipsa de precondiții trebuie mapată la `ERR.NO_DATA`, conform `architecture/INVOKE.CONTRACT.md`.
- Expirarea TTL (dacă este aplicabilă acestor note prin politici din `architecture/02_MEMORY_OS/TTL_POLICY.md`) se mapează la `ERR.TTL_EXPIRED`.
- Încălcările de scop (de ex. încercarea de a folosi direct notele brute în generarea de răspunsuri către utilizator) se mapează la `ERR.SCOPE_VIOLATION` și trebuie raportate în `architecture/08_OPERATIONS`.