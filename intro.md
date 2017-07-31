Introduction
============

Initial set up
--------------

### Operating System ###

See [this repo][i.i.os01] for guidance on setting up a Linux VPN

### Database ###

#### Install Postgres ####

As limited user:

```
sudo apt-get install postgresql
```

#### Initial Configuration of Postgres ####

Need to log in to the postgres database to set a password for postgres user.
(Note we are only setting the postgres/postgres user's password, not the OS/postgres user's password. By default, the OS/postgres user 
is locked).

```
sudo -u postgres psql postgres
```

The above command translates to "run the program `psql` with the argument `postgres` (which tells `psql` to load the database `postgres`) 
as the user `postgres`. Note that for many (most?) systems, the final `postgres` is redundant because `psql` will, by default, attempt to
connect to the database with the same name as the user executing the command (in this case, `postgres`).

Once in `psql` and connected to the `postgres` database, run the password metacommand to set the postgres/postgres user's password:

```
\password
```

#### Create a database ####

```SQL
CREATE DATABASE <databaseName>;
```

By default, the create database command allocates a new database by cloning the built-in system database *template1*.

You can confirm the existence of the newly-created database by using the `\list` (can be abbreviated as `\l`) metacommand.


#### Connect to a new database ####

Once the new DB is created, we want to connect to it. We can do it directly from psql or we can log in from the command line.

To connect from the command line, we simply repeat the command from Initial Configuration section but specify the db we want to which 
we want to connect:

```
sudo -u postgres psql <databaseName>
```

To connect from within psql:

```SQL
\connect <databaseName>
```

(Note that `\connect` can be abbreviated as `\c`)


[i.i.os01]: https://github.com/Crossroadsman/ServerAdmin
