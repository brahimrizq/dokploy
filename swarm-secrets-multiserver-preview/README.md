# Multi-server Swarm secrets validation

Tested implementation: `82d416fe07419fa4393d381af9929d2b3b35340f` for Dokploy/dokploy#5943.

Vagrant 2.4.9 uses its Docker provider to manage three SSH-enabled Docker-in-Docker test servers: two joined Swarm managers and one worker. The existing local preview runs a separate Swarm. These test servers are containers, not virtual machines. The tests use real SSH connections through Dokploy's normal remote Docker transport and real Swarm services.

All 16 checks passed. They cover selected-server create/list/count/delete, switching between local and remote, shared secret IDs across joined managers, independent same-name secrets across separate Swarms, typed-name deletion, worker errors, connection recovery, zero-replica and rollback-only protection, and a remote Stack deployed through Dokploy. Three healthy services on the worker mounted the exact UI-created multiline UTF-8 bytes. A replacement task mounted the same bytes too. Existing local secrets and the earlier MySQL test application were preserved.

The screenshots show only synthetic demo names, test server addresses, and a synthetic account. No secret values or private keys are included. The app and test servers are intentionally left running for the user's manual tests. See results.json for the exact checks and provider boundary.

The documentation companion, Dokploy/website#224, now explains selected servers and shared versus separate Swarms. No application code changes were needed for this validation.
