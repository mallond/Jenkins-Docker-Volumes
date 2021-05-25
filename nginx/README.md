


# Experimental Setup Jenkins
```
// Set Up Jenkins for experimental setup - Free running
docker run -p 8080:8080 -p 50000:50000 jenkins:2.60.3

// Create Certificate and Key
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout cert.key -out cert.crt

// Build Nginx Proxy that points to the above url specific running version
docker build . -t nginx-jenkins:0.0.1

Notes:
- reverse-proxy.config, be careful to pay attention to the IP address. Remember your container does not have the same local host as your desktop, you can lose lots of hours not seeing this concept. 
- Run on port other than 80. Spin up a new port via the docker build
- Run specify IP address in your url, localhost seems to have problems, and/or update your host file

```

# Experimental Setup Influx
```
// Set Up InfluxDB for experimental setup - Free running
docker run -p 8086:8086 -e DOCKER_INFLUXDB_INIT_USERNAME=admin -e DOCKER_INFLUXDB_INIT_PASSWORD=password -v influxdb:/var/lib/influxdb influxdb:2.0.6

// Create Certificate and Key
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout cert.key -out cert.crt

// Build Nginx Proxy that points to the above url specific running version
docker build . -t nginx-influxdb:0.0.1

```

# Experimental Setup Grafana
```
// Set Up Grafana for experimental setup - Free running
docker run -d -p 3000:3000 --name=grafana  -v grafana-storage:/var/lib/grafana grafana/grafana
# user/pwd initial admin/admin

// Create Certificate and Key
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout cert.key -out cert.crt

// Build Nginx Proxy that points to the above url specific running version
docker build . -t nginx-grafana:0.0.1


```