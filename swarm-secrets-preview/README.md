# Swarm secrets preview

Feature commit: `99d00b0e05db5296d1cf6581fd3c44a6531fe7be`. Base: `3c6d5f611389fdb0eeab9e13285ae3d6828800c0`.

Six screenshots show the source app on 8 November 2026. The list uses the standard signed-in Docker permission and selected-server checks. It opens directly. The app uses real PostgreSQL, Docker secrets, and service references in an isolated Docker-in-Docker Swarm. Screenshots contain sample names and public example content, with no private credentials or stored secret values.

The create dialog reuses Dokploy's shared code editor. Each secret row has only a delete action. Hovering over or focusing a disabled delete icon explains why deletion is blocked. Docker cannot return or change an existing value. To rotate a secret, create one with a new name and update the stack before removing the old secret.

`direct-access-results.json` records 15 browser checks with no browser errors. These cover normal signed-in access, column order, date formatting and sorting, copying names, typed-name deletion, count updates, metadata-only responses, anonymous access rejection, confirmation during background refresh, multiline UTF-8 content, delete-only row actions, and the disabled-delete tooltip. A temporary Swarm service mounted the UI-created value, and its SHA-256 matched the submitted bytes, including whitespace and non-ASCII text.

`direct-runtime-results.json` records nine live Docker checks from the preceding version. The server code is unchanged. These checks cover UTF-8 byte limits, duplicate names, exact-name confirmation, already-deleted errors, zero-replica services, and rollback-only references. The tests remove their temporary secrets and services.

149 targeted tests across 13 files and frontend type checking passed on this commit. Workspace type checks passed on the preceding commit, with only frontend and documentation changes since then. All workspace production builds passed on this commit. See `verification.json` for details. These screenshots come from the source development app. Earlier feature evidence remains in the branch history.

The usage count is the number of distinct Swarm services referencing a secret, including rollback references. One stack can contain several such services. The host Swarm was not initialized or changed.
