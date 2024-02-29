# Connect to PostgreSQL DB

If you want to connect to your Fly.io database, you can do it via `flyctl`.

Make sure you have `flyctl` installed:

```bash
brew install flyctl
```

Connect to the DB:
```bash
flyctl postgresql connect -a database-app-name
```

Make sure `database-app-name` is the database app. 
It's not the name of your actual application. 
Check your [dashboard](https://fly.io/dashboard) for the app names.


More info: https://fly.io/docs/postgres/connecting/connecting-with-flyctl/