COD:: /architecture/00_README_SYSTEM + canon + invoked on any architecture init / consult + TTL=permanent

## Canon

Acesta este README-ul canonic pentru `/architecture`.

- TTL: permanent.
- Nu se discută; se respectă.
- Orice schimbare se face numai prin amendament explicit, logat în `architecture/CHANGELOG.md` și înregistrat ca intrare `DECISION`.

## Guvernanță și ierarhie

- Structura `/architecture` este o ierarhie de guvernanță.
- Nivelele joase (00–01) domină nivelele înalte (02+).
- Dacă există conflict între fișiere, se rezolvă prin ierarhie, nu prin interpretare.

### Blocuri majore

- `00_MANIFEST`: scop, non-negociabile, ordine de citire.
- `01_CONSTITUTION`: voce, reguli de adevăr, stil.
- `02_MEMORY_OS`: reguli pentru memorie și date derivate din interacțiuni.
- `02_IDENTITY_ENGINE`: reguli pentru identitate, roluri și persona.

Separare dură:

- Tot ce ține de memorie, istoric conversațional, note, rezumate intră în `02_MEMORY_OS`.
- Tot ce ține de voce, rol stabil, identitate, persona, limite de comportament intră în `02_IDENTITY_ENGINE`.
- Nu se amestecă reguli de memorie în identitate și invers; dacă o regulă le atinge pe ambele, se împarte în două fișiere distincte.

## Regula „1 fișier = 1 decizie”

- 1 fișier de arhitectură = 1 decizie clară, invocabilă.
- Fără fișiere narative lungi; descrierile extinse merg în help-center sau guides.
- Dacă o decizie devine complexă, se fragmentează în mai multe fișiere de decizie, fiecare atomic.

## Puncte de intrare minime

La orice inițializare sau consultare a arhitecturii se citesc minim:

- `00_MANIFEST/PURPOSE.md`
- `00_MANIFEST/NON_NEGOTIABLES.md`
- `00_MANIFEST/ORDER.READ.md`
- `01_CONSTITUTION/CORE.VOICE.md`
- `01_CONSTITUTION/RULE.TRUTH.md`
- `01_CONSTITUTION/STYLE.NOEMOJI.md`

## 09_QUARANTINE

- `09_QUARANTINE` nu se invocă niciodată direct.
- Doar mecanismele de moderare / siguranță pot muta fișiere acolo.
- Orice regulă aflată în `09_QUARANTINE` este considerată suspendată până la o decizie explicită de reactivare.

## Validare brutală

Orice propunere de fișier nou sau amendament de arhitectură trebuie să treacă simultan următoarele teste:

- Poate fi rezumată într-o singură propoziție decizională clară (fără conjunctii inutile).
- Poate fi mapată imediat la un singur nivel și un singur bloc (de exemplu `02_MEMORY_OS`) fără ambiguitate.
- Are un mod de invocare clar: „când X se întâmplă, se aplică această decizie în Y pași”.

Dacă oricare dintre aceste teste eșuează, fișierul nu se publică în `/architecture`.

## Set minim de publicare

Pentru a publica orice schimbare în `/architecture`, trebuie să existe cel puțin:

- Un fișier de decizie atomic (1 fișier = 1 decizie).
- O intrare `DECISION` care descrie schimbarea și motivul.
- O intrare în `architecture/CHANGELOG.md` care indică:
  - fișierul modificat sau adăugat
  - data și autorul
  - link la `DECISION` relevant

Fără aceste elemente, schimbarea nu este considerată validă și nu trebuie invocată.