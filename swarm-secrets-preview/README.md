# Swarm secrets preview

Feature commit: `d78d6236196f092c0a76a5a8a3b0bc76dd287a12`. Base: `3c6d5f611389fdb0eeab9e13285ae3d6828800c0`.

Seven screenshots show the source app on 8 November 2026. The list uses the standard signed-in Docker permission and selected-server checks. It opens directly. The app uses real PostgreSQL, Docker secrets, and service references in an isolated Docker-in-Docker Swarm. Screenshots contain sample names and public example content, with no private credentials or stored secret values.

The create dialog reuses Dokploy's shared code editor. The pencil opens Create replacement secret with empty content and a new name. Docker cannot return or change an existing value. The old secret and its references are preserved. Hovering over or focusing a disabled delete icon explains why deletion is blocked.

`direct-access-results.json` records 17 browser checks with no browser errors. These cover normal signed-in access, column order, date formatting and sorting, copying names, typed-name deletion, count updates, metadata-only responses, anonymous access rejection, confirmation during background refresh, multiline UTF-8 content, replacement creation, and the disabled-delete tooltip. A temporary Swarm service mounted the UI-created value, and its SHA-256 matched the submitted bytes, including whitespace and non-ASCII text.

`direct-runtime-results.json` records nine live Docker checks, including UTF-8 byte limits, duplicate names, exact-name confirmation, already-deleted errors, zero-replica services, and rollback-only references. The tests remove their temporary secrets and services.

149 targeted tests across 13 files, workspace type checks, and changed-file Biome checks passed. All workspace production builds passed. See `verification.json` for details. These screenshots come from the source development app. Earlier feature evidence remains in the branch history.

The usage count is the number of distinct Swarm services referencing a secret, including rollback references. One stack can contain several such services. The host Swarm was not initialized or changed.
