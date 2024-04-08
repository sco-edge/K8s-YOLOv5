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


Registry and proxy are successfully up and running
```
curl http://cloud.cluster.local:8090/
# {"status":"OK","code":200,"message":"Starlight Proxy"}
curl http://cloud.cluster.local:5000/v2/
# {}
```

#### Edge



### 실험

#### tc 사용법

설정 초기화 및 확인
```
sudo tc qdisc del dev ens33 root
sudo tc -s qdisc ls dev wlan0
```


