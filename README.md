# Starlight installation
https://github.com/mc256/starlight
Starlight는 Golang<sup>[1](#footnote_1)</sup>으로 개발됨


## 배경

Docker uses file systems inspired by Unionfs, such as Aufs, to layer Docker images. As actions are done to a base image, layers are created and documented, such that each layer fully describes how to recreate an action. This strategy enables Docker's lightweight images, as only layer updates need to be propagated (compared to full VMs, for example). <sup>[2](#footnote_2)</sup>







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
sudo tc qdisc del dev enp0s3 root
sudo tc -s qdisc ls dev enp0s3
```
RTT 확인
```
ping -c 3 8.8.8.8
```
RTT 설정(200ms)
```
sudo tc qdisc add dev enp0s3 root netem delay 200ms
```


### 실험 수행

#### 초기화

#### 실험 
Starlight  
도커의 RTT=50ms부터 50ms 단위로 1000ms까지 증가시키면서 redis 6.2.1 컨테이너의 배포 시간 측정함

|RTT|1회차|2회차|3회차|4회차|5회차|
|---|---|---|---|---|---|
|50ms|3.165|2.923|2.901|4.298|2.890|
|100ms|5.385|5.467|5.572|6.819|6.774|
|150ms|8.160|8.034|11.203|7.886|7.876|
|200ms||---|---|---|---|
|250ms||---|---|---|---|
|300ms||---|---|---|---|
|350ms||---|---|---|---|

단위:second  
`docker pull redis:6.2.1`은 RTT=4ms에서 35.894s의 시간이 소요됨


<a name="footnote_1">[1]</a>: https://go.dev/
<a name="footnote_2">[2]</a>: https://en.wikipedia.org/wiki/UnionFS
