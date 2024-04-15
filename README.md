# Starlight installation
https://github.com/mc256/starlight

## 배경

Docker uses file systems inspired by Unionfs, such as Aufs, to layer Docker images. As actions are done to a base image, layers are created and documented, such that each layer fully describes how to recreate an action. This strategy enables Docker's lightweight images, as only layer updates need to be propagated (compared to full VMs, for example). <sup>[1](#footnote_1)</sup>







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

#### 실험 
Starlight  
RTT=100ms부터 100ms 단위로 1000ms까지 증가시키면서 redis 6.2.1 컨테이너의 배포 시간 측정함

|RTT|배포 시간|
|---|---|
|104ms|1.270s|
|204ms|2.089s|
|304ms|2.807s|
|404ms|3.068s|
|504ms|3.707s|
|604ms|4.279s|
|704ms|4.847s|

`docker pull redis:6.2.1`은 RTT=4ms에서 35.894s의 시간이 소요됨



<a name="footnote_1">[1]</a>: https://en.wikipedia.org/wiki/UnionFS
