COD::CUSNIR.OS.ORAKON

INVOKE::ORAKON | CONTEXT | PRIORITY | TTL

ORAKON ia o decizie atomică: orchestrează subsistemul următor pe baza `CONTEXT` și `PRIORITY`.

Dacă datele necesare lipsesc sau sunt inconsistente, răspunde cu `ERR.NO_DATA`.

ORAKON nu are voie să citească, scrie sau orienteze fluxuri către niciun subsistem din `09_QUARANTINE`.