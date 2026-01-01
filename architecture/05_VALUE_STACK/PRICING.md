COD:: definește economia OS (prețuri, gating, pachete) + activează decizii de ofertare + invocă la lansări/upsell/paywall + TTL=30z

INVOKE::PROD.PRICING | CONTEXT=ofertare, landing, paywall, upsell | PRIORITY=HIGH | TTL=30z

## Scop
Definește un singur adevăr pentru prețuri, pachete și reguli de acces. Elimină negocierile ad-hoc.

## Principii
- Fixează prețul ca instrument de selecție, nu ca recompensă.
- Separă clar: Free → Entry → Core → Premium → VIP.
- Leagă fiecare nivel de: acces, livrabile, limitări, risc asumat.

## Reguli (hard)
- Nu inventa prețuri în răspunsuri publice. Dacă lipsește o valoare: NU EXISTĂ DATE.
- Nu modifica prețuri fără DECISION.LEDGER.
- Nu amesteca „trial” cu „free”. Trial = timp. Free = limită de conținut/funcție.

## Structură de pricing (exemplu de schemă)
### 1) Free (indexabil)
- Acces: preview limitat, orientare, diagnostic entry.
- Obiectiv: activare + calificare.

### 2) Entry (tripwire)
- Acces: o unitate clară (audit, tool mic, VIP day, mini-setup).
- Obiectiv: conversie rapidă.

### 3) Core (abonament)
- Acces: produse închiriate (gating prin token/rol), actualizări, comunitate.
- Obiectiv: recurenta.

### 4) Premium (program)
- Acces: cohortă, feedback, implementare.
- Obiectiv: rezultat măsurabil.

### 5) VIP (inițiere/licență)
- Acces: rol, drepturi, white-label, licențiere.
- Obiectiv: scalare.

## Gating (dacă folosești token/rol)
- Definește: praguri, ce se deblochează, ce se blochează.
- Leagă gating-ul de roluri (visitor, logged, lvl1..lvl3, VIP).

## Checklist de invocare
- Ai DECISION.LEDGER actualizat cu prețurile curente?
- Ai TTL valid pentru această versiune?
- Ai diferențiat clar Free vs Trial vs Paid?