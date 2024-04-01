# Starlight installation
https://github.com/mc256/starlight

## Starlight helm package

### 설치 환경
AWS EC2 t3.micro with Ubuntu 22.04 LTS and `starlight v0.3.2`

### 설치 진행 상황

#### Cloud

AWS EC2 Free tier:750h/month
Registry and proxy are successfully up and running
```
curl http://cloud.cluster.local:8090/
# {"status":"OK","code":200,"message":"Starlight Proxy"}
curl http://cloud.cluster.local:5000/v2/
# {}
```

#### Edge
