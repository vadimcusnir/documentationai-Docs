COD:: 09_QUARANTINE/ORDER.READ TTL=30z

## 09_QUARANTINE / ORDER.READ

Zona `09_QUARANTINE` este un spațiu de izolare pentru artefacte, fluxuri și idei care nu au trecut încă printr-un review complet. Este deliberat periferică și nu intră în lanțul critic de execuție.

### Reguli dure

- Nu există niciun consumator critic care să depindă de `09_QUARANTINE`.
- Nicio unitate din `09_QUARANTINE` nu este invocată direct de alte module de arhitectură (de exemplu `architecture/02_MEMORY_OS`, `architecture/03_SYSTEMS_OS`, `architecture/05_VALUE_STACK`).
- Orice tentativă de integrare directă se tratează ca încălcare a `architecture/00_MANIFEST/NON_NEGOTIABLES`.

Orice referință directă de producție către `09_QUARANTINE` este interzisă. Singurele accesări permise sunt prin procese controlate de Operations sau system stewardship.

### Cine poate referenția 09_QUARANTINE

Sunt permise doar două tipuri de referințe, exclusiv în tooling intern sau documentație de lucru:

- Procese de `architecture/08_OPERATIONS` (de exemplu playbook-uri de migrare, audit, curățare).
- Procese de sistem meta (de exemplu revizuiri arhitecturale, experimente controlate, refactor offline).

Nu se admite:

- apel în lanțul de răspuns către utilizator
- dependență în `architecture/00_MANIFEST` sau `architecture/01_CONSTITUTION`
- folosire în căi critice de business (`architecture/05_VALUE_STACK`)

### Comportament pentru date lipsă

Orice flux din `09_QUARANTINE` care are nevoie de fișiere sau inputuri externe:

- nu încearcă să repare automat lipsurile
- nu introduce fallback-uri implicite

Când datele necesare nu există sau sunt inconsistente, se răspunde normalizat cu:

```text
ERR.NO_DATA
```

Acest cod este obligatoriu pentru a semnaliza clar că artefactul este incomplet și nu poate fi promovat.

### Proces minim de promovare din carantină

Un element poate fi mutat din `09_QUARANTINE` într-un nivel stabil doar după următorul proces explicit:

1. **Inventariere și scop clar**  
   Documentezi într-un fișier de tip `ORDER.READ` local ce problemă rezolvă și unde ar trebui să ajungă (de exemplu `architecture/02_MEMORY_OS` sau `architecture/03_SYSTEMS_OS`).

2. **Review arhitectural**  
   Un steward de arhitectură validează că:
   - nu introduce dependențe critice noi nejustificate
   - respectă principiile din `architecture/00_MANIFEST/NON_NEGOTIABLES` și `architecture/01_CONSTITUTION/RULE.TRUTH`.

3. **Refactor și normalizare erori**  
   Cureți codul sau structura, elimini specificul de experiment și te asiguri că erorile sunt normalizate (inclusiv `ERR.NO_DATA` acolo unde lipsesc inputuri).

4. **Integrare controlată**  
   Muți artefactul în noua locație țintă, actualizezi fișierele `ORDER.READ` relevante (atât în destinație, cât și aici, ca istoric) și doar apoi permiți referințe directe din module de producție.