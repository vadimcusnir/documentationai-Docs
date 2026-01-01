COD:: rol=arbore-arhitectură; activează=reguli non-negociabile pentru structură, identitate, valoare și adevăr executabil; când=când se creează, modifică sau evaluează orice parte din `/architecture`; TTL=permanent până la modificare explicită în `00_MANIFEST`/`01_CONSTITUTION`

## NON-NEGOCIABILE

Acest fișier definește reguli fundamentale pentru arborele `/architecture`. Ele se aplică înaintea oricărei alte convenții, documentații sau preferințe locale.

---

## 00–01: Constituția

- Fișierele `00_MANIFEST` și `01_CONSTITUTION` sunt constituția sistemului.
- Modificările asupra lor sunt rare, deliberate și documentate explicit în commit-uri.
- Orice abatere temporară trebuie marcată ca atare și planificată pentru rezolvare.

---

## 02–03: Motor de identitate și logică

- `02`–`03` definesc motorul de identitate și logica de bază a sistemului.
- Nicio decizie de arhitectură majoră nu poate contrazice explicit aceste fișiere.
- Modelele, rolurile și fluxurile cognitive derivă în mod constant din această zonă.

---

## 04: Semnătura publică

- `04` reprezintă semnătura publică: ce promite sistemul explicit în exterior.
- Orice interfață publică (API, interfață utilizator, documentație externă) trebuie să fie compatibilă cu această semnătură.
- Nu se expun în exterior comportamente care contrazic semnătura definită în `04`.

---

## 05–06: Valoare monetizată

- `05`–`06` descriu valoarea care poate fi monetizată și constrângerile ei.
- Orice funcționalitate care consumă timp sau energie de dezvoltare și operare trebuie să fie:
  - aliniată cu aceste definiții de valoare; sau
  - marcată explicit ca experiment și izolată.
- Nimic nu intră în „producție stabilă” dacă intră în conflict cu aceste fișiere.

---

## 07: Avantaj cognitiv

- `07` definește avantajul cognitiv al sistemului (de ce merită să existe).
- Designul de interfață, claritatea deciziilor și modul de prezentare a informației trebuie să maximizeze acest avantaj.
- Orice compromis care reduce avantajul cognitiv trebuie justificat și tratat ca excepție temporară, nu ca nouă regulă.

---

## 09: Carantină

- `09` este zonă de carantină: experimente, idei nevalidate, conținut cu statut incert.
- Nicio componentă critică nu poate depinde direct de elemente din `09`.
- `09` nu este invocat niciodată direct în fluxuri de execuție sau decizie stabile.
- Promovarea din `09` în zone stabile se face prin revizuire explicită și refactorizare clară.

---

## Verdict: `/architecture` ca unic „sursă executabilă de adevăr”

- Arborele `/architecture` este singura sursă executabilă de adevăr pentru:
  - identitate,
  - logică decizională,
  - promisiune publică,
  - valoare și avantaje.
- Codul, infrastructura și documentația derivă din `/architecture`, nu invers.
- Orice document sau implementare care contrazice `/architecture` este considerată în eroare până la actualizare sau revizuirea explicită a arhitecturii.

---

## Aplicare și conflicte

Când apare un conflict între:

- `/architecture` și cod;
- `/architecture` și altă documentație;
- două fișiere din `/architecture`,

se procedează astfel, în ordine:

1. **Se oprește propagarea conflictului**  
   Nu se adaugă cod nou bazat pe versiunea aflată în conflict.

2. **Se verifică ierarhia**  
   Se respectă prioritatea:
   - `00–01` peste tot.
   - `02–03` peste design local.
   - `04–07` peste preferințe de implementare.
   - `09` niciodată ca sursă normativă.

3. **Se aliniază implementarea la `/architecture`**  
   Codul și documentația externă se modifică pentru a se conforma.

4. **Dacă `/architecture` este depășită**  
   Se propune modificarea ei, cu argumente clare și impact explicit, și se face actualizarea controlată a fișierelor relevante.

Nimeni nu poate ignora aceste non-negociabile; singura cale legitimă de a le schimba este modificarea explicită a fișierelor din `/architecture` conform regulilor de mai sus.