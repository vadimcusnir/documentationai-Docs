COD:: ROLE=MEMORY.OS.DECISION.LEDGER | activates=on_write | invoked_when=decision_committed | TTL=permanent

Format strict, 1 linie / decizie:

`DECISION::<ID> | ce s-a decis | motiv | impact [Ψ/Σ/€] | data | TTL`

DECISION::0001 | README canonic este `architecture/00_README_SYSTEM.md` | avem nevoie de un singur punct de adevăr pentru descrierea sistemului | impact [Ψ] | 2026-01-01 | TTL=permanent  
DECISION::0002 | zona de carantină nu este invocată automat de DECISION.LEDGER | deciziile acestui ledger trebuie să fie stabile, nu provizorii | impact [Σ] | 2026-01-01 | TTL=revizuire_la_schimbare_OS  
DECISION::0003 | fiecare decizie nouă necesită contract explicit de invocare (role + triggers + TTL) | prevenim decizii orfane sau imposibil de aplicat operațional | impact [€] | 2026-01-01 | TTL=permanent  
DECISION::0004 | au fost create stub-urile lipsă pentru layerele de guvernanță `02_IDENTITY_ENGINE`, `04_SEMIOTICS_BRAND`, `06_GROWTH_FUNNELS`, `07_PROMPT_ENGINEERING`, `09_QUARANTINE` și au fost conectate în navigație | păstrăm arhitectura completă și evităm zone orfane în structură | impact [Σ] | 2026-01-01 | TTL=permanent  
DECISION::0005 | standardul unic de TTL este token-ul `TTL=permanent`, token-ul `TTL=∞` este depreciat și nu mai este folosit în arhitectură | reducem ambiguitatea semantică și facilităm parsarea automată a TTL-urilor | impact [Ψ] | 2026-01-01 | TTL=permanent  
DECISION::0006 | structura reală `architecture/10_ARCHIVE_RAW` a fost creată și integrată în `TTL_POLICY` ca arhivă necitabilă pentru conținut brut | separăm clar arhiva brută de sursele citabile și reducem riscul de a cita materiale necuratate | impact [€] | 2026-01-01 | TTL=permanent