# Starlight installation
https://github.com/mc256/starlight

## 설치 환경
2 VM  
Cloud  
VirtualBox with Ubuntu 22.04.4 LTS and `starlight v0.3.2`  
Edge  
WSL with Ubuntu 22.04.3 LTS and `starlight v0.3.2` 

## 설치

### Cloud
VM  
Registry and proxy are successfully up and running
```
curl http://cloud.cluster.local:8090/
# {"status":"OK","code":200,"message":"Starlight Proxy"}
curl http://cloud.cluster.local:5000/v2/
# {}
```

### Edge
WSL  


## 실험 환경

리눅스에서 트래픽 컨트롤 기능을 제공하는 도구인 tc를 이용해서 RTT 제어  


### tc 사용법

설정 초기화 및 확인
```
sudo tc qdisc del dev ens33 root
sudo tc -s qdisc ls dev ens33
```
RTT 확인
```
ping -c 3 8.8.8.8
```
RTT 설정(200ms)
```
sudo tc qdisc add dev ens33 root netem delay 200ms
```


### 실험 수행

#### 초기화
실험 1회 수행시 다음을 반복함
```
rm -rf test-redis-data/
sudo ctr container rm instance3
sudo ./demo/reset.sh
sudo systemc행
