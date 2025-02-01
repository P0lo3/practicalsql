# practicalsql

1. Allow External Connections to PostgreSQL on Raspberry Pi
   Open the postgresql.conf file on the Raspberry Pi. This is usually located at /etc/postgresql/{version}/main/postgresql.conf (where {version} is your PostgreSQL version).
   listen_addresses = '*'
2. Configure pg_hba.conf to Allow Connections
   Next, you need to modify the pg_hba.conf file, which controls client authentication. It's typically located in /etc/postgresql/{version}/main/pg_hba.conf.
   sudo nano /etc/postgresql/{version}/main/pg_hba.conf
   host    all             all             <your_windows_ip>/32          md5
3. Restart PostgreSQL
   sudo service postgresql restart


-- LOGS --

pi5@pi5:/etc/postgresql/17/main $ sudo tail -f /var/log/postgresql/postgresql-17-main.log
2025-02-01 16:51:39.165 GMT [2069] LOG:  shutting down
2025-02-01 16:51:39.167 GMT [2069] LOG:  checkpoint starting: shutdown immediate
2025-02-01 16:51:39.177 GMT [2069] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.003 s, sync=0.002 s, total=0.012 s; sync files=2, longest=0.001 s, average=0.001 s; distance=0 kB, estimate=0 kB; lsn=0/1950928, redo lsn=0/1950928
2025-02-01 16:51:39.179 GMT [2068] LOG:  database system is shut down
2025-02-01 16:51:39.357 GMT [2115] LOG:  starting PostgreSQL 17.2 (Debian 17.2-1.pgdg120+1) on aarch64-unknown-linux-gnu, compiled by gcc (Debian 12.2.0-14) 12.2.0, 64-bit
2025-02-01 16:51:39.358 GMT [2115] LOG:  listening on IPv6 address "::1", port 5432
2025-02-01 16:51:39.358 GMT [2115] LOG:  listening on IPv4 address "127.0.0.1", port 5432
2025-02-01 16:51:39.359 GMT [2115] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2025-02-01 16:51:39.364 GMT [2118] LOG:  database system was shut down at 2025-02-01 16:51:39 GMT
2025-02-01 16:51:39.370 GMT [2115] LOG:  database system is ready to accept connections
^C
pi5@pi5:/etc/postgresql/17/main $ sudo nano postgresql.conf
pi5@pi5:/etc/postgresql/17/main $ sudo service postgresql restart
pi5@pi5:/etc/postgresql/17/main $ sudo tail -f /var/log/postgresql/postgresql-17-main.log
2025-02-01 16:53:11.266 GMT [2116] LOG:  shutting down
2025-02-01 16:53:11.268 GMT [2116] LOG:  checkpoint starting: shutdown immediate
2025-02-01 16:53:11.278 GMT [2116] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.003 s, sync=0.002 s, total=0.012 s; sync files=2, longest=0.001 s, average=0.001 s; distance=0 kB, estimate=0 kB; lsn=0/19509D8, redo lsn=0/19509D8
2025-02-01 16:53:11.281 GMT [2115] LOG:  database system is shut down
2025-02-01 16:53:11.465 GMT [2162] LOG:  starting PostgreSQL 17.2 (Debian 17.2-1.pgdg120+1) on aarch64-unknown-linux-gnu, compiled by gcc (Debian 12.2.0-14) 12.2.0, 64-bit
2025-02-01 16:53:11.465 GMT [2162] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2025-02-01 16:53:11.465 GMT [2162] LOG:  listening on IPv6 address "::", port 5432
2025-02-01 16:53:11.467 GMT [2162] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2025-02-01 16:53:11.472 GMT [2165] LOG:  database system was shut down at 2025-02-01 16:53:11 GMT
2025-02-01 16:53:11.477 GMT [2162] LOG:  database system is ready to accept connections
