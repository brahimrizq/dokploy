# Compose database backup review evidence

Sanitized evidence for [Dokploy issue #6018](https://github.com/Dokploy/dokploy/issues/6018).

The implementation and documentation changes are on separate contribution branches. This branch contains only review screenshots and a verification summary.

## Validation

- 218 targeted backup tests across 16 files passed.
- Type checks for all four application workspaces and Biome on all 19 changed source/test files passed.
- The application production build passed in an isolated source copy. Its final frontend was rebuilt after the last UI changes.
- 66 live integration and compatibility checks passed against PostgreSQL 18.7 through a proxy on port 6543, MySQL 8.4 on port 3307, MariaDB 11.4 on port 3308, and MongoDB 8 on port 27018.
- 45 browser checks passed, covering desktop/mobile layout, validation, filenames, collapsed sections, draft preservation, and manual backup availability.
- Eight original saved configurations remained unchanged and produced backups without being resaved.
- The broader suite run had 1843 passing tests, four failures in `__test__/deploy/application.real.test.ts`, and five skipped tests. Those real deployment tests require Git/build/Swarm infrastructure; the full suite is not green.
- Documentation installation with the frozen lockfile, Biome CI, workspace and documentation type checks, and the production documentation build passed. The documentation build generated 453 pages using one worker. Generated backup-page headings and screenshots were inspected.

## Test boundaries

S3 tests used a local compatible emulator. Remote SSH dispatch has automated coverage, but a live remote-server deployment was not tested. Production build-time lookups could not resolve the default `dokploy-postgres` hostname; the application build still completed.

Custom command save tests perform a full dump and discard the output. They do not validate S3 access. The existing Restore Backup dialog does not expose the new connection overrides; nondefault endpoints were restored with native database clients.

The screenshots show a disposable local fixture. Its credentials and private session state are not included. Documentation screenshots were rendered from the production build without starting a server.

## Screenshots

- [21-reviewed-backup-dialog.png](screenshots/21-reviewed-backup-dialog.png)
- [15-connection-settings-expanded.png](screenshots/15-connection-settings-expanded.png)
- [22-custom-command-reviewed.png](screenshots/22-custom-command-reviewed.png)
- [03-unsafe-command-rejected.png](screenshots/03-unsafe-command-rejected.png)
- [04-invalid-credentials.png](screenshots/04-invalid-credentials.png)
- [17-manual-backup-stopped.png](screenshots/17-manual-backup-stopped.png)
- [16-connection-settings-mobile.png](screenshots/16-connection-settings-mobile.png)
- [23-backup-documentation.png](screenshots/23-backup-documentation.png)
- [24-proxy-documentation.png](screenshots/24-proxy-documentation.png)
