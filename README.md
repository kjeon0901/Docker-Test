# Docker-Test



### Docker란 무엇인가

애플리케이션을 환경에 구애받지 않고 신속하게 구축, 테스트 및 배포할 수 있는 소프트웨어 플랫폼. 

소프트웨어를 컨테이너라는 표준화된 유닛으로 패키징하며, **컨테이너에는 라이브러리, 시스템 도구, 코드, 런타임 등 소프트웨어를 실행하는 데 필요한 모든 것이 포함**되어 있음. 

AWS에서 Docker를 실행하면 개발자와 관리자가 어떤 규모에서든 매우 안정적이며 저렴한 방식으로 애플리케이션을 구축, 제공 및 실행 가능



### Docker를 사용하는 이유

- 개선되고 완벽한 이식성
- 보다 경량의 중량, 보다 미세한 업데이트
- 자동화된 컨테이너 작성
- 컨테이너 버전화
- 컨테이너 재사용
- 공유 컨테이너 라이브러리



### Docker 용어

**DockerFile**
모든 Docker 컨테이너는 이미지의 빌드 방법에 대한 지시사항이 포함된 단순 텍스트 파일로 시작됨. DockerFile은 Docker 이미지 작성 프로세스를 자동화함

**Docker 이미지**
실행 가능한 애플리케이션 소스 코드, 그 코드가 컨테이너로서 실행해야 하는 모든 툴, 라이브러리 및 종속 항목들이 포함됨. 버전에 따라 계층별로 되고, 개발자가 이미지 변경할 때마다 최상의 계층이 됨. 

**Docker 컨테이너**
Docker 이미지의 실행 중인 라이브 인스턴스. 이미지는 읽기 전용 파일이지만, 컨테이너는 라이브, 임시, 실행 가능 콘텐츠. 사용자는 Docker 컨테이너들과 상호작용할 수 있고, 관리자는 docker 명령을 사용해 자체 설정과 조건을 조정.

**Docker 허브**
컨테이너 이미지의 세계 최대 라이브러리 및 커뮤니티라고 불리는 Docker 이미지의 공용 저장소. 엄청 많은 이미지들을 바로 로컬로 다운받거나 직접 공유할 수도 있음. 
대부분 회사에서는 자체 Docker 허브 레지스트리를 구축. 왜냐하면 사용하고 있다가 서버가 다운되거나 회사가 사용해온 nginx 버전같은 걸 Docker 허브에서 삭제해서 막아버리면 계속 이미지를 요청해올 때 서비스에 타격이 있으니까. 

**Docker 레지스트리**
저장소에서 이미지 버전을 추적할 수 있음



### Docker Architecture

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c9801c9e-8a21-44ac-bd79-0302600c82c9/Untitled.png)

**Docker Deamon**
Docker의 API 요청을 수신하고 이미지, 컨테이너, 네트워크 및 볼륨과 같은 Docker 개체 관리. 다른 데몬과 통신하여 Docker 서비스 관리함.

**Docker Client**
데몬으로 도커를 사용하는 방법

**Docker Desktop**
Docker Deamon, Docker Client, Docker Compose, Kubernetes 등이 포함됨. 로컬에서 Docker 파일이 실행이 안 되는 경우는 사용하지 않는 이미지 파일을 삭제하거나 cpu 크기 조정해주기. 

**Docker Registry**
공용 레지스트리



### Docker 오케스트레이션

- 소수의 컨테이너만 실행하는 경우는 런타임인 Docker Engine 내에서 애플리케이션 관리하기 쉽지만, 배치가 수천 개의 컨테이너와 수천 개의 이미지일 경우 오케스트레이션으로 관리 .

**Docker Compose**
모두 동일한 호스트에 상주하는 다중 컨테이너의 프로세스에서 애플리케이션을 빌드하는 경우 Docker Compose를 사용하여 애플리케이션의 아키텍쳐를 관리할 수 있음. ELK : Elasticsearch + Logstash + Kibana 는 세 개를 각각 하지 말고 Docker Compose에서 한 번에 해줄 수 있음. 

