# PostgreSQL Commands
- To take backup from the local postgreSQL

`pg_dump -U USER -d DATABASE_NAME >backup.dump`

- In Windows, to restore data from dump file to postgres database

`psql -U postgres -f mine.dump Test`