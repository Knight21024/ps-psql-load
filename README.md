# ps-psql-load

## PowerShell PostgreSQL Load script

    This is a simple PowerShell script that generates load on a PostgresSQL database. 
    It was tested against verion 9.5 of enterprisedb.com's PostgreSQL running locally.
    I'm putting this up on GitHub because it took me a while to research this syntax
    and I'm hoping to save you some time.

### How it works
    It works by using the commandline tool for PostgreSQL called "psql.exe". 
    To invoke and craft the invocation of the image in PowerShell I had to use the & operator. 
    The next trick was getting the connection string to work with the password since there is 
    no explicit way to pass the password for PSQL.exe (example: PSQL --password=password).
    Turns out the -dbname parameter supports a connection string format with password.
    The prohibts PSQL from prompting for password every time and allows the script to run.
    Lastly my example is for a table named "t1", with two coloumns "c1" int primary key and "c2" text
    One last trick - if you are trying to use PSQL against an Azure database which has an "@" 
    in the user name (ex: postgresadmin@azuredb4postgres) drop the username from the dbname 
    and pass it explicitly 
        **psql --username postgresadmin@azuredb4postgres --dbname="postgresql://:Password@localhost:5432/postgres"**

### Syntax
    For the dbname fqdn = fully qualified domain name (location of the server)
    --dbname "postgresql://username:password@fqdn:port/database"