**Kubernetes**
컨테이너 라이프사이클 모니터링과 관리. Google이 쓰고 Google에서 관리되고 있어서, 레퍼런스가 많아서 사람들이 많이 사용. 단점은 공부할 게 너무 많고 진입 장벽이 높음. 컨테이너가 죽어도 알아서 관리해줌. 



### Docker Conference

[DockerCon 2022](https://docker.events.cube365.net/dockercon/2022)



### Docker 관련 기술 블로그

**[If kakao conference]**- Docker Swarm 기반 Redis SaaS 플랫폼 구축 사례
[if(kakao)dev2022](https://if.kakao.com/2022/session/26)

**[naver tech blog]**
[NAVER D2](https://d2.naver.com/search?keyword=docker)

**[심심하실 때..]**
[if(kakao)2021](https://elseif.kakao.com/2019/program?sessionId=aea80282-879c-4af8-9e88-86a27c454d4b)


---



### Semantic Versioning 2.0.0

1. MAJOR 기존 버전과 호환되지 않게 API가 바뀐 경우
    
    1.1.1 → 2.1.1
    
2. MINOR 새로운 기능 추가된 경우
    
    1.1.1 → 1.2.1
    
3. PATCH 기존 버전과 호환되면서 버그 수정한 경우
    
    1.1.1 → 1.1.2
    


### Docker 실습

```cmd
Microsoft Windows [Version 10.0.22621.1105]
(c) Microsoft Corporation. All rights reserved.

// Docker 백그라운드로 실행 (-d : detach. 백그라운드)
C:\Windows\System32>docker run -d -p 80:80 docker/getting-started
Unable to find image 'docker/getting-started:latest' locally
latest: Pulling from docker/getting-started
c158987b0551: Pull complete
1e35f6679fab: Pull complete
cb9626c74200: Pull complete
b6334b6ace34: Pull complete
f1d1c9928c82: Pull complete
9b6f639ec6ea: Pull complete
ee68d3549ec8: Pull complete
33e0cbbb4673: Pull complete
4f7e34c2de10: Pull complete
Digest: sha256:d79336f4812b6547a53e735480dde67f8f8f7071b414fbd9297609ffb989abc1
Status: Downloaded newer image for docker/getting-started:latest
e6d27152b102e66007bffd9244c67ed6558d05232b44c38061e8d4bd3ec03ec3

C:\Windows\System32>docker -v
Docker version 20.10.22, build 3a2c30b

C:\Windows\System32>docker pull mysql
Using default tag: latest
latest: Pulling from library/mysql
197c1adcd755: Pull complete
45f2e353f7d2: Pull complete
68ec6ece42ef: Pull complete
cfa4d9a7b88e: Pull complete
64cab5858b1d: Pull complete
92fcd248d982: Pull complete
88635e83312d: Pull complete
43f0427259d9: Pull complete
79828698a290: Pull complete
a8854781893e: Pull complete
6c8bdf3091d9: Pull complete
Digest: sha256:8653a170e0b0df19ea95055267def2615fc53c62df529e3750817c1a886485f0
Status: Downloaded newer image for mysql:latest
docker.io/library/mysql:latest

// 이미지 리스트

C:\Windows\System32>docker images
REPOSITORY                                                TAG                                                                          IMAGE ID       CREATED         SIZE
mysql                                                     latest                                                                       57da161f45ac   12 days ago     517MB
gcr.io/k8s-minikube/kicbase                               v0.0.37                                                                      01c0ce65fff7   3 weeks ago     1.15GB
docker/getting-started                                    latest                                                                       3e4394f6b72f   2 months ago    47MB
hubproxy.docker.internal:5000/docker/desktop-kubernetes   kubernetes-v1.25.4-cni-v1.1.1-critools-v1.25.0-cri-dockerd-v0.2.6-1-debian   2511e1796e7d   2 months ago    398MB
registry.k8s.io/kube-apiserver                            v1.25.4                                                                      00631e54acba   3 months ago    128MB
registry.k8s.io/kube-proxy                                v1.25.4                                                                      2c2bc1864279   3 months ago    61.7MB
registry.k8s.io/kube-scheduler                            v1.25.4                                                                      e2d17ec744c1   3 months ago    50.6MB
registry.k8s.io/kube-controller-manager                   v1.25.4                                                                      8f59f6dfaed6   3 months ago    117MB
registry.k8s.io/etcd                                      3.5.5-0                                                                      4694d02f8e61   5 months ago    300MB
registry.k8s.io/pause                                     3.8                                                                          4873874c08ef   8 months ago    711kB
registry.k8s.io/coredns/coredns                           v1.9.3                                                                       5185b96f0bec   8 months ago    48.8MB
docker/desktop-vpnkit-controller                          v2.0                                                                         8c2c38aa676e   21 months ago   21MB
docker/desktop-storage-provisioner                        v2.0                                                                         99f89471f470   22 months ago   41.9MB

// 컨테이너 생성과 동시에 백그라운드로 컨테이너 실행 (-e : environment)
// --name 풀네임은 -- 두 개
// -e 약자는 - 한 개

C:\Windows\System32>docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=KJEON0901Q1W2E3R4 -d -p 3306:3306 mysql:latest
bac25a9c9d1b91e7650243759b23a9c5eb61b9d4f143bfc44dea7572ceeb5130

// 컨테이너 리스트

C:\Windows\System32>docker ps -a
CONTAINER ID   IMAGE                                 COMMAND                  CREATED          STATUS                      PORTS                               NAMES
bac25a9c9d1b   mysql:latest                          "docker-entrypoint.s…"   46 seconds ago   Up 45 seconds               0.0.0.0:3306->3306/tcp, 33060/tcp   mysql-container
e6d27152b102   docker/getting-started                "/docker-entrypoint.…"   13 minutes ago   Up 13 minutes               0.0.0.0:80->80/tcp                  wizardly_germain
0d1caa9c4ed9   gcr.io/k8s-minikube/kicbase:v0.0.37   "/usr/local/bin/entr…"   22 hours ago     Exited (130) 22 hours ago                                       minikube

// 컨테이너 중지 : docker stop mysql-container
// 컨테이너 시작 : docker start mysql-container
// 컨테이너 재시작 : docker restart mysql-container

// 컨테이너를 bash로 접속

C:\Windows\System32>docker exec -it mysql-container bash
bash-4.4# mysql -u root -p         // bash에서 컨테이너로 접근 (-p : 패스워드 입력)
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.32 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>    // mysql 접속 완료 !

----------------------------------------------------------------

// Docker MySQL 테이블 생성, 등록, 조회 해보기
// 데이터베이스 확인

mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.00 sec)

// docker_users 라는 데이터베이스 생성

mysql> CREATE DATABASE docker_users;
Query OK, 1 row affected (0.01 sec)

mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| docker_users       |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)

// docker_users 데이터베이스 안에 users 테이블 생성

mysql> USE docker_users;
Database changed
mysql> CREATE TABLE users (
    -> id int NOT NULL AUTO_INCREMENT PRIMARY KEY,
    -> name varchar(55) NOT NULL
    -> );
Query OK, 0 rows affected (0.04 sec)

// 데이터 등록

mysql> INSERT INTO users (name) VALUES ('chungnam');
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO users (name) VALUES ('university');
Query OK, 1 row affected (0.01 sec)

// 데이터 조회하기

mysql> SELECT * FROM users;
+----+------------+
| id | name       |
+----+------------+
|  1 | chungnam   |
|  2 | university |
+----+------------+
2 rows in set (0.00 sec)

mysql> quit
Bye
bash-4.4# exit
exit

---------------------------------------------------------------

C:\Windows\System32>docker pull bitnami/postgresql
Using default tag: latest
latest: Pulling from bitnami/postgresql
089af92e8575: Pull complete
Digest: sha256:a18fde65055e5a9571b1d28683220057f2401919189ca1fe62f934165fc980f7
Status: Downloaded newer image for bitnami/postgresql:latest
docker.io/bitnami/postgresql:latest

C:\Windows\System32>docker images
REPOSITORY                                                TAG                                                                          IMAGE ID       CREATED         SIZE
bitnami/postgresql                                        latest                                                                       fced759f9dc5   3 days ago      275MB
mysql                                                     latest                                                                       57da161f45ac   12 days ago     517MB
gcr.io/k8s-minikube/kicbase                               v0.0.37                                                                      01c0ce65fff7   3 weeks ago     1.15GB
docker/getting-started                                    latest                                                                       3e4394f6b72f   2 months ago    47MB
hubproxy.docker.internal:5000/docker/desktop-kubernetes   kubernetes-v1.25.4-cni-v1.1.1-critools-v1.25.0-cri-dockerd-v0.2.6-1-debian   2511e1796e7d   2 months ago    398MB
registry.k8s.io/kube-apiserver                            v1.25.4                                                                      00631e54acba   3 months ago    128MB
registry.k8s.io/kube-controller-manager                   v1.25.4                                                                      8f59f6dfaed6   3 months ago    117MB
registry.k8s.io/kube-scheduler                            v1.25.4                                                                      e2d17ec744c1   3 months ago    50.6MB
registry.k8s.io/kube-proxy                                v1.25.4                                                                      2c2bc1864279   3 months ago    61.7MB
registry.k8s.io/etcd                                      3.5.5-0                                                                      4694d02f8e61   5 months ago    300MB
registry.k8s.io/pause                                     3.8                                                                          4873874c08ef   8 months ago    711kB
registry.k8s.io/coredns/coredns                           v1.9.3                                                                       5185b96f0bec   8 months ago    48.8MB
docker/desktop-vpnkit-controller                          v2.0                                                                         8c2c38aa676e   21 months ago   21MB
docker/desktop-storage-provisioner                        v2.0                                                                         99f89471f470   22 months ago   41.9MB

C:\Windows\System32>docker run --name postgresql-container -e POSTGRESQL_ROOT_PASSWORD=KJEON0901Q1W2E3R4 -d -p 5432:5432 bitnami/postgresql:latest
f80f7c867db1a45de8d9c7e7f16775430ccded043738c255a107938d3473c1e4

```


Dockerfile

: 텍스트 파일이고 build 시 사용될 명령어들을 모아놓은 것

Build Context

: PATH 또는 URL을 통해 지정된 다수의 파일을 갖는 경로(위치)

```jsx
// 1) helloworld 파일 생성

#! /bin/sh
echo Hello, World!

// 2) Dockerfile 생성

FROM alpine:latest
COPY helloworld /usr/local/bin   // 로컬 현재 디렉토리의 helloworld 파일을 도커 컨테이너 내부의 /usr/local/bin 폴더로 복사
RUN chmod +x /usr/local/bin/helloworld

CMD ["helloworld"]

// 3) Dockerfile 빌드 및 실행 => docker build . : 현재 경로(.)를 build context로 지정
// build context : 

docker build -t helloworld:latest .   // -t : tag. helloworld의 태그를 latest(default)로 정함
docker run helloworld
docker image ls
```


---


1. Docker Hub 가입
2. Dockerfile 만들기
    1. ubuntu 최신 버전으로 base image 만들기
        
        **FROM ubuntu:latest**
        
        **MAINTAINER kjeon0901 <kjeon0901@naver.com>**
        
        **CMD[”echo”, “Hello CNU World!”]**
        
    2. Dockerfile 빌드
        
        **docker build —tag kjeon0901/test-repository:latest .**
        
3. Docker Hub에 이미지 올리기
    
    **docker login**
    
    **docker push kjeon0901/test-repository**
    

---


1. [app.py](http://app.py/) 파일 생성

```cmd
from flask import Flask
app = Flask(**name**)

@app.route("/")
def hello():
return "Hello World!"

if **name** == "**main**":
app.run(host='0.0.0.0')
```

2. Dockerfile 생성

```cmd
FROM python:3.8-slim
COPY . /app
RUN pip3 install flask
WORKDIR /app
CMD ["python3", "-m", "flask", "run", "--host=0.0.0.0"]
```

3. Dockerfile 빌드 및 실행

```cmd
docker build -t flask_test .
docker run -p 5001:5000 flask_test
curl localhost:5001
docker ps
docker inspect flask_test
```
