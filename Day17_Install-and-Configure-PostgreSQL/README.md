**TASK**

The Nautilus application development team has shared that they are planning to deploy one newly developed application on Nautilus infra in Stratos DC. The application uses PostgreSQL database, so as a pre-requisite we need to set up PostgreSQL database server as per requirements shared below:

PostgreSQL database server is already installed on the Nautilus database server.

a. Create a database user kodekloud_roy and set its password to 8FmzjvFU6S.

b. Create a database kodekloud_db3 and grant full permissions to user kodekloud_roy on this database.

Note: Please do not try to restart PostgreSQL server service.

**Steps**

Logged into the database

ssh peter@stdb01

Switched to the postgres system user

```bash
sudo -i -u postgres
```

Created the database user

```bash
psql -c "CREATE USER kodekloud_roy WITH PASSWORD '8FmzjvFU6S';"
```

Created the database and assigned ownership

```bash
psql -c "CREATE DATABASE kodekloud_db3 OWNER kodekloud_roy;"
```

Explicitly granted privileges

```bash
psql -c "GRANT ALL PRIVILEGES ON DATABASE kodekloud_db3 TO kodekloud_roy;"
```

Verified the connection

```bash
psql -U kodekloud_roy -d kodekloud_db3 -h localhost
```

