# Docker

Docker is the most popular containerization stack around, and we use it for
automatically setting up our database so that all developers are always on the
same version of PostgreSQL.

## Installation

1. Follow the instructions at their [website](https://www.docker.com/get-started)
2. ???
    1. If you use Windows, pray it works
4. Profit

You should also install `docker-compose`, which may or may not be included in
the installation bundle depending on which OS you're using. Consult the
documentation.

## Configuring environment variables

Before you start the database you need to create a file for the environment
variables that will determine the name of the database and its user, the
password and host. Make a copy of `.env.example` and name it `.env`. For
developing it should look like the following:

```ini
POSTGRES_DB=echokarriere
POSTGRES_USER=karriere
POSTGRES_PASSWORD=password
POSTGRES_HOST=localhost
```

## Starting the database

Once you've configured the `.env` file you can simply run `docker-compose up -d`
to start the database in the background. To see what is happening run `docker
logs echo_backend_db`, it might offer up a hint if it is not working.

## Connecting the database to WebStorm

Since we're using IntelliJ for working on the backend you should add the
database as a data source in the editor.

<figure>
  <img src="/images/intellij-database.png" />
  <figcaption>On the right side of the editor, click on these buttons.</figcaption>
</figure>

<figure>
  <img src="/images/intellij-configure-database.png" />
  <figcaption>Fill in the fields matching the data in your <code>.env</code> file. You may have to download a database driver, but IntelliJ will prompt you for this and automatically download and install it for you.</figcaption>
</figure>

<figure>
  <img src="/images/intellij-tables.png" />
  <figcaption>Once you've successfully established a connection the Database tab will look like this.</figcaption>
</figure>

You'll now have access to a console where you can run SQL queries against our
development database that will include auto completion for table names, columns
and so on.

<figure>
  <img src="/images/intellij-sql-console.png" />
  <figcaption>Running a query against our database.</figcaption>
</figure>

<figure>
  <img src="/images/intellij-query-result.png" />
  <figcaption>The result of the SQL query.</figcaption>
</figure>
