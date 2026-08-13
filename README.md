# SchoolAccount-LocalDevTools
Supporting services and tools to for local development of the School Account Beta.

## COLLECT Portal Database

An instance of the COLLECT Portal database is required to run the School Account services.

The database is not owned by the team, so must sit outside of the code base. This project provides the facility to run a local database for development and testing purposes.
A suitable database backup can be obtained from the School Account Beta team. 

This project includes a [docker-compose](./docker-compose.yml) to restore the database backup to a containerised SQL Sever database.

To run the database place a database backup file named `CollectPortal.BAK` file into the root of this project and run the command:
```
docker compose up -d
```

The database server will automatically restart on reboot, but can be manually stopped via 
```
docker compose stop
```
or removed and completely and reset via 
```
docker compose down -v
``` 

The database runs on the standard SQL Server port of `1433`. If you have another database running you may experience a port conflict, so will need to shut down any local SQL Server instance.

The default password for the `sa` account is `MyStrongPassword123!`.