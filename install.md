## install zookeeper

- zookeeper를 설치하기 전, java를 먼저 설치해줘야 합니다
<br>

```shell
cd /usr/local/
```

<br>

```shell
wget https://mirror.navercorp.com/apache/zookeeper/zookeeper-3.7.0/apache-zookeeper-3.7.0-bin.tar.gz
```
result
```
--2022-03-25 06:55:16--  https://mirror.navercorp.com/apache/zookeeper/zookeeper-3.7.0/apache-zookeeper-3.7.0-bin.tar.gz
Resolving mirror.navercorp.com (mirror.navercorp.com)... 125.209.216.167
Connecting to mirror.navercorp.com (mirror.navercorp.com)|125.209.216.167|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12387614 (12M) [application/octet-stream]
Saving to: ‘apache-zookeeper-3.7.0-bin.tar.gz’

apache-zookeeper-3. 100%[==================>]  11.81M  8.97MB/s    in 1.3s    

2022-03-25 06:55:17 (8.97 MB/s) - ‘apache-zookeeper-3.7.0-bin.tar.gz’ saved [12387614/12387614]
```

<br>

```shell
tar zxf apache-zookeeper-3.7.0-bin.tar.gz
```


<br>

- 심볼릭 링크 생성 
```shell
ln -s apache-zookeeper-3.7.0-bin zookeeper

ls -la zookeeper
```

result
```
lrwxrwxrwx 1 root root 26 Mar 25 07:00 zookeeper -> apache-zookeeper-3.7.0-bin
```


<br>

- 주키퍼의 환경설정 파일 생성
```shell
vi /usr/local/zookeeper/conf/zoo.cfg
```
 - 작성할 파일 내용

    ```
    tickTime=2000
    initLimit=10
    syncLimit=5
    dataDir=/data
    clientPort=2181
    server.1=peter-zk001:2888:3888
    server.2=peter-zk001:2888:3888
    server.3=peter-zk001:2888:3888
    ```

<br>

```shell
```