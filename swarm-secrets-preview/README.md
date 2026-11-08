# Swarm secrets preview

Feature commit: `0b07870fb2ac48dba33439f89c75c634d9c179f3`. Base: `3c6d5f611389fdb0eeab9e13285ae3d6828800c0`.

The five screenshots show the final optimized production build on 8 November 2026. They use sample names and an isolated Docker-in-Docker Swarm. No real credentials or secret values are included.

The production browser run checks the Overview count, password or authenticator access, secret creation, exact-name deletion, service counts, disabled deletion, copying a name, date layout and sorting, Docker byte limits, duplicate names, rollback references, and metadata-only responses. See `production-results.json` for the final run.

`runtime-results.json` records the earlier real Dokploy stack deployment, mounted file bytes, task recreation, zero-replica deletion protection, and local/SSH scope checks. `security-results.json` records password and 2FA checks, expiry, parallel attempt limits, second-session rejection, and mobile verification. The final production run also checks the updated typed-name dialog.

HTTPS uses a local self-signed certificate through Traefik. Browser certificate trust is bypassed only for this fixture. Public ACME issuance was not tested. The host Swarm was not initialized or changed.

The usage count is the number of distinct Swarm services referencing a secret, including rollback references. One stack can contain several such services.
