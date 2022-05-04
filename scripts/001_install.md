# 001. install



<br>



### environment

- linux ubuntu 



<br>



#### install jdk

```
apt-get install openjdk-11-jdk
```



<br>



#### zookeeper install

설치를 위한 website 방문 https://zookeeper.apache.org/releases.html

<img src="https://user-images.githubusercontent.com/46165696/166267926-2b894250-d0ea-439b-8173-5969c7bc8f03.png"> 



<br>



##### zookeeper download

<img src="https://user-images.githubusercontent.com/46165696/166273255-1ae7b532-f8ae-4d48-b292-575cfd11b983.png">

```
cd /usr/local/

wget https://dlcdn.apache.org/zookeeper/zookeeper-3.8.0/apache-zookeeper-3.8.0-bin.tar.gz

tar zxf apache-zookeeper-3.8.0-bin.tar.gz
```



<br>



#### 심볼릭 링크 생성

매번 사용하기에는 너무 긴 이름에 대해 심볼릭 링크(별칭)를 적용한다.

```
ln -s apache-zookeeper-3.8.0-bin zookeeper
```

##### 적용 확인

<img src="https://user-images.githubusercontent.com/46165696/166282013-341bb5f3-afb1-4f13-b87b-421d7db67d30.png">



<br>



:bulb: zookeeper는 애플리케이션에서 별도의 데이터 디렉토리를 사용하는데, 이 디렉토리에는 지노드의 복사본인 스냅샷과 트랜잭션 로그들이 저장.

-> 중요 정보들이기 때문에 설치 경로와는 다른 경로로 설정하는 것이 바람직 !



<br>



다른 경로 설정

```
mkdir -p /data
```



환경 설정 파일 생성

```
vi /usr/local/zookeeper/conf/zoo.cfg
```

후 작업

```
tickTime=2000
initLimit=10
syncLimit=5
dataDir=/data
clientPort=2181
server.1=yaans-zk001:2888:3888
server.2=yaans-zk002:2888:3888
server.3=yaans-zk003:2888:3888
```

` dataDir=/data`이 바로 **주키퍼의 트랜잭션 로그와 스냅샷이 저장되는 데이터 저장 경로 설정** 부분



<br>



#### 주키퍼 실행

```
/usr/local/zookeeper/bin/zkServer.sh start
```

##### 주키퍼 중지

```
/usr/local/zookeeper/bin/zkServer.sh stop
```

<img src="https://user-images.githubusercontent.com/46165696/166290208-ce1bf340-2fe6-4a2a-9f99-92239cd2346d.png">



<br>

