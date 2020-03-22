# Criando uma imagem do Prometheus

```
docker image pull prom/prometheus
docker image pull prom/node-exporter
```

```
docker run -dit --name PROMETHEUS -p 9090:9090 -i prom/prometheus -config.file=prometheus/prometheus.yml
docker run -dit --name PROMETHEUS -p 9090:9090 -v prometheus/prometheus.yml:/etc/prometheus/prometheus.yml -i prom/prometheus
docker run -dit --name PROMETHEUS -p 9090:9090 -v /home/vagrant/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml -i prom/prometheus 
docker run -dit --name NODE_EXPORTER -p 9100:9100 -v "/proc:/host/proc" -v "/sys:/host/sys" -v "/:/rootfs" --net="host" prom/node-exporter -collector.procfs /host/proc -collector.sysfs /host/proc -collector.filesystem.ignored-mount-points "^/(sys|proc|dev|host|etc)($|/)"
```

## Configurando o docker 
```
vim /etc/docker/daemon.json 

{
  "metrics-addr" : "192.168.57.80:9323",
  "experimental" : true
}
```


```
$ sudo systemctl restart docker
```




# Grafana
```
docker pull grafana/grafana
```

```
docker run -d --name=grafana -p 3000:3000 grafana/grafana
```
