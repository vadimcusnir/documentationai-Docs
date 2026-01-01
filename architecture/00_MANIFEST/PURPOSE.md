COD::ARCH.PURPOSE.MANIFEST

## Scop

Acest manifest definește de ce există directorul `/architecture` și cum trebuie folosit de către contributori și operatori.

`/architecture` este *sursa unică de adevăr executabil* pentru modul în care este gândit, guvernat și operat sistemul. Orice decizie structurală importantă trebuie să fie:

- explicită,
- versionată,
- legată de un artefact concret (fișier, regulă, procedură) în `/architecture`.

Dacă nu este scris aici, nu este încă o regulă de arhitectură.

## De ce există `/architecture`

- **Claritate**: separă deciziile de arhitectură de implementarea lor concretă în cod.
- **Coerență**: reduce contradicțiile dintre documentație, cod și practici de operare.
- **Trasabilitate**: permite urmărirea evoluției deciziilor și motivelor din spatele lor.
- **Operabilitate**: face arhitectura acționabilă pentru cei care operează sistemul zi de zi.

Directorul este organizat în straturi de guvernanță numerotate `00–09`, de la principii fundamentale la proceduri locale.

## Straturi de guvernanță 00–09

- `00_MANIFEST`: scopul general al arhitecturii, convenții globale și reguli meta despre cum se citește și se modifică `/architecture`.
- `01_CONSTITUTION`: principii non‑negociabile (adevăr, stil, voce) și limitele identității sistemului.
- `02_IDENTITY_ENGINE`: reguli pentru modelarea identității, a entităților de bază și a relațiilor dintre ele.
- `03_SYSTEMS_OS`: structura de operare a sistemului, subsisteme majore și modul lor de coordonare.
- `04_SEMIOTICS_BRAND`: convenții de semnificație, limbaj, ton și reprezentare de brand în toate interfețele.
- `05_VALUE_STACK`: definirea nivelelor de valoare livrată, capabilități cheie și priorități de investiție.
- `06_GROWTH_FUNNELS`: modele și constrângeri pentru funnel‑uri de creștere, conversie și retenție.
- `07_PROMPT_ENGINEERING`: pattern‑uri, standarde și limite pentru designul prompturilor și al interacțiunilor cu modele.
- `08_OPERATIONS`: proceduri de operare, monitorizare, alerte, runbooks, backup și recovery.
- `09_QUARANTINE`: excepții controlate, experimente riscante și conținut aflat în proces de integrare sau retragere.

## Cum folosești `/architecture` zi de zi

### Ca operator

- **Pentru a înțelege comportamentul așteptat**:
  - verifică mai întâi `01_CONSTITUTION`, `02_IDENTITY_ENGINE` și `03_SYSTEMS_OS` pentru principii și structură,
  - apoi consultă `05_VALUE_STACK`, `06_GROWTH_FUNNELS` și `07_PROMPT_ENGINEERING` pentru detalii pe zona afectată.
- **Pentru incidente și schimbări operaționale**:
  - folosește `08_OPERATIONS` pentru proceduri și runbooks,
  - documentează în `08_OPERATIONS` orice nouă lecție operațională stabilă.

### Ca contributor (dezvoltator / arhitect)

- **Înainte de a propune o schimbare**:
  - verifică `01_CONSTITUTION` pentru a te asigura că nu contravii principiilor de bază,
  - consultă `02_IDENTITY_ENGINE`, `03_SYSTEMS_OS` și `04_SEMIOTICS_BRAND` pentru politici și standarde relevante,
  - folosește `05_VALUE_STACK` și `06_GROWTH_FUNNELS` pentru a ancora schimbarea în valoare și impact.
- **La implementare**:
  - aliniază designul la regulile din `07_PROMPT_ENGINEERING` când lucrezi cu modele și interfețe conversaționale,
  - actualizează documentele relevante din `02–08` dacă schimbarea afectează identitatea, structura sau fluxurile.
- **La review**:
  - confirmă că documentele relevante din `/architecture` au fost actualizate înainte de a marca schimbarea ca finalizată.

### Reguli practice

- Nicio decizie arhitecturală semnificativă nu rămâne doar în PR‑uri, bilete sau discuții; ea trebuie ancorată în `/architecture`.
- Orice contradicție între cod și `/architecture` trebuie rezolvată explicit:
  - fie se actualizează codul pentru a respecta arhitectura,
  - fie se actualizează arhitectura, urmând procesul de guvernanță potrivit nivelului.

## TTL (Time‑to‑Live) și igienă

Pentru ca `/architecture` să rămână sursa unică de adevăr executabil, fiecare element trebuie să aibă un ciclu de viață clar.

- **Documente cu TTL scurt** (3–6 luni):
  - notițe de tranziție, planuri temporare, excepții aprobate,
  - trebuie marcate explicit cu data de expirare și revizuite sau șterse la termen.
- **Documente cu TTL mediu** (6–18 luni):
  - specificații de servicii în evoluție, pattern‑uri experimentale,
  - necesită o revizuire periodică planificată.
- **Documente cu TTL lung** (stabil)**:**
  - principii constituționale, politici de bază,
  - se schimbă rar și doar printr‑un proces de guvernanță formal.

Responsabilități:

- fiecare fișier din `/architecture` trebuie să aibă un responsabil implicit (owner de zonă sau de serviciu);
- la fiecare schimbare majoră, verifică dacă:
  - TTL‑ul este încă rezonabil,
  - referințele la alte straturi (`00–09`) sunt corecte și actuale.

Dacă găsești conținut expirat sau nealiniat, tratează‑l ca pe un bug de producție: deschide un ticket sau un PR și corectează arhitectura.