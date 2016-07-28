# Sentry on Flynn

```text
flynn create -y sentry

flynn resource add redis

flynn resource add postgres

flynn limit set slugbuilder memory=4GB

flynn env set SECRET_KEY=$(openssl rand -hex 32) SENTRY_URL_PREFIX=https://sentry.mycluster.com

git push flynn master

flynn run sentry --config=sentry.conf.py upgrade --noinput

flynn run sentry --config=sentry.conf.py createuser

flynn scale worker=1 beat=1
```
