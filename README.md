<a href="https://electric-sql.com">
  <picture>
    <source media="(prefers-color-scheme: dark)"
        srcset="https://raw.githubusercontent.com/electric-sql/meta/main/identity/ElectricSQL-logo-light-trans.svg"
    />
    <source media="(prefers-color-scheme: light)"
        srcset="https://raw.githubusercontent.com/electric-sql/meta/main/identity/ElectricSQL-logo-black.svg"
    />
    <img alt="ElectricSQL logo"
        src="https://raw.githubusercontent.com/electric-sql/meta/main/identity/ElectricSQL-logo-black.svg"
    />
  </picture>
</a>

# Welcome to your ElectricSQL app!

This is an example web application using ElectricSQL in the browser with [wa-sqlite](https://github.com/rhashimoto/wa-sqlite).

## Pre-reqs

You need [NodeJS >= 16.11 and Docker Compose v2](https://electric-sql.com/docs/usage/installation/prereqs).

## Install

Install the dependencies:

```sh
npm install
```

## Setup

Start Postgres and Electric using Docker (see [running the examples](https://electric-sql.com/docs/examples/notes/running) for more options):

```shell
npm run backend:up
# Or `npm run backend:start` to foreground
```

Note that, if useful, you can connect to Postgres using:

```shell
npm run db:psql
```

Setup your [database schema](https://electric-sql.com/docs/usage/data-modelling):

```shell
npm run db:migrate
```

Generate your [type-safe client](https://electric-sql.com/docs/usage/data-access/client):

```shell
npm run client:generate
# or `yarn client:watch`` to re-generate whenever the DB schema changes
```

## Run

Start your app:

```sh
npm run dev
```

Open [localhost:5173](http://localhost:5173) in your web browser.

## Develop

`./src/Example.tsx` has the main example code. For more information see the:

- [Documentation](https://electric-sql.com/docs)
- [Quickstart](https://electric-sql.com/docs/quickstart)
- [Usage guide](https://electric-sql.com/docs/usage)

If you need help [let us know on Discord](https://discord.electric-sql.com).

# DEPLOYMENT AND PG NOTES

I went with Fly Postgres... app called my-app-pg (in bx account)
https://fly.io/docs/postgres/getting-started/what-you-should-know/

NOTE: You don't have a fly.toml (presumably because it could get mixed up with your actual app one..) so you have to explicitly specify the pg app name, e.g.:

`flyctl <command> -a my-app-pg`

Then, the "main app": named it electricsql-on-fly-test-app
Pasted the fly.toml data as ElectricSQL suggests, then overwrote the value for DATABASE_URL with the "connection string" value that came back from creating my-app-pg and added the DATABASE_USE_IPV6 = 'true' and DATABASE_REQUIRE_SSL = 'false'

Allocated dedicated ipv4: 149.248.221.49
Allocated dedicated ipv6: 2a09:8280:1::38:65f8:0

IT FAILED. Raised a github issue with Electric, as the message told me to..
