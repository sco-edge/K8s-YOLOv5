# Starlight installation
https://github.com/mc256/starlight

## Starlight helm package

### 설치 환경
2 VM  
Cloud  
VirtualBox with Ubuntu 22.04.4 LTS and `starlight v0.3.2`  
Edge  
WSL with Ubuntu 22.04.3 LTS and `starlight v0.3.2` 

### 설치

#### Cloud
```
CONTAINER ID   IMAGE                                  COMMAND                  CREATED             STATUS          PORTS                                       NAMES
ab6e266e97b7   adminer:latest                         "entrypoint.sh php -…"   About an hour ago   Up 5 seconds    0.0.0.0:8080->8080/tcp, :::8080->8080/tcp   compose_dbadmin_1
556c2a40ec67   ghcr.io/mc256/starlight/proxy:latest   "/opt/starlight-proxy"   About an hour ago   Up 2 seconds    0.0.0.0:8090->8090/tcp, :::8090->8090/tcp   compose_proxy_1
c44da6f90056   postgres:latest                        "docker-entrypoint.s…"   About an hour ago   Up 15 seconds   0.0.0.0:5432->5432/tcp, :::5432->5432/tcp   compose_db_1
fe471bfd1141   registry:2                             "/entrypoint.sh /etc…"   About an hour ago   Up 15 seconds   0.0.0.0:5000->5000/tcp, :::5000->5000/tcp   compose_registry_1
```

Registry and proxy are successfully up and running
```
curl http://cloud.cluster.local:8090/
# {"status":"OK","code":200,"message":"Starlight Proxy"}
curl http://cloud.cluster.local:5000/v2/
# {}
```

#### Edge



### 실험

리눅스에서 트래픽 컨트롤 기능을 제공하는 도구인 tc를 이용해서 RTT 제어  


#### tc 사용법

설정 초기화 및 확인
```
sudo tc qdisc del dev ens33 root
sudo tc -s qdisc ls dev wlan0
```
RTT 확인
```
ping -c 3 8.8.8.8
```
RTT 설정(200ms)
```
sudo tc qdisc add dev ens33 root netem delay 200ms
```



