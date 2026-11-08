# Swarm secrets preview

Feature commit: `5deb0c575f2f824d9eb0ba6f37cf7bf14af90a25`. Base: `3c6d5f611389fdb0eeab9e13285ae3d6828800c0`.

The five screenshots show the latest source app on 8 November 2026. They were refreshed after moving Created before Actions and removing the clock time from creation dates. The app uses real PostgreSQL, Docker secrets, and service references in an isolated Docker-in-Docker Swarm. No real credentials or secret values are included.

`layout-results.json` records eight browser checks against the current development app: column order, date-only text above relative time, sorting, copy-name buttons, referenced deletion protection, typed-name deletion, the Overview count, and TOTP verification. Type checks and changed-file Biome checks also passed.

The initial feature commit `0b07870fb2ac48dba33439f89c75c634d9c179f3` passed 175 targeted tests, workspace type checks and production builds, and 17 HTTPS production browser checks. See `production-results.json` for that run. Its earlier column layout was replaced by the layout follow-up above. HTTPS used a local self-signed certificate through Traefik; public ACME issuance was not tested.

`runtime-results.json` records the earlier real Dokploy stack deployment, mounted file bytes, task recreation, zero-replica deletion protection, and local/SSH scope checks. `security-results.json` records password and 2FA checks, expiry, parallel attempt limits, second-session rejection, and mobile verification.

The usage count is the number of distinct Swarm services referencing a secret, including rollback references. One stack can contain several such services. The host Swarm was not initialized or changed.
