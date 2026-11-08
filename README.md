# hikari-stats

<img src="assets/hikari-linux.svg" alt="Hikari Linux" width="128">

An optional WSGI service that stores installation reports in PostgreSQL and
generates an aggregate statistics page. Rebranding this service does not enable
reporting in the Hikari installer; no public reporting endpoint is configured.

## Running

Install `psycopg` or `psycopg2`, create a PostgreSQL database, and load `schema.sql`.
The default connection is `dbname=hikaristats user=hikaristats`; override it with
`HIKARI_STATS_DB` for both the WSGI service and `update_stats.sh`. Set it in the
server process environment to a libpq connection string or URI. With PostgreSQL
peer authentication, run the service and report job as the `hikaristats` OS user
or configure an appropriate identity map.

Serve `app:application` through a WSGI server. `update_stats.sh` writes the
aggregate page to `htdocs/stats.txt`. Existing databases can be used by setting
`HIKARI_STATS_DB`; no data migration or database rename is required.

## Origin and license

Based on the preserved MIT [snapshot of asahistats](https://github.com/HikariLinux/asahistats/tree/633ccdea950654dc2a9206032441c59dddcd6642),
commit `633ccdea950654dc2a9206032441c59dddcd6642`. The original history and
`snapshot-2026-11-08` tag are retained. Hikari Linux maintains this project
independently; it is not an official Asahi Linux release.

Original copyright notices are preserved. Hikari Linux changes and artwork
are also provided under the [MIT license](LICENSE).
