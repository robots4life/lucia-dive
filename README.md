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

create postgresql database lucia_dive

`create database lucia_dive;`

list postgresql databases available, lucia_dive should be listed

`postgres=# \l`

<img src="https://github.com/robots4life/lucia-dive/blob/master/docs/Screenshot_20230516_191822.png">

7.

## Creating the database schema

https://www.prisma.io/docs/getting-started/setup-prisma/start-from-scratch/relational-databases/using-prisma-migrate-typescript-postgresql#creating-the-database-schema

create the schema for the database

```js
model Post {
  id        Int      @id @default(autoincrement())
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  title     String   @db.VarChar(255)
  content   String?
  published Boolean  @default(false)
  author    User     @relation(fields: [authorId], references: [id])
  authorId  Int
}

model Profile {
  id     Int     @id @default(autoincrement())
  bio    String?
  user   User    @relation(fields: [userId], references: [id])
  userId Int     @unique
}

model User {
  id      Int      @id @default(autoincrement())
  email   String   @unique
  name    String?
  posts   Post[]
  profile Profile?
}
```

8.

## Use Prisma migrate

`npx prisma migrate dev --name init`

```shell
devilbox@php-8.1.14 in /shared/httpd/lucia-dive $ npx prisma migrate dev --name init
Environment variables loaded from .env
Prisma schema loaded from prisma/schema.prisma
Datasource "db": PostgreSQL database "lucia_dive", schema "public" at "pgsql:5432"

Applying migration `20230518102429_init`

The following migration(s) have been created and applied from new schema changes:

migrations/
  └─ 20230518102429_init/
    └─ migration.sql

Your database is now in sync with your schema.

Running generate... (Use --skip-generate to skip the generators)

added 2 packages, and audited 228 packages in 2m

44 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

✔ Generated Prisma Client (4.14.0 | library) to ./node_modules/@prisma/client in 109ms


devilbox@php-8.1.14 in /shared/httpd/lucia-dive $
```

<img src="/docs/Screenshot_20230518_123002.png">
