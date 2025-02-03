# How to use this Postgresql server

*** Before starting the docker container you should run the following command exactly where you have the docker-compose file. This command below creates a folder for pg with write permissions 
 otherwise the database wont work as expected. ***
```
mkdir -p pg-vol
sudo chown -R 1001 pg-vol
```

Then, you can start the docker container by
```
docker compose up --build --detach
```

To enter the cli provided by posgtres
```
docker exec -it pg-pg-1 bash
```

It will take you to a cli with weird looking name, There you need to type
```
psql -U postgres
```

It will ask you password and you need to give 
```
Password123
```
as password

Then you will successfully enter the postgress database server's cli.

There hit the following command
```
create database new_database;
***Hit Enter***

create user new_user with password 'password';
***Hit Enter***

grant all privileges on database new_database to new_user;
***Hit Enter***

alter database new_database owner to new_user;
***Hit Enter***
```

This will successfully create database named new_database and its user is set as new_user.
To connect to this database using database url, you can use followng URL:
```
postgresql://new_user:password@localhost:5432/new_database
```