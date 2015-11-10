# Build

```
[sudo] docker build -t projectatomic/sentry .
```

# Run

- Copy ``answers.conf.sample`` to ``answers.conf`` and customize as needed.

```
[sudo] atomic run projectatomic/sentry
```

## Kubernetes

Run ``kubectl get pods`` to check if the pods for ``redis``, ``postgres``
and ``sentry`` are up and running.

Check info for ``sentry`` service.

```
$ kubectl get services sentry
NAME      LABELS        SELECTOR      IP(S)           PORT(S)
sentry    name=sentry   name=sentry   10.254.131.20   9000/TCP
```

## Docker

Run ``sudo docker ps`` to check if the containers for sentry are running.

```
CONTAINER ID        IMAGE                                  COMMAND                  CREATED             STATUS              PORTS                     NAMES
e0c500f83ea8        rtnpro/sentry                          "/docker-entrypoint.s"   2 seconds ago       Up 2 seconds        0.0.0.0:30001->9000/tcp   sentry
dc6a8ef80731        redis                                  "/entrypoint.sh redis"   3 seconds ago       Up 2 seconds        6379/tcp                  sentry_redis
0b8c51d12644        postgres                               "/docker-entrypoint.s"   3 seconds ago       Up 3 seconds        5432/tcp                  sentry_postgres
```

# Usage

## Kubernetes

- Setup sentry: ``kubectl exec -ti sentry sentry upgrade``

- Open ``http://10.254.131.20:9000`` in browser to access Sentry.

## Docker
- Setup sentry: ``sudo docker exec -ti sentry sentry upgrade``
- Open ``http://localhost:30001`` in browser to access Sentry.
