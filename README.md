# Docker Container QA Tooling

> Nginx-Reverse-Proxy Jenkins InfluxDB Graphana - Dockerized 

## Install Docker
```
sudo snap install docker
```

## Volumes
```
# target /var/jenkins_home
mkdir data/jenkins_home
chmod -R 777 data/jenkins_home
e05ae6b0fe63411caf0cf512f1426088

```
```
# target /var/lib/influxdb2
mkdir data/influxdb2
```
```
# target /var/lib/grafana
mkdir data/grafana
```
## Jenkins
```
docker run -p 8080:8080 --restart unless-stopped -p 50000:50000 -v ~/data/jenkins_home:/var/jenkins_home jenkins:2.60.3
# add the -d for deamon 
```

## InfluxDB

## Graphana

