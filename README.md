# SchoolAccount-LocalDevTools
Supporting services and tools to for local development of the School Account Beta.

## COLLECT Portal Database

An instance of the COLLECT Portal database is required to run the School Account services.

The database is not owned by the team, so must sit outside of the code base. This project provides the facility to run a local database for development and testing purposes.
A suitable database backup can be obtained from the School Account Beta team. 

This project includes a [docker-compose](./docker-compose.yml) to restore the database backup to a containerised SQL Sever database.
To run this a database backup file named `CollectPortal.BAK` needs to be placed in the root of this project.

The database runs on the standard SQL Server port of `1433`. If you have another database running you may experience a port conflict, so will need to shut down any local SQL Server instance.

The default password for the `sa` account is `MyStrongPassword123!`.

## Azurite
For the feedback component to be fully functional on the School Account project, an Azure Table Service storage is needed.
Azurite provides a local instance of the Azure services (Blob, Table, Queue).

An Azure client container will run alongside the Azurite container to provide the needed table and fields to access the feedback with no errors.
This will allow you to run the School Account services locally and test this component using Azure or a local tool such as Azure Storage Explorer.

## Local Running

To run all container, run the command:
```
docker compose up -d
```

The database server will automatically restart on reboot, the other containers will not, but it can be manually stopped via 
```
docker compose stop
```
or all containers can be removed completely and reset via 
```
docker compose down -v
```