COD:: 09_QUARANTINE.PURPOSE TTL=30z

## Scop

09_QUARANTINE este zona tampon pentru experimente, idei nevalidate și schițe de design care nu au trecut încă printr-un review formal. Aici testezi direcții, nu construiești fundații.

Această zonă există pentru a proteja restul arhitecturii: tot ce intră aici este temporar și presupus descartabil până la promovare explicită.

## Reguli dure

- Niciun component critic nu poate depinde direct de 09.
- Niciun fișier din 09 nu este invocat direct de rutine de producție sau de căile documentate în `architecture/INVOKE.CONTRACT`.
- Orice promovare din 09 către un nivel stabil necesită review explicit și refactor, urmat de mutare în stratul corespunzător.

## Ce intră aici

- Experimente de arhitectură sau fluxuri noi, încă nepilotate.
- Drafturi de convenții care nu au ajuns încă în `architecture/00_MANIFEST` sau `architecture/01_CONSTITUTION`.
- Note temporare care validează ipoteze înainte de integrarea în straturile 02–08.

Pentru ordinea internă a acestui strat și convențiile de numire, vezi `architecture/09_QUARANTINE/ORDER.READ`.

## Out of scope

- Orice regulă, contract sau mecanism de care depind deja alte straturi.
- Documente considerate sursă de adevăr pentru produs sau pentru procese operaționale.
- Specificații de interfață, protocoale sau API-uri care sunt deja expuse clienților sau altor sisteme.