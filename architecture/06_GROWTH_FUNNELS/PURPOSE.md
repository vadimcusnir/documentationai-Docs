COD:: PURPOSE; LAYER=06_GROWTH_FUNNELS; TTL=90z

## Scop

Stratul `06_GROWTH_FUNNELS` definește modelele și constrângerile pentru funnel-uri de creștere, conversie și retenție. Aici stabilești cum este transformată atenția în trafic, traficul în utilizatori, iar utilizatorii în valoare recurentă, într-un mod aliniat cu `architecture/00_MANIFEST/PURPOSE` și cu principiile din `architecture/05_VALUE_STACK/PRICING`.

## Ce intră aici

- Definirea arhitecturii standard de funnel (awareness → activation → revenue → retention → referral) și a variațiilor acceptate.
- Modele de tracking pentru evenimente critice de funnel (de exemplu: activare, conversie, churn, reactivare), fără a detalia implementarea tehnică.
- Criterii și praguri pentru trecerea între etapele de funnel (ce înseamnă "activat", "convertit", "retinut").
- Constrângeri asupra experimentelor de creștere (ce tipuri de teste sunt permise, cum se raportează la `architecture/02_MEMORY_OS/DECISION.LEDGER`).
- Reguli pentru alinierea funnel-urilor cu strategiile de valoare și monetizare din `architecture/05_VALUE_STACK/PRICING`.
- Terminologie canonică pentru tipuri de funnel (growth, sales, onboarding, reactivation, referral) și relațiile dintre ele.
- Ghidarea modului în care funnel-urile influențează designul de sistem din straturile `03_SYSTEMS_OS` și `08_OPERATIONS`.

## Out of scope

- Detalii de implementare analitică (configurare de tool-uri, schema exactă de evenimente) care aparțin stratului `02_MEMORY_OS` și sistemelor concrete.
- Descrierea sistemelor sau automatizărilor specifice (flow-uri de email, campanii, playbook-uri operaționale) care țin de `08_OPERATIONS`.
- Politici de preț și pachete comerciale detaliate (acestea sunt definite în `architecture/05_VALUE_STACK/PRICING`, nu aici).
- Considerații legale, de conformitate sau termeni comerciali (contracte, GDPR, etc.).
- Documentarea UI/UX pentru pagini sau ecrane specifice; aici se lucrează cu etape și metrici, nu cu layout-uri.
- Metrici ad-hoc sau one-off pentru experimente izolate care nu devin standarde de funnel.

## Next documents

- `architecture/06_GROWTH_FUNNELS/ORDER.READ`