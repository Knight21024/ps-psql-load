# ps-psql-load

## Title: PowerShell PostgreSQL Load script

Description: This is a simple PowerShell script that generates load on a PostgresSQL database.  It was tested against verion 9.5 running locally.

It works by using the commandline tool for PostgreSQL called "psql.exe".  To invoke and craft the invocation of the image in PowerShell
I had to use the *&* operator.   The next trick was getting the connection string to work with the password since there is no explicit
way to pass the password for PSQL.exe (example: PSQL --password=N0t@r3@lP@55w0rd).
