# A GlassFish cluster with Apache loadbalancer in Docker

You'll get a cluster with 3 instances, Admin Console, Apache loadbalancer.
A sample application clusterjsp will be deployed on the cluster. It will be available at the following addresses:

* https://localhost:28181/clusterjsp
* https://localhost:28182/clusterjsp
* https://localhost:28183/clusterjsp

## 1. Build GlassFish Admin docker image

Run the following:

```
docker build --pull --rm -t gf-cluster-admin glassfish-admin
```

## 2. Build GlassFish Node docker image

In the directory `glassfish-node`, run the following:

```
docker build --pull --rm -t gf-cluster-node glassfish-node
```

## 3. Build Apache docker image

To do...

## 4. Start the cluster

In the root directory (make sure that the directory is named `glassfish-apache-cluster`), start all containers using Docker compose:

``
docker compose -f "docker-compose.yml" up -d --build
``


## 5. Setup the cluster after docker compose started:

```
docker run -e AS_ADMIN_HOST=gfadmin --rm --network=glassfish-apache-cluster_default gf-cluster-admin:latest ./setup
```

where `glassfish-apache-cluster` is the name of the directory where the `docker-compose.yml`` file is located.

## When done, stop everything

Run

```
docker compose -f "docker-compose.yml" down
```