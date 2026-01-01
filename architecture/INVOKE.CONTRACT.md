COD::INVOKE.CONTRACT :: rol: definește contractul de invocare :: se activează: la orice apel acționabil :: invocat când: se emite o comandă cu efect :: TTL: permanent

## Semnătură de invocare

Fiecare invocare acționabilă TREBUIE să folosească semnătura canonică:

```text
INVOKE::<COD> | CONTEXT | PRIORITY | TTL
```

- `INVOKE::<COD>`: verbul de invocare plus identificatorul unic al comenzii.
- `CONTEXT`: descriere concretă, minimă, fără presupuneri implicite.
- `PRIORITY`: cheie total ordonată pentru rezolvarea conflictelor (valoarea mai mare câștigă).
- `TTL`: fereastra explicită de valabilitate, relativă sau absolută.

## Reguli de contract

1. **Unicitate efect**  
   - O invocare duce la un singur efect sau la o singură eroare standard.  
   - Fiecare `COD` corespunde exact unui efect bine definit.

2. **Determinism**  
   - Aceeași semnătură, în același stat, trebuie să producă întotdeauna același rezultat (efect sau eroare).

3. **Fără ambiguități semantice**  
   - `CONTEXT` trebuie să fie suficient de precis pentru ca doi cititori competenți să ajungă la aceeași interpretare.  
   - Nu se bazează pe implicite care nu sunt documentate.  
   - Dacă se detectează ambiguitate, se tratează ca `ERR.NO_DATA`, nu se ghicește.

4. **Rezolvare de conflicte prin PRIORITY, nu prin text**  
   - Când mai multe invocări active vizează un context care se suprapune, conflictul se rezolvă exclusiv prin `PRIORITY`.  
   - Textul, formularea argumentelor sau identitatea autorului NU pot suprascrie `PRIORITY`.  
   - Dacă `PRIORITY` este egală și efectele sunt incompatibile, se tratează ca `ERR.SCOPE_VIOLATION`.

5. **Aplicarea strictă a TTL**  
   - O invocare este valabilă numai cât timp `TTL` este în vigoare.  
   - Invocările expirate NU se execută și se normalizează la `ERR.TTL_EXPIRED`.  
   - Sistemele pot elimina anticipat invocările care este garantat că vor expira înainte de aplicare.

## Erori standard

Toate implementările de `INVOKE::<COD>` TREBUIE să normalizeze eșecul în următoarele erori:

- `ERR.NO_DATA`  
  - Declanșator: date, context sau precondiții lipsă ori indecidabile.  
  - Comportament: se abandonează efectul; nu se fac încercări de „best-effort”.

- `ERR.TTL_EXPIRED`  
  - Declanșator: `TTL` este în trecut sau expiră înainte de angajarea efectului.  
  - Comportament: se abandonează efectul; invocarea se tratează ca neaplicabilă.

- `ERR.SCOPE_VIOLATION`  
  - Declanșator: invocarea încearcă să acționeze în afara `CONTEXT` declarat sau încalcă o invocare existentă cu `PRIORITY` mai mare.  
  - Comportament: se abandonează efectul; starea impusă de invocarea cu `PRIORITY` mai mare sau deja angajată rămâne neschimbată.

## Note operaționale

- Se loghează semnătura completă și rezultatul ales (efect sau eroare standard) pentru fiecare invocare procesată.  
- În lanțuri de invocări, fiecare hop emite propriul `INVOKE::<COD> | CONTEXT | PRIORITY | TTL`, fără moștenire tăcută.  
- Erorile locale suplimentare, dacă există, se mapează clar pe erorile standard la frontiera de arhitectură.