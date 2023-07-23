# A GlassFish cluster with Apache loadbalancer in Docker

You'll get a cluster with 3 instances, Admin Console, Apache loadbalancer.

The GlassFish Admin Console will be available at:

* https://localhost:14848 (not the default 4848 ! )
* admin user:     `admin`
* admin password: `admin`

A sample application clusterjsp will be deployed on the cluster. It will be available at the following address:

* https://localhost:44443/clusterjsp

## Start the cluster

In the root directory, start all containers using Docker compose:

``
docker compose up -d --build
``

## Administer the cluster

You can configure the GlassFish cluster in the Admin Console.

You can open terminal for each server:
* Admin Console: `docker exec -it glassfish-apache-cluster-gfadmin-1 bash`
* Instance 1: `docker exec -it glassfish-apache-cluster-gfnode1-1 bash`
* Instance 2: `docker exec -it glassfish-apache-cluster-gfnode2-1 bash`
* Instance 3: `docker exec -it glassfish-apache-cluster-gfnode3-1 bash`
* Apache Server: `docker exec -it glassfish-apache-cluster-apache-1 bash`

## Configuration

### Apache server

* Persistent configuration in `apache/httpd.conf`
* Configuration in the container: `/usr/local/apache2/conf/httpd.conf`
* See: https://hub.docker.com/_/httpd

### GlassFish

* Persistent configuration in `glassfish-admin/setup.commands` - list of asadmin commands that are executed when docker containers are created
* Configuration in the container: 
  * edit in Admin Console
  * or open the terminal for the container (`docker exec -it glassfish-apache-cluster-gfadmin-1 bash`) and use `bin/asdadmin` as usual