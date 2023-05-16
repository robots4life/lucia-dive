## Learning Lucia..

### Getting started

1.

https://lucia-auth.com/start-here/getting-started

2.

install lucia-auth

`npm install lucia-auth --verbose`

### Set up the database

3.

https://lucia-auth.com/adapters/prisma

4.

https://www.prisma.io/docs/getting-started/quickstart

https://www.prisma.io/docs/getting-started/setup-prisma/start-from-scratch/relational-databases-typescript-postgresql#create-project-setup

initialize a TypeScript project and add the Prisma CLI as a development dependency to it

`npm install prisma typescript ts-node @types/node --save-dev --verbose`

5.

set up Prisma with the init command of the Prisma CLI

`npx prisma init --datasource-provider postgresql`

6.

setup devilbox postgresql connection

https://devilbox.readthedocs.io/en/latest/configuration-files/env-file.html#postgresql

https://devilbox.readthedocs.io/en/latest/configuration-files/env-file.html#pgsql-root-user

`PGSQL_ROOT_USER` : `postgres`

https://devilbox.readthedocs.io/en/latest/configuration-files/env-file.html#pgsql-root-password

`PGSQL_ROOT_PASSWORD` : `empty`

https://www.prisma.io/docs/concepts/database-connectors/postgresql#connection-details

`postgresql://USER:PASSWORD@HOST:PORT/DATABASE`

enter devilbox shell

`/media/user/d/WWW/devilbox/shell`

enter postgresql via terminal

`psql -h pgsql -U postgres`

create database lucia_dive

`create database lucia_dive;`

`postgres=# \l`

<img src="https://github.com/robots4life/lucia-dive/docs/Screenshot_20230516_191822.png">
