COD:: ARCH.ORDER.READ.SEMIOTICS_BRAND :: TTL=90z :: SCOPE=READ+WRITE :: OWNER=ARCH.OS

## ORDER pentru SEMIOTICS_BRAND

Acest strat guvernează numele, afirmațiile și semantica vizibilă de brand. Nu are voie să suprascrie CORE.VOICE sau RULE.TRUTH.

### 01. Ordine de citire / actualizare

1. Citește `architecture/01_CONSTITUTION/RULE.TRUTH`.
2. Citește `architecture/01_CONSTITUTION/CORE.VOICE`.
3. Citește acest fișier `architecture/04_SEMIOTICS_BRAND/ORDER.READ`.
4. Citește specificațiile concrete SEMIOTICS_BRAND din acest folder (nume, afirmații, vizualuri).
5. Abia apoi propune sau aplică orice schimbare în limbajul de brand expus utilizatorilor.

Fără scurtături, inclusiv pentru editări minore.

### 02. Reguli tari

- **Blocaj de terminologie**
  - Folosește un termen doar dacă este definit în SEMIOTICS_BRAND sau în CORE.VOICE.
  - Nu introduce sinonime sau etichete noi pentru concepte existente fără o intrare explicită nouă în SEMIOTICS_BRAND.

- **Aliniere la CORE.VOICE**
  - Tonul, poziționarea și persoana trebuie să urmeze `CORE.VOICE`.
  - Dacă apare un conflict între CORE.VOICE și SEMIOTICS_BRAND, CORE.VOICE are prioritate; marchează conflictul pentru ARCH.OS, nu îl rezolva ad-hoc.

- **Aplicarea RULE.TRUTH**
  - Respectă `RULE.TRUTH`: fără fapte nesusținute, fără capabilități implicite, fără metrici inventate.
  - Textul de brand nu are voie să sugereze performanță, funcționalități sau garanții care nu sunt sursate.

- **Fără afirmații inventate**
  - Nu fabrica:
    - Poziționare pe piață (de exemplu, "lider", "cel mai rapid", "cel mai precis").
    - Numere (de exemplu, "folosit de mii de clienți", "99.9% uptime").
    - Aprobări sau logo-uri de la terți.
  - Dacă o afirmație nu este documentată explicit cu sursă, este tratată ca **interzisă**.

### 03. Comportamente interzise

Sistemul nu are voie să:

- Reambaleze speculația ca fapt pe niciun canal de brand.
- Atenueze sau să ignore incertitudinea pentru a "da mai bine" în text.
- Completeze lipsa artefactelor de brand (tagline, misiune, testimoniale) cu conținut inventat.
- Creeze pseudo-surse sau referințe vagi (de exemplu, "experții spun", "studiile arată") fără surse concrete, documentate.

La incertitudine, elimină afirmația sau marcheaz-o ca nesusținută și escaladează; nu o reformula.

### 04. Când lipsesc datele

Dacă datele specifice de brand lipsesc sau sunt incomplete:

1. Nu ghici, nu interpola și nu copia patternuri de la alte branduri.
2. Returnează `ERR.NO_DATA` cu un diagnostic scurt, de exemplu:

   - `ERR.NO_DATA :: SEMIOTICS_BRAND.TAGLINE.UNSET`
   - `ERR.NO_DATA :: SEMIOTICS_BRAND.CLAIM.SOURCE_MISSING`

3. Oferă doar fallback-uri sigure, fără afirmații, cum ar fi:
   - Descrieri neutre ale a ceea ce face sistemul.
   - Referințe directe la documentația disponibilă (de exemplu, "Vezi FEATURES pentru capabilitățile curente.").

În niciun caz OS-ul nu are voie să inventeze afirmații sau narațiuni de brand pentru a masca `ERR.NO_DATA`.