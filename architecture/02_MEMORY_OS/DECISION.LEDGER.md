COD:: ROLE=MEMORY.OS.DECISION.LEDGER | activates=on_write | invoked_when=decision_committed | TTL=∞

Format strict, 1 linie / decizie:

`DECISION::<ID> | ce s-a decis | motiv | impact [Ψ/Σ/€] | data | TTL`

DECISION::0001 | README canonic este `architecture/00_README_SYSTEM.md` | avem nevoie de un singur punct de adevăr pentru descrierea sistemului | impact [Ψ] | 2026-01-01 | TTL=∞  
DECISION::0002 | zona de carantină nu este invocată automat de DECISION.LEDGER | deciziile acestui ledger trebuie să fie stabile, nu provizorii | impact [Σ] | 2026-01-01 | TTL=revizuire_la_schimbare_OS  
DECISION::0003 | fiecare decizie nouă necesită contract explicit de invocare (role + triggers + TTL) | prevenim decizii orfane sau imposibil de aplicat operațional | impact [€] | 2026-01-01 | TTL=∞