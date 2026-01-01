COD:: architecture/10_ARCHIVE_RAW/PURPOSE TTL=permanent

## PURPOSE

`10_ARCHIVE_RAW` este stratul de stocare pentru material brut, necuratat si neintegrat. Servește exclusiv ca sursa interna de lucru pentru analize, verificari si posibile promovari in straturile superioare. Conținutul de aici nu este niciodata tratat ca adevar canon, nici ca referinta stabila.

Arhiva raw este:
- sursa de material pentru rafinare ulterioara
- spatiu de parcare pentru date inainte de triere
- buffer pentru investigatii interne si audituri

## REGULI DURE

1. **Fara citare externa**

   - Niciun fragment din `10_ARCHIVE_RAW` nu poate fi citat direct in raspunsuri catre utilizatori.
   - Nu se permite parafrazarea continutului din arhiva raw ca sursa aparent sigura.
   - Orice continut folosit extern trebuie mai intai promovat intr-un strat 00–08 sau, daca este problematic, mutat in `09_QUARANTINE`.

2. **Fara dependinte pentru straturile 00–09**

   - Nicio regula, contract sau decizie din straturile `00_MANIFEST`–`09_QUARANTINE` nu poate avea `10_ARCHIVE_RAW` ca sursa primara.
   - Daca o informatie din arhiva raw devine critica, ea trebuie:
     - validata, si
     - rescrisa / integrata intr-un fisier dedicat din stratul corespunzator, apoi
     - referinta trebuie facuta doar catre noul fisier, nu catre arhiva raw.

3. **Fara invocare directa in fluxurile de raspuns**

   - Mecanismele care compun raspunsuri pentru utilizator nu au voie sa invoce direct continut din `10_ARCHIVE_RAW`.
   - Ambiguitatea asupra statutului unei surse din arhiva raw se trateaza conform `INVOKE.CONTRACT` ca `ERR.NO_DATA`, nu prin presupuneri sau interpolari.

4. **Promovare controlata**

   Orice promovare din `10_ARCHIVE_RAW` urmeaza acelasi traseu:

   1. Identificare material candidat.
   2. Verificare si curatare manuala / asistata.
   3. Decizie explicita de destinatie (ex: `02_MEMORY_OS`, `07_PROMPT_ENGINEERING`, `09_QUARANTINE`).
   4. Scrierea unui nou artefact in stratul tinta.
   5. Marcare in arhiva raw ca "consumat" sau "migrat" conform regulilor din `architecture/10_ARCHIVE_RAW/ORDER.READ`.

   Pana la finalizarea acestor pasi, continutul ramane **strict intern** si **neutilizabil extern**.

## RELATIA CU TTL SI ERORI

- Tot continutul din `10_ARCHIVE_RAW` foloseste implicit standardul `TTL=permanent`, aliniat cu politicile din `02_MEMORY_OS/TTL_POLICY`.
- Permanent nu inseamna "de incredere"; inseamna doar ca materialul nu este sters automat si ramane disponibil pentru audit si re-evaluare.
- Orice incertitudine privind acuratetea datelor din arhiva raw trebuie tratata ca lipsa de date, nu ca adevar partial: eroare canonica `ERR.NO_DATA` din `INVOKE.CONTRACT`.

## ORIENTARE SI ORDINE

Regulile operationale detaliate pentru acest strat (naming, mutari, status-uri, fluxuri de revizuire) sunt definite in:

- `architecture/10_ARCHIVE_RAW/ORDER.READ`