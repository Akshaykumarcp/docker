### 1. Build the project

```PS J:\VSCODE_WORKSPACE\mongodb\Keep-Track-of-Number-of-User> docker-compose build
Building web
[+] Building 2.3s (10/10) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                              0.0s
 => => transferring dockerfile: 32B                                                                                                                               0.0s 
 => [internal] load .dockerignore                                                                                                                                 0.0s 
 => => transferring context: 2B                                                                                                                                   0.0s 
 => [internal] load metadata for docker.io/library/python:3                                                                                                       2.0s 
 => [1/5] FROM docker.io/library/python:3@sha256:db428075304d53783f6c7bdf075a47597464b79fac81622c58b92daf170c4af3                                                 0.0s
 => [internal] load build context                                                                                                                                 0.0s 
 => => transferring context: 4.95kB                                                                                                                               0.0s 
 => CACHED [2/5] WORKDIR /usr/src/app                                                                                                                             0.0s 
 => CACHED [3/5] COPY requirements.txt ./                                                                                                                         0.0s 
 => CACHED [4/5] RUN pip install --no-cache-dir -r requirements.txt                                                                                               0.0s 
 => [5/5] COPY . .                                                                                                                                                0.0s 
 => exporting to image                                                                                                                                            0.1s
 => => exporting layers                                                                                                                                           0.0s 
 => => writing image sha256:f961580bf679321b1e0b5b73f989e21218aa2517911fec5e41beb3121a7f0690                                                                      0.0s 
 => => naming to docker.io/library/keep-track-of-number-of-user_web                                                                                               0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

### 2. Start the docker image

```PS J:\VSCODE_WORKSPACE\mongodb\Keep-Track-of-Number-of-User> docker-compose up   
Starting keep-track-of-number-of-user_db_1 ... done
Recreating keep-track-of-number-of-user_web_1 ... done
Attaching to keep-track-of-number-of-user_db_1, keep-track-of-number-of-user_web_1
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten] MongoDB starting : pid=1 port=27017 dbpath=/data/db 64-bit host=c134bc9d9d0c
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten] db version v3.6.4
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten] git version: d0181a711f7e7f39e60b5aeb1dc7097bf6ae5856
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten] OpenSSL version: OpenSSL 1.0.1t  3 May 2016
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten] allocator: tcmalloc
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten] modules: none
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten] build environment:
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten]     distmod: debian81
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten]     distarch: x86_64
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten]     target_arch: x86_64
db_1   | 2022-04-08T00:46:01.009+0000 I CONTROL  [initandlisten] options: { net: { bindIpAll: true } }
db_1   | 2022-04-08T00:46:01.009+0000 I -        [initandlisten] Detected data files in /data/db created by the 'wiredTiger' storage engine, so setting the active storage engine to 'wiredTiger'.
db_1   | 2022-04-08T00:46:01.009+0000 I STORAGE  [initandlisten]
db_1   | 2022-04-08T00:46:01.009+0000 I STORAGE  [initandlisten] ** WARNING: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine       
db_1   | 2022-04-08T00:46:01.009+0000 I STORAGE  [initandlisten] **          See http://dochub.mongodb.org/core/prodnotes-filesystem
db_1   | 2022-04-08T00:46:01.009+0000 I STORAGE  [initandlisten] wiredtiger_open config: create,cache_size=1434M,session_max=20000,eviction=(threads_min=4,threads_max=4),config_base=false,statistics=(fast),cache_cursors=false,log=(enabled=true,archive=true,path=journal,compressor=snappy),file_manager=(close_idle_time=100000),statistics_log=(wait=0),verbose=(recovery_progress),
db_1   | 2022-04-08T00:46:02.029+0000 I STORAGE  [initandlisten] WiredTiger message [1649378762:29587][1:0x7f528fbd7a00], txn-recover: Main recovery loop: starting at 1/16000
db_1   | 2022-04-08T00:46:02.111+0000 I STORAGE  [initandlisten] WiredTiger message [1649378762:111652][1:0x7f528fbd7a00], txn-recover: Recovering log 1 through 2     
db_1   | 2022-04-08T00:46:02.167+0000 I STORAGE  [initandlisten] WiredTiger message [1649378762:167839][1:0x7f528fbd7a00], txn-recover: Recovering log 2 through 2     
db_1   | 2022-04-08T00:46:02.223+0000 I STORAGE  [initandlisten] WiredTiger message [1649378762:223953][1:0x7f528fbd7a00], txn-recover: Set global recovery timestamp: 0
db_1   | 2022-04-08T00:46:02.244+0000 I CONTROL  [initandlisten]
db_1   | 2022-04-08T00:46:02.245+0000 I CONTROL  [initandlisten] ** WARNING: Access control is not enabled for the database.
db_1   | 2022-04-08T00:46:02.245+0000 I CONTROL  [initandlisten] **          Read and write access to data and configuration is unrestricted.
db_1   | 2022-04-08T00:46:02.245+0000 I CONTROL  [initandlisten]
db_1   | 2022-04-08T00:46:02.245+0000 I CONTROL  [initandlisten]
db_1   | 2022-04-08T00:46:03.441+0000 I NETWORK  [conn2] received client metadata from 172.19.0.3:49594 conn2: { driver: { name: "PyMongo", version: "4.1.0" }, os: { type: "Linux", name: "Linux", architecture: "x86_64", version: "5.10.16.3-microsoft-standard-WSL2" }, platform: "CPython 3.10.4.final.0" }db_1   | 2022-04-08T00:46:03.482+0000 I STORAGE  [conn2] createCollection: userTracker.UserNum with generated UUID: dac3413d-dbfb-41c0-9bb0-0fa074135916
web_1  |  * Serving Flask app 'app' (lazy loading)
web_1  |  * Environment: production
web_1  |    WARNING: This is a development server. Do not use it in a production deployment.
web_1  |    Use a production WSGI server instead.
web_1  |  * Debug mode: off
web_1  |  * Running on all addresses (0.0.0.0)web_1  |    WARNING: This is a development server. Do not use it in a production deployment.
web_1  |  * Running on http://127.0.0.1:5000
web_1  |  * Running on http://172.19.0.3:5000 (Press CTRL+C to quit)
```

### 3. Visit the URL: http://127.0.0.1:5000/

```
Hello World!
```

### 4. Visit the URL: http://127.0.0.1:5000/hello

```
"Hello user 1"
```

### 5. Visit the URL: http://127.0.0.1:5000/hello

```
"Hello user 2"
```

### 6. Visit the URL: http://127.0.0.1:5000/hello

```
"Hello user 3"
```

### 7. Hit ctrl+c to stop the docker container