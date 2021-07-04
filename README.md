# kubernetes_percona_psql
## Installing Percona Postgresql in Kubernetes
### Option 1
Build docker image from https://github.com/tixsalvador/patroni/tree/master/kubernetes
```sh
$ git clone https://github.com/tixsalvador/patroni.git
$ cd patroni/kubernetes
$ docker build -t patroni .
```
