# Build

## Build refactored redis Nulecule app

```
[sudo] docker build -t pa/redis ../redis-centos7-atomicapp/

```

## Build refactored postgresql Nulecule app

```
[sudo] docker build -t pa/pg ../postgresql-centos7-atomicapp/
```

## Build refactored  sentry app

```
[sudo] docker build -t projectatomic/sentry .
```

# Run

- Copy ``answers.conf.sample`` to ``answers.conf`` and customize as needed.

```
[sudo] atomicapp run --provider kubernetes projectatomic/sentry
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

# Usage

## Kubernetes

- Setup sentry: ``kubectl exec -ti sentry sentry upgrade``

- Open ``http://10.254.131.20:9000`` in browser to access Sentry.

