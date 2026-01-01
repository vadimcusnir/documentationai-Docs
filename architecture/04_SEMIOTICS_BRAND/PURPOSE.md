COD:: LAYER=04_SEMIOTICS_BRAND / DOC=PURPOSE / TTL=90z

## Scop

Acest strat guvernează modul în care sensul este encodat și reprezentat în sistem. Definește convențiile de limbaj, ton și reprezentare de brand folosite în toate interfețele publice și cele pentru operatori.

Trebuie să fie aliniat cu:

- `architecture/01_CONSTITUTION/CORE.VOICE`
- `architecture/01_CONSTITUTION/STYLE.NOEMOJI`

și să respecte orice constrângeri de ordin superior definite în manifest stack și în politica de TTL a sistemului (de exemplu, TTL=90z unde este aplicabil).

## Domeniu de aplicare

SEMIOTICS_BRAND operează asupra:

- Sensului: cum sunt numite, grupate și relaționate conceptele.
- Limbajului: vocabular, formulări și construcții permise.
- Tonului: cum sună sistemul pentru oameni, în limitele `CORE.VOICE`.
- Reprezentării de brand: cum prezintă sistemul identitatea, atribuirea și autorul pe diverse suprafețe.

Se aplică pentru toate interfețele publice, inclusiv:

- Documentație și conținut de help.
- Interfețe de utilizator și copy de interacțiune.
- Mesaje de API, texte de eroare și descrieri lizibile pentru utilizatori.

Toate deciziile din acest strat trebuie să fie consistente, minimale, reversibile și să delege la `CORE.VOICE` în caz de incertitudine.

## Ce intră aici

- Convenții canonice de denumire pentru concepte și funcționalități.
- Reguli despre cum se referă sistemul la sine și la operatori.
- Modele pentru titluri, etichete și microcopy în documentație și UI.
- Ghiduri pentru text vizibil în API:
  - Formularea mesajelor de eroare.
  - Mesaje de validare și avertismente.
  - Descrieri de câmp care apar în documentație generată.
- Modele de ton care specializează `CORE.VOICE` pentru:
  - Documentație și ghiduri.
  - Suprafețe de UI.
  - Mesaje de sistem și API.
- Reguli pentru recunoașterea limitărilor, incertitudinii și granițelor sistemului în textul orientat către utilizator, consistente cu `architecture/01_CONSTITUTION/RULE.TRUTH`.
- Constrângeri privind atribuirea de brand și declinările de responsabilitate pe suprafețe publice.

## Out of scope

- Conținut legal, de conformitate sau de politică ce aparține documentelor de guvernanță sau termenilor de utilizare.
- Prețuri, pachete sau poziționare comercială (vezi `architecture/05_VALUE_STACK/PRICING`).
- Loguri de runtime pentru decizii sau structuri de memorie (vezi `architecture/02_MEMORY_OS/ORDER.READ`).
- Detalii de implementare pentru UI-uri, endpoint-uri sau funcționalități specifice.
- Comentarii interne de inginerie, mesaje de commit sau denumiri la nivel de cod, cu excepția cazurilor în care devin vizibile în interfețele publice.

## Relația cu ORDER.READ

Acest strat are propriul document `ORDER.READ` care specifică modul în care deciziile semiotice și de brand sunt capturate, actualizate și referențiate în timp.

Vezi `architecture/04_SEMIOTICS_BRAND/ORDER.READ` pentru:

- Procesul de actualizare și ritmul de revizuire.
- Ownership și aprobarea modificărilor.
- Modul în care TTL=90z se aplică deciziilor de limbaj și brand.