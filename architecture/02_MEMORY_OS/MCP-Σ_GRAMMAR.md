COD:: role=MEMORY_OS + activates=INVOKE.MEMORY_OS + invoked_when=MEMORY_SCOPE + TTL=SECONDS

## TIP.RECORD_TYPES

- `INVOKE`
- `DECISION`

## TIP.COMMON_FIELDS

- `record_type` ∈ {`INVOKE`,`DECISION`} (obligatoriu)
- `id` = string non-goal, unic per conversație (obligatoriu)
- `ts` = timestamp ISO8601 (obligatoriu)
- `ttl_sec` = int >= 0 (obligatoriu)
- `scope` = string enum definit de orchestrator (obligatoriu)
- `payload` = obiect JSON valid (obligatoriu)
- `err` = string sau `null` (normalizat, vezi mai jos)

## TIP.INVOKE

Semnătură logică INVOKE:

- `record_type` = `INVOKE`
- `intent` = string scurt, stabil (obligatoriu)
- `query` = string brut de căutare / cheie memorie (obligatoriu)
- `limit` = int > 0 (opțional, default 10)
- `payload`:
  - `filters` = obiect JSON determinist (opțional)
  - `hints` = listă string (opțional)

Contract:

- dacă `ttl_sec = 0` ⇒ doar lookup sincron, fără persistență.
- dacă `ttl_sec > 0` ⇒ orice efect persistent expiră logic la `ts + ttl_sec`.

## TIP.DECISION

- `record_type` = `DECISION`
- `source_invoke_id` = `id` de la un `INVOKE` (obligatoriu)
- `decision` = string enum (ex: `WRITE`,`SKIP`,`REFRESH`) (obligatoriu)
- `payload`:
  - `memory` = obiect JSON serializabil (opțional, doar când `decision=WRITE`)
- `ttl_sec` moștenit sau explicit; dacă lipsește, se copiază din `INVOKE`.

## TIP.TTL_SEMANTICS

- `now > ts + ttl_sec` ⇒ orice utilizare de date este interzisă.
- orice acces la `payload.memory` după expirare ⇒ eroare `ERR.TTL_EXPIRED`.
- reînnoirea TTL se face doar prin nou `DECISION` sau nou `INVOKE`.

## TIP.ERROR_NORMALIZATION

Câmp `err` este obligatoriu la toate înregistrările:

- succes: `err = null`
- fără date utile, dar fără eroare tehnică:
  - `err = "ERR.NO_DATA"`
- acces la date cu TTL expirat:
  - `err = "ERR.TTL_EXPIRED"`
- încălcare de scope (citire / scriere în afara `scope` activ):
  - `err = "ERR.SCOPE_VIOLATION"`

Alte coduri de eroare interne se mapează la unul din cele trei coduri admise înainte de expunere.