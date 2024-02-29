# Run migrations automatically

When there are changes to your Prisma schema you want to run migrations to update your database.
This is how I'm doing it in my current project, which is using yarn workspaces, and deploys via a Docker container:

# Local Migrations

For local development, I'm using `concurrently` to start up PostgreSQL in a Docker container, and then the React `client` dev server and the Express `server`.
Before the database is started, it calls this package.json script to run migrations:

```
"prisma:init": "yarn workspace server prisma migrate dev --name init",
```

I do need to quit my `yarn start` process and restart it to update the database, but it's a decent enough workflow for now.


# Production Migrations
In my `server` workspace in my project, I have a script in `package.json` like this, which will run the production migration:

```
"prisma:update": "yarn prisma migrate deploy"
```

In my `Dockerfile` I run that script before starting the server:

```Dockerfile
CMD yarn prisma:update && node server.ts
```

This ensures that the database is updated before the server starts up.