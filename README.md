# Hands-On Lab: Backups, Point-in-Time Recovery, and Replication - Summary

## 1. Logical Backup & Restore
* **What we did:** Created a backup directory (`~/backups`) and exported the database snapshot using `pg_dump`[span_0](start_span)[span_0](end_span).
* **Verification:** Tested the backup file using `pg_restore` and loaded it into a check database to ensure data integrity[span_1](start_span)[span_1](end_span).

## 2. Enabling WAL (Write-Ahead Log) Archiving
* **Configuration:** Updated `postgresql.conf` to set `wal_level = replica` and enabled `archive_mode` so all transaction logs are safely archived[span_2](start_span)[span_2](end_span).

## 3. Disaster Recovery & Point-in-Time Recovery (PITR)
* **The Scenario:** Simulated a disaster by accidentally deleting records (`DELETE FROM students;`)[span_3](start_span)[span_3](end_span).
* **The Fix:** Used our base backup combined with the WAL transaction logs to recover the database right up to the exact moment before the deletion occurred[span_4](start_span)[span_4](end_span)[span_5](start_span)[span_5](end_span).

## 4. Setting Up a Streaming Standby Replica
* **Replication:** Created a replication user role on the primary server (`CREATE ROLE replicator...`)[span_6](start_span)[span_6](end_span) and used `pg_basebackup` to spin up a live standby server[span_7](start_span)[span_7](end_span)[span_8](start_span)[span_8](end_span).
* **Health Check:** Monitored the replication lag using `pg_stat_replication`[span_9](start_span)[span_9](end_span).
*