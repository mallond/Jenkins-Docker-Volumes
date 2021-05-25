# Docker Container QA Tooling

> Nginx-Reverse-Proxy Jenkins InfluxDB Graphana - Dockerized 

## Install Docker
```
sudo snap install docker
```

# Volumes - Why? First reason is backup!
##  target /var/jenkins_home
```
# target /var/jenkins_home
mkdir data/jenkins_home -p
chmod -R 777 data/jenkins_home
sudo chown cloud_user:cloud_user data/jenkins_home
e05ae6b0fe63411caf0cf512f1426088
```
## target /var/lib/influxdb2
```
mkdir data/influxdb2 -p
chmod -R 777 data/influxdb2
sudo chown cloud_user:cloud_user data/influxdb2
```

## target /var/lib/grafana
```
mkdir data/grafana
chmod -R 777 data/grafana
sudo chown cloud_user:cloud_user data/grafana
```

# Services
## Jenkins
```
docker run -d --restart unless-stopped -p 8080:8080 -p 50000:50000 -v ~/data/jenkins_home:/var/jenkins_home jenkins:2.60.3 
```

## InfluxDB
```

docker run --restart unless-stopped -p 8086:8086 \
      -v ~/data/influxdb2:/var/lib/influxdb2 \
      -e DOCKER_INFLUXDB_INIT_USERNAME=admin \
      -e DOCKER_INFLUXDB_INIT_PASSWORD=password \
      -e DOCKER_INFLUXDB_INIT_ORG=everi.com \
      -e DOCKER_INFLUXDB_INIT_BUCKET=everi \
      influxdb:2.0
          

```

## Graphana
```
docker run -d  --restart unless-stopped -p 3000:3000 --name=grafana -v ~/data/grafana:/var/lib/grafana grafana/grafana:7.5.7-ubuntu
# user/pwd admin/admin - please change


```

