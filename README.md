# Starlight installation
https://github.com/mc256/starlight

## Starlight helm package

### 설치 환경
운영체제: Ubuntu 22.04  
쿠버네티스: k3s

### 설치 진행 상황

#### Local Path Provisioner
https://github.com/rancher/local-path-provisioner  
Local path provisioner를 이용하여 persistent storage 사용

#### Starlight Daemon 에지 노드에 설치 및 containerd 연결
k3s 환경 사용하므로 containerd의 소켓 주소 변경 필요


