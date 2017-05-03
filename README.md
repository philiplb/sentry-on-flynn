# Sentry on Flynn

```text
flynn create -y sentry

flynn resource add redis

flynn resource add postgres

flynn limit set slugbuilder memory=4GB

flynn env set SECRET_KEY=$(openssl rand -hex 32) SENTRY_URL_PREFIX=https://sentry.demo.localflynn.com/

git push flynn master

flynn run sentry --config=sentry.conf.py upgrade --noinput

flynn run sentry --config=sentry.conf.py createuser

flynn scale worker=1 beat=1
```

## Upgrading

After you have upgraded Sentry via a newer version of this repository, run the database migrations with this command:

```text
flynn run sentry --config=sentry.conf.py upgrade
```
