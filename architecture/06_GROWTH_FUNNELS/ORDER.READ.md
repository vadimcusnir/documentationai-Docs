COD:: ORDER.READ GROWTH_FUNNELS TTL=90z

## ORDINE DE CITIRE / MODIFICARE

1. Citești `architecture/00_MANIFEST/ORDER.READ` pentru regulile globale de ordine.
2. Verifici `architecture/01_CONSTITUTION/RULE.TRUTH` pentru disciplina pe date/metrici.
3. Verifici `architecture/05_VALUE_STACK/PRICING` pentru ancore de valoare și monetizare.
4. Abia apoi citești sau modifici regulile din `architecture/06_GROWTH_FUNNELS/*`.
5. Orice schimbare stabilă de funnel se loghează în `architecture/02_MEMORY_OS/DECISION.LEDGER` cu ID unic.

## REGULI DURE PENTRU FUNNELS

- Orice funnel trebuie să fie explicit legat de un strat de valoare din `architecture/05_VALUE_STACK/*`.
- Este interzis să inventezi metrici sau valori; dacă nu există sursă, marchezi explicit `ERR.NO_DATA` (vezi secțiunea de mai jos) și nu tragi concluzii numerice. Vezi `architecture/01_CONSTITUTION/RULE.TRUTH`.
- Nicio modificare de definiție de funnel (stadii, conversii, praguri) nu este validă fără intrare în `architecture/02_MEMORY_OS/DECISION.LEDGER`.
- Când datele sunt conflictuale între surse, se notează conflictul în DECISION.LEDGER și se alege sursa de adevăr explicit, nu tacit.
- Orice KPI nou derivat din funnels trebuie legat de o decizie operațională clară (ce se schimbă dacă KPI se mișcă).

## SECȚIUNE PENTRU LIPSA DE DATE

Când nu există date sigure pentru un funnel sau o etapă:

- marchezi linia sau paragraful cu prefix `ERR.NO_DATA`
- menționezi sursa care lipsește sau este instabilă
- te abții de la extrapolări sau proiecții numerice

Exemplu de notare:

```text
ERR.NO_DATA: Nu există încă serii istorice stabile pentru rata de conversie acestui funnel. Nu se trag concluzii și nu se setează ținte numerice până la clarificare.
```