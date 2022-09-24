# Node.js with MongoDB and Docker Demo

Application demo designed to show how Node.js and MongoDB can be run in Docker containers. 
The app uses Mongoose to create a simple database that stores Docker commands and examples. 

### Starting the Application with Docker Containers:

1. Install Docker for Windows or Docker for Mac (If you're on Windows 7 install Docker Toolbox: http://docker.com/toolbox).

2. Open a command prompt.

3. Run the commands listed in `node.dockerfile` (see the comments at the top of the file).

4. Navigate to http://localhost:3000. Use http://192.168.99.100:8080 in your browser to view the site if using Docker toolbox. This assumes that's the IP assigned to VirtualBox - change if needed.


### Starting the Application with Docker Compose

1. Install Docker for Windows or Docker for Mac (If you're on Windows 7 install Docker Toolbox: http://docker.com/toolbox).

2. Open a command prompt at the root of the application's folder.

3. Run `docker-compose build`

4. Run `docker-compose up`

5. Open another command prompt and run `docker ps -a` and note the ID of the Node container

6. Run `docker exec -it <nodeContainerID> sh` (replace <nodeContainerID> with the proper ID) to sh into the container

7. Run `node dbSeeder.js` to seed the MongoDB database

8. Type `exit` to leave the sh session

9. Navigate to http://localhost:3000 (http://192.168.99.100:3000 if using Docker Toolbox) in your browser to view the site. This assumes that's the IP assigned to VirtualBox - change if needed.

10. Run `docker-compose down` to stop the containers and remove them.

## To run the app with Node.js and MongoDB (without Docker):

1. Install and start MongoDB (https://docs.mongodb.com/manual/administration/install-community/).

2. Install the LTS version of Node.js (http://nodejs.org).

3. Open `config/config.development.json` and adjust the host name to your MongoDB server name (`localhost` normally works if you're running locally). 

4. Run `npm install`.

5. Run `node dbSeeder.js` to get the sample data loaded into MongoDB. Exit the command prompt.

6. Run `npm start` to start the server.

7. Navigate to http://localhost:3000 in your browser.


### Logs

```
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker-compose up
[+] Running 10/11
 - mongodb Pulled                                                                                                                                                                      26.5s
   - 675920708c8b Pull complete                                                                                                                                                         4.4s
   - 6f9c8c301e0f Pull complete                                                                                                                                                         4.5s
   - 73738965c4ce Pull complete                                                                                                                                                         4.7s
   - 7fd6635b9ddf Pull complete                                                                                                                                                         5.1s
   - 73a471eaa4ad Pull complete                                                                                                                                                         5.2s
   - bcf274af89b0 Pull complete                                                                                                                                                         5.3s
   - 04fc489f2a3b Pull complete                                                                                                                                                         5.3s
   - 6eff8a505292 Pull complete                                                                                                                                                        21.2s
   - a5ef4431fce7 Pull complete                                                                                                                                                        21.3s
 - node Error                                                                                                                                                                           4.0s
[+] Building 19.5s (12/12) FINISHED
 => [internal] load build definition from node.dockerfile                                                                                                                               0.1s
 => => transferring dockerfile: 1.23kB                                                                                                                                                  0.0s 
 => [internal] load .dockerignore                                                                                                                                                       0.1s 
 => => transferring context: 52B                                                                                                                                                        0.0s 
 => [internal] load metadata for docker.io/library/node:alpine                                                                                                                          2.6s
 => [auth] library/node:pull token for registry-1.docker.io                                                                                                                             0.0s
 => CACHED [1/6] FROM docker.io/library/node:alpine@sha256:831d5eca5b7437a8132031a25bd18bdb0399e7415d4e8e02a8c14426b6dcf17f                                                             0.0s
 => [internal] load build context                                                                                                                                                       0.5s 
 => => transferring context: 4.11MB                                                                                                                                                     0.1s
 => [2/6] RUN         apk update && apk add nano wget curl                                                                                                                              5.3s 
 => [3/6] WORKDIR     /var/www                                                                                                                                                          0.2s
 => [4/6] COPY        package.json package-lock.json ./                                                                                                                                 0.2s
 => [5/6] RUN         npm install                                                                                                                                                       9.5s
 => [6/6] COPY        . ./                                                                                                                                                              0.2s
 => exporting to image                                                                                                                                                                  1.0s
 => => exporting layers                                                                                                                                                                 1.0s
 => => writing image sha256:6d6996c8f03a6521015fa5c637436e7ad08b1e621a2698c2b90d4c6235f48f64                                                                                            0.0s
 => => naming to docker.io/library/nodeapp                                                                                                                                              0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
[+] Running 3/3
 - Network nodeexpressmongodbdockerapp-main_nodeapp-network  Created                                                                                                                    0.8s 
 - Container mongodb                                         Created                                                                                                                    0.2s
 - Container nodeapp                                         Created                                                                                                                    0.2s
Attaching to mongodb, nodeapp
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.954+00:00"},"s":"I",  "c":"NETWORK",  "id":4915701, "ctx":"thread1","msg":"Initialized wire specification","attr":{"spec":{"incomingExternalClient":{"minWireVersion":0,"maxWireVersion":17},"incomingInternalClient":{"minWireVersion":0,"maxWireVersion":17},"outgoing":{"minWireVersion":6,"maxWireVersion":17},"isInternalClient":true}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.955+00:00"},"s":"I",  "c":"CONTROL",  "id":23285,   "ctx":"thread1","msg":"Automatically disabling TLS 1.0, to force-enable TLS 1.0 specify --sslDisabledProtocols 'none'"}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.956+00:00"},"s":"I",  "c":"NETWORK",  "id":4648601, "ctx":"thread1","msg":"Implicit TCP FastOpen unavailable. If TCP FastOpen is required, set tcpFastOpenServer, tcpFastOpenClient, and tcpFastOpenQueueSize."}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.959+00:00"},"s":"I",  "c":"REPL",     "id":5123008, "ctx":"thread1","msg":"Successfully registered PrimaryOnlyService","attr":{"service":"TenantMigrationDonorService","namespace":"config.tenantMigrationDonors"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.959+00:00"},"s":"I",  "c":"REPL",     "id":5123008, "ctx":"thread1","msg":"Successfully registered PrimaryOnlyService","attr":{"service":"TenantMigrationRecipientService","namespace":"config.tenantMigrationRecipients"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.959+00:00"},"s":"I",  "c":"REPL",     "id":5123008, "ctx":"thread1","msg":"Successfully registered PrimaryOnlyService","attr":{"service":"ShardSplitDonorService","namespace":"config.tenantSplitDonors"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.959+00:00"},"s":"I",  "c":"CONTROL",  "id":5945603, "ctx":"thread1","msg":"Multi threading initialized"}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.960+00:00"},"s":"I",  "c":"CONTROL",  "id":4615611, "ctx":"initandlisten","msg":"MongoDB starting","attr":{"pid":1,"port":27017,"dbPath":"/data/db","architecture":"64-bit","host":"804a926f9c39"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.960+00:00"},"s":"I",  "c":"CONTROL",  "id":23403,   "ctx":"initandlisten","msg":"Build Info","attr":{"buildInfo":{"version":"6.0.1","gitVersion":"32f0f9c88dc44a2c8073a5bd47cf779d4bfdee6b","openSSLVersion":"OpenSSL 1.1.1f  31 Mar 2020","modules":[],"allocator":"tcmalloc","environment":{"distmod":"ubuntu2004","distarch":"x86_64","target_arch":"x86_64"}}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.960+00:00"},"s":"I",  "c":"CONTROL",  "id":51765,   "ctx":"initandlisten","msg":"Operating System","attr":{"os":{"name":"Ubuntu","version":"20.04"}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.960+00:00"},"s":"I",  "c":"CONTROL",  "id":21951,   "ctx":"initandlisten","msg":"Options set by command line","attr":{"options":{"net":{"bindIp":"*"}}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.963+00:00"},"s":"I",  "c":"STORAGE",  "id":22297,   "ctx":"initandlisten","msg":"Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem","tags":["startupWarnings"]}
mongodb  | {"t":{"$date":"2022-09-24T05:46:35.963+00:00"},"s":"I",  "c":"STORAGE",  "id":22315,   "ctx":"initandlisten","msg":"Opening WiredTiger","attr":{"config":"create,cache_size=1434M,session_max=33000,eviction=(threads_min=4,threads_max=4),config_base=false,statistics=(fast),log=(enabled=true,remove=true,path=journal,compressor=snappy),builtin_extension_config=(zstd=(compression_level=6)),file_manager=(close_idle_time=600,close_scan_interval=10,close_handle_minimum=2000),statistics_log=(wait=0),json_output=(error,message),verbose=[recovery_progress:1,checkpoint_progress:1,compact_progress:1,backup:0,checkpoint:0,compact:0,evict:0,history_store:0,recovery:0,rts:0,salvage:0,tiered:0,timestamp:0,transaction:0,verify:0,log:0],"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.594+00:00"},"s":"I",  "c":"STORAGE",  "id":4795906, "ctx":"initandlisten","msg":"WiredTiger opened","attr":{"durationMillis":631}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.594+00:00"},"s":"I",  "c":"RECOVERY", "id":23987,   "ctx":"initandlisten","msg":"WiredTiger recoveryTimestamp","attr":{"recoveryTimestamp":{"$timestamp":{"t":0,"i":0}}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.638+00:00"},"s":"I",  "c":"WT",       "id":4366408, "ctx":"initandlisten","msg":"No table logging settings modifications are required for existing WiredTiger tables","attr":{"loggingEnabled":true}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.659+00:00"},"s":"W",  "c":"CONTROL",  "id":22120,   "ctx":"initandlisten","msg":"Access control is not enabled for the database. Read and write access to data and configuration is unrestricted","tags":["startupWarnings"]}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.659+00:00"},"s":"W",  "c":"CONTROL",  "id":22178,   "ctx":"initandlisten","msg":"/sys/kernel/mm/transparent_hugepage/enabled is 'always'. We suggest setting it to 'never'","tags":["startupWarnings"]}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.659+00:00"},"s":"W",  "c":"CONTROL",  "id":5123300, "ctx":"initandlisten","msg":"vm.max_map_count is too low","attr":{"currentValue":65530,"recommendedMinimum":1677720,"maxConns":838860},"tags":["startupWarnings"]}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.660+00:00"},"s":"I",  "c":"STORAGE",  "id":20320,   "ctx":"initandlisten","msg":"createCollection","attr":{"namespace":"admin.system.version","uuidDisposition":"provided","uuid":{"uuid":{"$uuid":"3fef5e59-02b0-44e5-837e-6d2d7102d898"}},"options":{"uuid":{"$uuid":"3fef5e59-02b0-44e5-837e-6d2d7102d898"}}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.727+00:00"},"s":"I",  "c":"INDEX",    "id":20345,   "ctx":"initandlisten","msg":"Index build: done building","attr":{"buildUUID":null,"collectionUUID":{"uuid":{"$uuid":"3fef5e59-02b0-44e5-837e-6d2d7102d898"}},"namespace":"admin.system.version","index":"_id_","ident":"index-1--735204603252627015","collectionIdent":"collection-0--735204603252627015","commitTimestamp":null}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.727+00:00"},"s":"I",  "c":"REPL",     "id":20459,   "ctx":"initandlisten","msg":"Setting featureCompatibilityVersion","attr":{"newVersion":"6.0"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.727+00:00"},"s":"I",  "c":"REPL",     "id":5853300, "ctx":"initandlisten","msg":"current featureCompatibilityVersion value","attr":{"featureCompatibilityVersion":"6.0","context":"setFCV"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.727+00:00"},"s":"I",  "c":"NETWORK",  "id":4915702, "ctx":"initandlisten","msg":"Updated wire specification","attr":{"oldSpec":{"incomingExternalClient":{"minWireVersion":0,"maxWireVersion":17},"incomingInternalClient":{"minWireVersion":0,"maxWireVersion":17},"outgoing":{"minWireVersion":6,"maxWireVersion":17},"isInternalClient":true},"newSpec":{"incomingExternalClient":{"minWireVersion":0,"maxWireVersion":17},"incomingInternalClient":{"minWireVersion":17,"maxWireVersion":17},"outgoing":{"minWireVersion":17,"maxWireVersion":17},"isInternalClient":true}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.727+00:00"},"s":"I",  "c":"NETWORK",  "id":4915702, "ctx":"initandlisten","msg":"Updated wire specification","attr":{"oldSpec":{"incomingExternalClient":{"minWireVersion":0,"maxWireVersion":17},"incomingInternalClient":{"minWireVersion":17,"maxWireVersion":17},"outgoing":{"minWireVersion":17,"maxWireVersion":17},"isInternalClient":true},"newSpec":{"incomingExternalClient":{"minWireVersion":0,"maxWireVersion":17},"incomingInternalClient":{"minWireVersion":17,"maxWireVersion":17},"outgoing":{"minWireVersion":17,"maxWireVersion":17},"isInternalClient":true}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.727+00:00"},"s":"I",  "c":"REPL",     "id":5853300, "ctx":"initandlisten","msg":"current featureCompatibilityVersion value","attr":{"featureCompatibilityVersion":"6.0","context":"startup"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.727+00:00"},"s":"I",  "c":"STORAGE",  "id":5071100, "ctx":"initandlisten","msg":"Clearing temp directory"}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.728+00:00"},"s":"I",  "c":"CONTROL",  "id":20536,   "ctx":"initandlisten","msg":"Flow Control is enabled on this deployment"}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.731+00:00"},"s":"I",  "c":"FTDC",     "id":20625,   "ctx":"initandlisten","msg":"Initializing full-time diagnostic data capture","attr":{"dataDirectory":"/data/db/diagnostic.data"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.740+00:00"},"s":"I",  "c":"STORAGE",  "id":20320,   "ctx":"initandlisten","msg":"createCollection","attr":{"namespace":"local.startup_log","uuidDisposition":"generated","uuid":{"uuid":{"$uuid":"8b7dcd1a-43ec-4ca1-b5a9-c08ea238b39e"}},"options":{"capped":true,"size":10485760}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.780+00:00"},"s":"I",  "c":"INDEX",    "id":20345,   "ctx":"initandlisten","msg":"Index build: done building","attr":{"buildUUID":null,"collectionUUID":{"uuid":{"$uuid":"8b7dcd1a-43ec-4ca1-b5a9-c08ea238b39e"}},"namespace":"local.startup_log","index":"_id_","ident":"index-3--735204603252627015","collectionIdent":"collection-2--735204603252627015","commitTimestamp":null}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.781+00:00"},"s":"I",  "c":"REPL",     "id":6015317, "ctx":"initandlisten","msg":"Setting new configuration state","attr":{"newState":"ConfigReplicationDisabled","oldState":"ConfigPreStart"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.781+00:00"},"s":"I",  "c":"STORAGE",  "id":22262,   "ctx":"initandlisten","msg":"Timestamp monitor starting"}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.796+00:00"},"s":"I",  "c":"CONTROL",  "id":20712,   "ctx":"LogicalSessionCacheReap","msg":"Sessions collection is not set up; waiting until next sessions reap interval","attr":{"error":"NamespaceNotFound: config.system.sessions does not exist"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.796+00:00"},"s":"I",  "c":"NETWORK",  "id":23015,   "ctx":"listener","msg":"Listening on","attr":{"address":"/tmp/mongodb-27017.sock"}}        
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.796+00:00"},"s":"I",  "c":"STORAGE",  "id":20320,   "ctx":"LogicalSessionCacheRefresh","msg":"createCollection","attr":{"namespace":"config.system.sessions","uuidDisposition":"generated","uuid":{"uuid":{"$uuid":"f9e7273f-6a77-4aa1-8029-8d440544002b"}},"options":{}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.796+00:00"},"s":"I",  "c":"NETWORK",  "id":23015,   "ctx":"listener","msg":"Listening on","attr":{"address":"0.0.0.0"}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.796+00:00"},"s":"I",  "c":"NETWORK",  "id":23016,   "ctx":"listener","msg":"Waiting for connections","attr":{"port":27017,"ssl":"off"}}        
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.891+00:00"},"s":"I",  "c":"INDEX",    "id":20345,   "ctx":"LogicalSessionCacheRefresh","msg":"Index build: done building","attr":{"buildUUID":null,"collectionUUID":{"uuid":{"$uuid":"f9e7273f-6a77-4aa1-8029-8d440544002b"}},"namespace":"config.system.sessions","index":"_id_","ident":"index-5--735204603252627015","collectionIdent":"collection-4--735204603252627015","commitTimestamp":null}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:36.891+00:00"},"s":"I",  "c":"INDEX",    "id":20345,   "ctx":"LogicalSessionCacheRefresh","msg":"Index build: done building","attr":{"buildUUID":null,"collectionUUID":{"uuid":{"$uuid":"f9e7273f-6a77-4aa1-8029-8d440544002b"}},"namespace":"config.system.sessions","index":"lsidTTLIndex","ident":"index-6--735204603252627015","collectionIdent":"collection-4--735204603252627015","commitTimestamp":null}}
nodeapp  | 
nodeapp  | > expressite@1.0.0 start
nodeapp  | > node server.js
nodeapp  |
nodeapp  | Trying to connect to mongodb/funWithDocker MongoDB database
nodeapp  | (node:17) [MONGODB DRIVER] Warning: promiseLibrary is a deprecated option
nodeapp  | (Use `node --trace-warnings ...` to show where the warning was created)
nodeapp  | [production] Listening on http://localhost:3000
mongodb  | {"t":{"$date":"2022-09-24T05:46:38.400+00:00"},"s":"I",  "c":"NETWORK",  "id":22943,   "ctx":"listener","msg":"Connection accepted","attr":{"remote":"172.20.0.3:46410","uuid":"efea1563-7a2f-4539-995e-4b6362eca2b1","connectionId":1,"connectionCount":1}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:38.414+00:00"},"s":"I",  "c":"NETWORK",  "id":51800,   "ctx":"conn1","msg":"client metadata","attr":{"remote":"172.20.0.3:46410","client":"conn1","doc":{"driver":{"name":"nodejs|Mongoose","version":"4.7.0"},"os":{"type":"Linux","name":"linux","architecture":"x64","version":"5.10.16.3-microsoft-standard-WSL2"},"platfor9.0, LE (unified)","version":"4.7.0|6.4.6"}}}
nodeapp  | db connection open
mongodb  | {"t":{"$date":"2022-09-24T05:46:38.443+00:00"},"s":"I",  "c":"NETWORK",  "id":22943,   "ctx":"listener","msg":"Connection accepted","attr":{"remote":"172.20.0.3:46412","uuid":"403c6137-3b7f-4ca2-8e7e-8cd58cfa0ef2","connectionId":2,"connectionCount":2}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:38.445+00:00"},"s":"I",  "c":"NETWORK",  "id":51800,   "ctx":"conn2","msg":"client metadata","attr":{"remote":"172.20.0.3:46412","client":"conn2","doc":{"driver":{"name":"nodejs|Mongoose","version":"4.7.0"},"os":{"type":"Linux","name":"linux","architecture":"x64","version":"5.10.16.3-microsoft-standard-WSL2"},"platform":"Node.js v18.9.0, LE (unified)","version":"4.7.0|6.4.6"}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:38.453+00:00"},"s":"I",  "c":"STORAGE",  "id":20320,   "ctx":"conn2","msg":"createCollection","attr":{"namespace":"funWithDocker.dockercommands","uuidDisposition":"generated","uuid":{"uuid":{"$uuid":"464558f3-66cb-40ae-82a1-29aae2c7c628"}},"options":{}}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:38.502+00:00"},"s":"I",  "c":"INDEX",    "id":20345,   "ctx":"conn2","msg":"Index build: done building","attr":{"buildUUID":null,"collectionUUID":{"uuid":{"$uuid":"464558f3-66cb-40ae-82a1-29aae2c7c628"}},"namespace":"funWithDocker.dockercommands","index":"_id_","ident":"index-8--735204603252627015","collectionIdent":"collection-7--735204603252627015","commitTimestamp":null}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:48.962+00:00"},"s":"I",  "c":"NETWORK",  "id":22943,   "ctx":"listener","msg":"Connection accepted","attr":{"remote":"172.20.0.3:46494","uuid":"9ec4e75a-2ff6-4d9c-9ebc-88d109368815","connectionId":3,"connectionCount":3}}
mongodb  | {"t":{"$date":"2022-09-24T05:46:48.963+00:00"},"s":"I",  "c":"NETWORK",  "id":51800,   "ctx":"conn3","msg":"client metadata","attr":{"remote":"172.20.0.3:46494","client":"conn3","doc":{"driver":{"name":"nodejs|Mongoose","version":"4.7.0"},"os":{"type":"Linux","name":"linux","architecture":"x64","version":"5.10.16.3-microsoft-standard-WSL2"},"platform":"Node.js v18.9.0, LE (unified)","version":"4.7.0|6.4.6"}}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:23.236+00:00"},"s":"I",  "c":"NETWORK",  "id":22943,   "ctx":"listener","msg":"Connection accepted","attr":{"remote":"172.20.0.3:47682","uuid":"acb85d7c-62c2-4559-b858-4d8a3d54dd79","connectionId":4,"connectionCount":4}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:23.244+00:00"},"s":"I",  "c":"NETWORK",  "id":51800,   "ctx":"conn4","msg":"client metadata","attr":{"remote":"172.20.0.3:47682","client":"conn4","doc":{"driver":{"name":"nodejs|Mongoose","version":"4.7.0"},"os":{"type":"Linux","name":"linux","architecture":"x64","version":"5.10.16.3-microsoft-standard-WSL2"},"platform":"Node.js v18.9.0, LE (unified)","version":"4.7.0|6.4.6"}}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:23.260+00:00"},"s":"I",  "c":"NETWORK",  "id":22943,   "ctx":"listener","msg":"Connection accepted","attr":{"remote":"172.20.0.3:47684","uuid":"fd2ad6f6-fc16-4a54-8755-6a6dce427114","connectionId":5,"connectionCount":5}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:23.260+00:00"},"s":"I",  "c":"NETWORK",  "id":22943,   "ctx":"listener","msg":"Connection accepted","attr":{"remote":"172.20.0.3:47686","uuid":"9be83474-f72f-4abb-beca-e54e1e77bfa2","connectionId":6,"connectionCount":6}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:23.262+00:00"},"s":"I",  "c":"NETWORK",  "id":51800,   "ctx":"conn5","msg":"client metadata","attr":{"remote":"172.20.0.3:47684","client":"conn5","doc":{"driver":{"name":"nodejs|Mongoose","version":"4.7.0"},"os":{"type":"Linux","name":"linux","architecture":"x64","version":"5.10.16.3-microsoft-standard-WSL2"},"platform":"Node.js v18.9.0, LE (unified)","version":"4.7.0|6.4.6"}}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:23.263+00:00"},"s":"I",  "c":"NETWORK",  "id":51800,   "ctx":"conn6","msg":"client metadata","attr":{"remote":"172.20.0.3:47686","client":"conn6","doc":{"driver":{"name":"nodejs|Mongoose","version":"4.7.0"},"os":{"type":"Linux","name":"linux","architecture":"x64","version":"5.10.16.3-microsoft-standard-WSL2"},"platform":"Node.js v18.9.0, LE (unified)","version":"4.7.0|6.4.6"}}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:23.269+00:00"},"s":"I",  "c":"NETWORK",  "id":22943,   "ctx":"listener","msg":"Connection accepted","attr":{"remote":"172.20.0.3:47688","uuid":"fb5450ce-fdb9-4369-9040-92c30116988d","connectionId":7,"connectionCount":7}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:23.270+00:00"},"s":"I",  "c":"NETWORK",  "id":51800,   "ctx":"conn7","msg":"client metadata","attr":{"remote":"172.20.0.3:47688","client":"conn7","doc":{"driver":{"name":"nodejs|Mongoose","version":"4.7.0"},"os":{"type":"Linux","name":"linux","architecture":"x64","version":"5.10.16.3-microsoft-standard-WSL2"},"platform":"Node.js v18.9.0, LE (unified)","version":"4.7.0|6.4.6"}}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:33.762+00:00"},"s":"I",  "c":"NETWORK",  "id":22943,   "ctx":"listener","msg":"Connection accepted","attr":{"remote":"172.20.0.3:47774","uuid":"c2624182-4dbe-4d32-b526-65d227c4b47d","connectionId":8,"connectionCount":8}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:33.763+00:00"},"s":"I",  "c":"NETWORK",  "id":51800,   "ctx":"conn8","msg":"client metadata","attr":{"remote":"172.20.0.3:47774","client":"conn8","doc":{"driver":{"name":"nodejs|Mongoose","version":"4.7.0"},"os":{"type":"Linux","name":"linux","architecture":"x64","version":"5.10.16.3-microsoft-standard-WSL2"},"platform":"Node.js v18.9.0, LE (unified)","version":"4.7.0|6.4.6"}}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:37.879+00:00"},"s":"I",  "c":"-",        "id":20883,   "ctx":"conn4","msg":"Interrupted operation as its client disconnected","attr":{"opId":2223}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:37.887+00:00"},"s":"I",  "c":"NETWORK",  "id":22944,   "ctx":"conn7","msg":"Connection ended","attr":{"remote":"172.20.0.3:47688","uuid":"fb5450ce-fdb9-4369-9040-92c30116988d","connectionId":7,"connectionCount":7}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:37.887+00:00"},"s":"I",  "c":"NETWORK",  "id":22944,   "ctx":"conn8","msg":"Connection ended","attr":{"remote":"172.20.0.3:47774","uuid":"c2624182-4dbe-4d32-b526-65d227c4b47d","connectionId":8,"connectionCount":6}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:37.887+00:00"},"s":"I",  "c":"NETWORK",  "id":22944,   "ctx":"conn6","msg":"Connection ended","attr":{"remote":"172.20.0.3:47686","uuid":"9be83474-f72f-4abb-beca-e54e1e77bfa2","connectionId":6,"connectionCount":5}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:37.887+00:00"},"s":"I",  "c":"NETWORK",  "id":22944,   "ctx":"conn5","msg":"Connection ended","attr":{"remote":"172.20.0.3:47684","uuid":"fd2ad6f6-fc16-4a54-8755-6a6dce427114","connectionId":5,"connectionCount":4}}
mongodb  | {"t":{"$date":"2022-09-24T05:49:37.888+00:00"},"s":"I",  "c":"NETWORK",  "id":22944,   "ctx":"conn4","msg":"Connection ended","attr":{"remote":"172.20.0.3:47682","uuid":"acb85d7c-62c2-4559-b858-4d8a3d54dd79","connectionId":4,"connectionCount":3}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:11.414+00:00"},"s":"I",  "c":"-",        "id":20883,   "ctx":"conn1","msg":"Interrupted operation as its client disconnected","attr":{"opId":2672}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:11.414+00:00"},"s":"I",  "c":"NETWORK",  "id":22944,   "ctx":"conn2","msg":"Connection ended","attr":{"remote":"172.20.0.3:46412","uuid":"403c6137-3b7f-4ca2-8e7e-8cd58cfa0ef2","connectionId":2,"connectionCount":1}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:11.414+00:00"},"s":"I",  "c":"NETWORK",  "id":22944,   "ctx":"conn3","msg":"Connection ended","attr":{"remote":"172.20.0.3:46494","uuid":"9ec4e75a-2ff6-4d9c-9ebc-88d109368815","connectionId":3,"connectionCount":2}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:11.415+00:00"},"s":"I",  "c":"NETWORK",  "id":22944,   "ctx":"conn1","msg":"Connection ended","attr":{"remote":"172.20.0.3:46410","uuid":"efea1563-7a2f-4539-995e-4b6362eca2b1","connectionId":1,"connectionCount":0}}
nodeapp  | npm ERR! path /var/www
nodeapp  | npm ERR! command failed
nodeapp  | npm ERR! signal SIGTERM
nodeapp  | npm ERR! command sh -c -- node server.js
nodeapp  |
nodeapp  | npm ERR! A complete log of this run can be found in:
nodeapp  | npm ERR!     /root/.npm/_logs/2022-09-24T05_46_37_738Z-debug-0.log
nodeapp exited with code 1
nodeapp exited with code 0
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.787+00:00"},"s":"I",  "c":"CONTROL",  "id":23377,   "ctx":"SignalHandler","msg":"Received signal","attr":{"signal":15,"error":"Terminated"}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.787+00:00"},"s":"I",  "c":"CONTROL",  "id":23378,   "ctx":"SignalHandler","msg":"Signal was sent by kill(2)","attr":{"pid":0,"uid":0}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.788+00:00"},"s":"I",  "c":"CONTROL",  "id":23381,   "ctx":"SignalHandler","msg":"will terminate after current cmd ends"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.790+00:00"},"s":"I",  "c":"REPL",     "id":4784900, "ctx":"SignalHandler","msg":"Stepping down the ReplicationCoordinator for shutdown","attr":{"waitTimeMillis":15000}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.796+00:00"},"s":"I",  "c":"REPL",     "id":4794602, "ctx":"SignalHandler","msg":"Attempting to enter quiesce mode"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.796+00:00"},"s":"I",  "c":"-",        "id":6371601, "ctx":"SignalHandler","msg":"Shutting down the FLE Crud thread pool"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.796+00:00"},"s":"I",  "c":"COMMAND",  "id":4784901, "ctx":"SignalHandler","msg":"Shutting down the MirrorMaestro"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.796+00:00"},"s":"I",  "c":"SHARDING", "id":4784902, "ctx":"SignalHandler","msg":"Shutting down the WaitForMajorityService"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.798+00:00"},"s":"I",  "c":"CONTROL",  "id":4784903, "ctx":"SignalHandler","msg":"Shutting down the LogicalSessionCache"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.804+00:00"},"s":"I",  "c":"NETWORK",  "id":20562,   "ctx":"SignalHandler","msg":"Shutdown: going to close listening sockets"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.804+00:00"},"s":"I",  "c":"NETWORK",  "id":23017,   "ctx":"listener","msg":"removing socket file","attr":{"path":"/tmp/mongodb-27017.sock"}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.805+00:00"},"s":"I",  "c":"NETWORK",  "id":4784905, "ctx":"SignalHandler","msg":"Shutting down the global connection pool"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.805+00:00"},"s":"I",  "c":"CONTROL",  "id":4784906, "ctx":"SignalHandler","msg":"Shutting down the FlowControlTicketholder"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.805+00:00"},"s":"I",  "c":"-",        "id":20520,   "ctx":"SignalHandler","msg":"Stopping further Flow Control ticket acquisitions."}  
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.806+00:00"},"s":"I",  "c":"CONTROL",  "id":4784908, "ctx":"SignalHandler","msg":"Shutting down the PeriodicThreadToAbortExpiredTransactions"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.806+00:00"},"s":"I",  "c":"REPL",     "id":4784909, "ctx":"SignalHandler","msg":"Shutting down the ReplicationCoordinator"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.806+00:00"},"s":"I",  "c":"SHARDING", "id":4784910, "ctx":"SignalHandler","msg":"Shutting down the ShardingInitializationMongoD"}      
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.806+00:00"},"s":"I",  "c":"REPL",     "id":4784911, "ctx":"SignalHandler","msg":"Enqueuing the ReplicationStateTransitionLock for shutdown"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.807+00:00"},"s":"I",  "c":"-",        "id":4784912, "ctx":"SignalHandler","msg":"Killing all operations for shutdown"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.807+00:00"},"s":"I",  "c":"-",        "id":4695300, "ctx":"SignalHandler","msg":"Interrupted all currently running operations","attr":{"opsKilled":3}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.807+00:00"},"s":"I",  "c":"TENANT_M", "id":5093807, "ctx":"SignalHandler","msg":"Shutting down all TenantMigrationAccessBlockers on global shutdown"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.807+00:00"},"s":"I",  "c":"COMMAND",  "id":4784913, "ctx":"SignalHandler","msg":"Shutting down all open transactions"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.807+00:00"},"s":"I",  "c":"REPL",     "id":4784914, "ctx":"SignalHandler","msg":"Acquiring the ReplicationStateTransitionLock for shutdown"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.807+00:00"},"s":"I",  "c":"INDEX",    "id":4784915, "ctx":"SignalHandler","msg":"Shutting down the IndexBuildsCoordinator"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.808+00:00"},"s":"I",  "c":"NETWORK",  "id":4784918, "ctx":"SignalHandler","msg":"Shutting down the ReplicaSetMonitor"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.809+00:00"},"s":"I",  "c":"SHARDING", "id":4784921, "ctx":"SignalHandler","msg":"Shutting down the MigrationUtilExecutor"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.811+00:00"},"s":"I",  "c":"ASIO",     "id":22582,   "ctx":"MigrationUtil-TaskExecutor","msg":"Killing all outstanding egress activity."}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.812+00:00"},"s":"I",  "c":"COMMAND",  "id":4784923, "ctx":"SignalHandler","msg":"Shutting down the ServiceEntryPoint"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.819+00:00"},"s":"I",  "c":"STORAGE",  "id":20282,   "ctx":"SignalHandler","msg":"Deregistering all the collections"}        
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.821+00:00"},"s":"I",  "c":"STORAGE",  "id":22261,   "ctx":"SignalHandler","msg":"Timestamp monitor shutting down"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.821+00:00"},"s":"I",  "c":"STORAGE",  "id":22317,   "ctx":"SignalHandler","msg":"WiredTigerKVEngine shutting down"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.822+00:00"},"s":"I",  "c":"STORAGE",  "id":22318,   "ctx":"SignalHandler","msg":"Shutting down session sweeper thread"}     
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.822+00:00"},"s":"I",  "c":"STORAGE",  "id":22319,   "ctx":"SignalHandler","msg":"Finished shutting down session sweeper thread"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.823+00:00"},"s":"I",  "c":"STORAGE",  "id":4795902, "ctx":"SignalHandler","msg":"Closing WiredTiger","attr":{"closeConfig":"leak_memory=true,"}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.862+00:00"},"s":"I",  "c":"STORAGE",  "id":4795901, "ctx":"SignalHandler","msg":"WiredTiger closed","attr":{"durationMillis":39}}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.862+00:00"},"s":"I",  "c":"STORAGE",  "id":22279,   "ctx":"SignalHandler","msg":"shutdown: removing fs lock..."}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.863+00:00"},"s":"I",  "c":"-",        "id":4784931, "ctx":"SignalHandler","msg":"Dropping the scope cache for shutdown"}    
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.863+00:00"},"s":"I",  "c":"FTDC",     "id":20626,   "ctx":"SignalHandler","msg":"Shutting down full-time diagnostic data capture"}
mongodb  | {"t":{"$date":"2022-09-24T05:50:12.870+00:00"},"s":"I",  "c":"CONTROL",  "id":20565,   "ctx":"SignalHandler","msg":"Now exiting"}mongodb  | {"t":{"$date":"2022-09-24T05:50:12.872+00:00"},"s":"I",  "c":"CONTROL",  "id":23138,   "ctx":"SignalHandler","msg":"Shutting down","attr":{"exitCode":0}}      
mongodb exited with code 0
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS                  NAMES
1a488bc06abe   nginx:alpine   "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8080->80/tcp   sharp_joliot
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
CONTAINER ID   IMAGE              COMMAND                  CREATED         STATUS                     PORTS                  NAMES
1a488bc06abe   nginx:alpine       "/docker-entrypoint.…"   2 minutes ago   Up 2 minutes               0.0.0.0:8080->80/tcp   sharp_joliot
f472f591a55d   9620/nodeapp:1.0   "npm start"              7 minutes ago   Exited (1) 7 minutes ago                          elegant_cartwright
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker rm 1a
Error response from daemon: You cannot remove a running container 1a488bc06abe8198f505176b02a3a8f155b457a0d1cad7588c7746af28ee7914. Stop the container before attempting removal or force remove
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker stop 1a
1a
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker rm 1a  
1a
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a  
CONTAINER ID   IMAGE              COMMAND       CREATED         STATUS                     PORTS     NAMES
f472f591a55d   9620/nodeapp:1.0   "npm start"   8 minutes ago   Exited (1) 8 minutes ago             elegant_cartwright
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> cd nginx
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main\nginx> docker run -p 8080:80 -v ${PWD}:/usr/share/nginx/html nginx:alpine
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/09/24 06:40:18 [notice] 1#1: using the "epoll" event method
2022/09/24 06:40:18 [notice] 1#1: nginx/1.23.1
2022/09/24 06:40:18 [notice] 1#1: built by gcc 11.2.1 20220219 (Alpine 11.2.1_git20220219)
2022/09/24 06:40:18 [notice] 1#1: OS: Linux 5.10.16.3-microsoft-standard-WSL2
2022/09/24 06:40:18 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/09/24 06:40:18 [notice] 1#1: start worker processes
2022/09/24 06:40:18 [notice] 1#1: start worker process 32
2022/09/24 06:40:18 [notice] 1#1: start worker process 33
2022/09/24 06:40:18 [notice] 1#1: start worker process 34
2022/09/24 06:40:18 [notice] 1#1: start worker process 35
2022/09/24 06:40:18 [notice] 1#1: start worker process 36
2022/09/24 06:40:18 [notice] 1#1: start worker process 37
2022/09/24 06:40:18 [notice] 1#1: start worker process 38
2022/09/24 06:40:18 [notice] 1#1: start worker process 39
2022/09/24 06:40:18 [notice] 1#1: start worker process 40
2022/09/24 06:40:18 [notice] 1#1: start worker process 41
2022/09/24 06:40:18 [notice] 1#1: start worker process 42
2022/09/24 06:40:18 [notice] 1#1: start worker process 43
172.17.0.1 - - [24/Sep/2022:06:40:22 +0000] "GET / HTTP/1.1" 200 398 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/105.0.0.0 Safari/537.36" "-"
2022/09/24 06:40:22 [error] 32#32: *1 open() "/usr/share/nginx/html/main.css" failed (2: No such file or directory), client: 172.17.0.1, server: localhost, request: "GET /main.css HTTP/1.1", host: "localhost:8080", referrer: "http://localhost:8080/"
172.17.0.1 - - [24/Sep/2022:06:40:22 +0000] "GET /main.css HTTP/1.1" 404 555 "http://localhost:8080/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/105.0.0.0 Safari/537.36" "-"
172.17.0.1 - - [24/Sep/2022:06:40:22 +0000] "GET /main.js HTTP/1.1" 404 555 "http://localhost:8080/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/105.0.0.0 Safari/537.36" "-"
2022/09/24 06:40:22 [error] 33#33: *2 open() "/usr/share/nginx/html/main.js" failed (2: No such file or directory), client: 172.17.0.1, server: localhost, request: "GET /main.js HTTP/1.1", host: "localhost:8080", referrer: "http://localhost:8080/"
2022/09/24 06:42:08 [notice] 1#1: signal 3 (SIGQUIT) received, shutting down
2022/09/24 06:42:08 [notice] 32#32: gracefully shutting down
2022/09/24 06:42:08 [notice] 33#33: gracefully shutting down
2022/09/24 06:42:08 [notice] 34#34: gracefully shutting down
2022/09/24 06:42:08 [notice] 35#35: gracefully shutting down
2022/09/24 06:42:08 [notice] 36#36: gracefully shutting down
2022/09/24 06:42:08 [notice] 34#34: exiting
2022/09/24 06:42:08 [notice] 37#37: gracefully shutting down
2022/09/24 06:42:08 [notice] 38#38: gracefully shutting down
2022/09/24 06:42:08 [notice] 33#33: exiting
2022/09/24 06:42:08 [notice] 32#32: exiting
2022/09/24 06:42:08 [notice] 35#35: exiting
2022/09/24 06:42:08 [notice] 36#36: exiting
2022/09/24 06:42:08 [notice] 40#40: gracefully shutting down
2022/09/24 06:42:08 [notice] 41#41: gracefully shutting down
2022/09/24 06:42:08 [notice] 37#37: exiting
2022/09/24 06:42:08 [notice] 40#40: exiting
2022/09/24 06:42:08 [notice] 38#38: exiting
2022/09/24 06:42:08 [notice] 42#42: gracefully shutting down
2022/09/24 06:42:08 [notice] 41#41: exiting
2022/09/24 06:42:08 [notice] 39#39: gracefully shutting down
2022/09/24 06:42:08 [notice] 39#39: exiting
2022/09/24 06:42:08 [notice] 33#33: exit
2022/09/24 06:42:08 [notice] 32#32: exit
2022/09/24 06:42:08 [notice] 36#36: exit
2022/09/24 06:42:08 [notice] 34#34: exit
2022/09/24 06:42:08 [notice] 35#35: exit
2022/09/24 06:42:08 [notice] 42#42: exiting
2022/09/24 06:42:08 [notice] 38#38: exit
2022/09/24 06:42:08 [notice] 40#40: exit
2022/09/24 06:42:08 [notice] 41#41: exit
2022/09/24 06:42:08 [notice] 37#37: exit
2022/09/24 06:42:08 [notice] 39#39: exit
2022/09/24 06:42:08 [notice] 43#43: gracefully shutting down
2022/09/24 06:42:08 [notice] 42#42: exit
2022/09/24 06:42:08 [notice] 43#43: exiting
2022/09/24 06:42:08 [notice] 43#43: exit
2022/09/24 06:42:08 [notice] 1#1: signal 17 (SIGCHLD) received from 42
2022/09/24 06:42:08 [notice] 1#1: worker process 37 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: worker process 42 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:42:08 [notice] 1#1: signal 17 (SIGCHLD) received from 33
2022/09/24 06:42:08 [notice] 1#1: worker process 33 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:42:08 [notice] 1#1: signal 17 (SIGCHLD) received from 32
2022/09/24 06:42:08 [notice] 1#1: worker process 32 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: worker process 38 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:42:08 [notice] 1#1: signal 17 (SIGCHLD) received from 39
2022/09/24 06:42:08 [notice] 1#1: worker process 39 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:42:08 [notice] 1#1: signal 17 (SIGCHLD) received from 35
2022/09/24 06:42:08 [notice] 1#1: worker process 35 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: worker process 40 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: worker process 41 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: worker process 43 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:42:08 [notice] 1#1: signal 17 (SIGCHLD) received from 36
2022/09/24 06:42:08 [notice] 1#1: worker process 36 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:42:08 [notice] 1#1: signal 17 (SIGCHLD) received from 34
2022/09/24 06:42:08 [notice] 1#1: worker process 34 exited with code 0
2022/09/24 06:42:08 [notice] 1#1: exit
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main\nginx> docker run -p 3000:3000 -v ${PWD}/logs:/var/www/logs 9620/nodeapp:1.0 

> expressite@1.0.0 start
> node server.js

Node environment: development
loading config.development.json
Trying to connect to mongodb/funWithDocker MongoDB database
(node:17) [MONGODB DRIVER] Warning: promiseLibrary is a deprecated option
(Use `node --trace-warnings ...` to show where the warning was created)
[development] Listening on http://localhost:3000
connection error: MongooseServerSelectionError: getaddrinfo EAI_AGAIN mongodb
    at Connection.openUri (/var/www/node_modules/mongoose/lib/connection.js:819:32)
    at /var/www/node_modules/mongoose/lib/index.js:379:10
    at /var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:32:5
    at new Promise (<anonymous>)
    at promiseOrCallback (/var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:31:10)
    at Mongoose._promiseOrCallback (/var/www/node_modules/mongoose/lib/index.js:1224:10)
    at Mongoose.connect (/var/www/node_modules/mongoose/lib/index.js:378:20)
    at Object.init (/var/www/lib/database.js:16:22)
    at Object.<anonymous> (/var/www/server.js:41:4)
    at Module._compile (node:internal/modules/cjs/loader:1119:14) {
  reason: TopologyDescription {
    type: 'Unknown',
    servers: Map(1) { 'mongodb:27017' => [ServerDescription] },
    stale: false,
    compatible: true,
    heartbeatFrequencyMS: 10000,
    localThresholdMS: 15,
    logicalSessionTimeoutMinutes: undefined
  },
  code: undefined
}
node:internal/process/promises:288
            triggerUncaughtException(err, true /* fromPromise */);
            ^

MongooseServerSelectionError: getaddrinfo EAI_AGAIN mongodb
    at Connection.openUri (/var/www/node_modules/mongoose/lib/connection.js:819:32)
    at /var/www/node_modules/mongoose/lib/index.js:379:10
    at /var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:32:5
    at new Promise (<anonymous>)
    at promiseOrCallback (/var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:31:10)
    at Mongoose._promiseOrCallback (/var/www/node_modules/mongoose/lib/index.js:1224:10)
    at Mongoose.connect (/var/www/node_modules/mongoose/lib/index.js:378:20)
    at Object.init (/var/www/lib/database.js:16:22)
    at Object.<anonymous> (/var/www/server.js:41:4)
    at Module._compile (node:internal/modules/cjs/loader:1119:14) {
  reason: TopologyDescription {
    type: 'Unknown',
    servers: Map(1) {
      'mongodb:27017' => ServerDescription {
        _hostAddress: HostAddress { isIPv6: false, host: 'mongodb', port: 27017 },
        address: 'mongodb:27017',
        type: 'Unknown',
        hosts: [],
        passives: [],
        arbiters: [],
        tags: {},
        minWireVersion: 0,
        maxWireVersion: 0,
        roundTripTime: -1,
        lastUpdateTime: 6694197,
        lastWriteDate: 0,
        error: MongoNetworkError: getaddrinfo EAI_AGAIN mongodb
            at connectionFailureError (/var/www/node_modules/mongodb/lib/cmap/connect.js:382:20)
            at Socket.<anonymous> (/var/www/node_modules/mongodb/lib/cmap/connect.js:302:22)
            at Object.onceWrapper (node:events:628:26)
            at Socket.emit (node:events:513:28)
            at emitErrorNT (node:internal/streams/destroy:151:8)
          [Symbol(errorLabels)]: Set(0) {}
        }
      }
    },
    stale: false,
    compatible: true,
    heartbeatFrequencyMS: 10000,
    localThresholdMS: 15,
    logicalSessionTimeoutMinutes: undefined
  },
  code: undefined
}

Node.js v18.9.0
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main\nginx> cd ..
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker network ;s

Usage:  docker network COMMAND

Manage networks

Commands:
  connect     Connect a container to a network
  create      Create a network
  disconnect  Disconnect a container from a network
  inspect     Display detailed information on one or more networks
  ls          List networks
  prune       Remove all unused networks
  rm          Remove one or more networks

Run 'docker network COMMAND --help' for more information on a command.
s : The term 's' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, 
verify that the path is correct and try again.
At line:1 char:17
+ docker network ;s
+                 ~
    + CategoryInfo          : ObjectNotFound: (s:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker network ls
NETWORK ID     NAME              DRIVER    SCOPE
2108109dbe9e   bridge            bridge    local
a14fba8ddb0b   docker_gwbridge   bridge    local
7708b89f0246   host              host      local
inx2szobygkt   ingress           overlay   swarm
4113a7b6dfac   none              null      local
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker network create --driver bridge isolated_network
adc2a4e1a9de1582af95ffc6d322871563d700fedfb516f45b12bf0a490bb091
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker network ls
NETWORK ID     NAME               DRIVER    SCOPE
2108109dbe9e   bridge             bridge    local
a14fba8ddb0b   docker_gwbridge    bridge    local
7708b89f0246   host               host      local
inx2szobygkt   ingress            overlay   swarm
adc2a4e1a9de   isolated_network   bridge    local
4113a7b6dfac   none               null      local
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker run -d --net=isolated_network --name mongodb mongo
bde43ce1a487153012b111db9b912b82e9118e317daf5e6c7ff43ded600985ca
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker network ls
NETWORK ID     NAME               DRIVER    SCOPE
2108109dbe9e   bridge             bridge    local
a14fba8ddb0b   docker_gwbridge    bridge    local
7708b89f0246   host               host      local
inx2szobygkt   ingress            overlay   swarm
adc2a4e1a9de   isolated_network   bridge    local
4113a7b6dfac   none               null      local
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS       NAMES
bde43ce1a487   mongo     "docker-entrypoint.s…"   28 seconds ago   Up 26 seconds   27017/tcp   mongodb
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker run -d --net=isolated_network --name nodeapp -p 3000:3000 -v ${pwd}/logs:/var/www/logs 9620/nodeapp:1.0                                                                                                                                                                         421e3f012f32ca97761bd9593f22a2384bfa142a16bb9d12eb7d2bec554c126e
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps
CONTAINER ID   IMAGE              COMMAND                  CREATED         STATUS         PORTS                    NAMES
421e3f012f32   9620/nodeapp:1.0   "npm start"              6 seconds ago   Up 3 seconds   0.0.0.0:3000->3000/tcp   nodeapp
bde43ce1a487   mongo              "docker-entrypoint.s…"   2 minutes ago   Up 2 minutes   27017/tcp                mongodb
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker logs 421

> expressite@1.0.0 start
> node server.js

Node environment: development
loading config.development.json
Trying to connect to mongodb/funWithDocker MongoDB database
(node:17) [MONGODB DRIVER] Warning: promiseLibrary is a deprecated option
(Use `node --trace-warnings ...` to show where the warning was created)
[development] Listening on http://localhost:3000
db connection open
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker network ls
NETWORK ID     NAME               DRIVER    SCOPE
2108109dbe9e   bridge             bridge    local
a14fba8ddb0b   docker_gwbridge    bridge    local
7708b89f0246   host               host      local
inx2szobygkt   ingress            overlay   swarm
adc2a4e1a9de   isolated_network   bridge    local
4113a7b6dfac   none               null      local
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker network inspect adc
[
    {
        "Name": "isolated_network",
        "Id": "adc2a4e1a9de1582af95ffc6d322871563d700fedfb516f45b12bf0a490bb091",
        "Created": "2022-09-24T06:55:10.9376458Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.21.0.0/16",
                    "Gateway": "172.21.0.1"
                "EndpointID": "91cb04372f2bb10ecf534f87255a2dbf6dae997fe98722daf3bb4e581aac118a",
                "MacAddress": "02:42:ac:15:00:03",
                "IPv4Address": "172.21.0.3/16",
                "IPv6Address": ""
            },
            "bde43ce1a487153012b111db9b912b82e9118e317daf5e6c7ff43ded600985ca": {
                "Name": "mongodb",
                "EndpointID": "b2d76493a70c48684f0602f634ce7098ea9ea2efc1ae97cdd310d3d2445679f1",
                "MacAddress": "02:42:ac:15:00:02",
                "IPv4Address": "172.21.0.2/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]

---------------- Different Terminal----------------

Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS              PORTS                    NAMES
97eff8547d48   nodeapp   "npm start"              About a minute ago   Up About a minute   0.0.0.0:3000->3000/tcp   nodeapp
804a926f9c39   mongo     "docker-entrypoint.s…"   About a minute ago   Up About a minute   27017/tcp                mongodb
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker exec -t 97eff8547d48 sh
/var/www #
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker exec -t 97eff8547d48 sh
/var/www #
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker exec -it 97eff8547d48 sh
/var/www # node dbSeeder.js
Trying to connect to mongodb/funWithDocker MongoDB database
Initializing Data
Data Initialized!
(node:46) [MONGODB DRIVER] Warning: promiseLibrary is a deprecated option
(Use `node --trace-warnings ...` to show where the warning was created)
db connection open
^C
/var/www # exit
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker-compose down
[+] Running 3/3
 - Container nodeapp                                         Removed                                                                                                            1.4s
 - Container mongodb                                         Removed                                                                                                            0.5s
 - Network nodeexpressmongodbdockerapp-main_nodeapp-network  Removed                                                                                                            0.6s
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker build -t nodeapp .
[+] Building 0.1s (2/2) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                                                                        0.1s
 => => transferring dockerfile: 2B                                                                                                                                                                          0.0s 
 => [internal] load .dockerignore                                                                                                                                                                           0.1s 
 => => transferring context: 52B                                                                                                                                                                            0.0s 
failed to solve with frontend dockerfile.v0: failed to read dockerfile: open /var/lib/docker/tmp/buildkit-mount232728908/Dockerfile: no such file or directory
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker build -t nodeapp -f .\node.dockerfile
"docker build" requires exactly 1 argument.
See 'docker build --help'.

Usage:  docker build [OPTIONS] PATH | URL | -

Build an image from a Dockerfile
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker build -t nodeapp -f .\node.dockerfile .
[+] Building 17.9s (12/12) FINISHED
 => [internal] load build definition from node.dockerfile                                                                                                                                                   0.0s
 => => transferring dockerfile: 1.23kB                                                                                                                                                                      0.0s 
 => [internal] load .dockerignore                                                                                                                                                                           0.1s 
 => => transferring context: 34B                                                                                                                                                                            0.0s 
 => [internal] load metadata for docker.io/library/node:alpine                                                                                                                                              3.1s
 => [auth] library/node:pull token for registry-1.docker.io                                                                                                                                                 0.0s
 => CACHED [1/6] FROM docker.io/library/node:alpine@sha256:831d5eca5b7437a8132031a25bd18bdb0399e7415d4e8e02a8c14426b6dcf17f                                                                                 0.0s
 => [internal] load build context                                                                                                                                                                           0.2s 
 => => transferring context: 4.11MB                                                                                                                                                                         0.1s 
 => [2/6] RUN         apk update && apk add nano                                                                                                                                                            5.5s 
 => [3/6] WORKDIR     /var/www                                                                                                                                                                              0.1s
 => [4/6] COPY        package.json package-lock.json ./                                                                                                                                                     0.1s
 => [5/6] RUN         npm install                                                                                                                                                                           7.7s
 => [6/6] COPY        . ./                                                                                                                                                                                  0.1s
 => exporting to image                                                                                                                                                                                      0.9s
 => => exporting layers                                                                                                                                                                                     0.9s
 => => writing image sha256:ee503dd44ef43889ae262ed57f60802eeec4599c645b1cbc5614fb9a3c59fe33                                                                                                                0.0s
 => => naming to docker.io/library/nodeapp                                                                                                                                                                  0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker images
REPOSITORY                                                TAG                                                                          IMAGE ID       CREATED          SIZE
nodeapp                                                   latest                                                                       ee503dd44ef4   23 seconds ago   253MB
<none>                                                    <none>                                                                       6d6996c8f03a   18 minutes ago   257MB
nigelpoulton/gsd                                          swarm-stack                                                                  37ec379c40b7   39 minutes ago   64.1MB
multi-container-web-fe                                    latest                                                                       3c8f966a1782   57 minutes ago   64.1MB
9620/gsd                                                  first-ctr                                                                    875e37fba1e3   11 hours ago     181MB
canary-app                                                latest                                                                       bfeee798dbdf   13 hours ago     212MB
stable-app                                                latest                                                                       8a868f2d805c   13 hours ago     212MB
redis                                                     alpine                                                                       0139e7020436   37 hours ago     28.5MB
mongo                                                     latest                                                                       d34d21a9eb5b   3 weeks ago      693MB
hubproxy.docker.internal:5000/docker/desktop-kubernetes   kubernetes-v1.25.0-cni-v1.1.1-critools-v1.24.2-cri-dockerd-v0.2.5-1-debian   2042e761d17a   4 weeks ago      363MB
k8s.gcr.io/kube-apiserver                                 v1.25.0                                                                      4d2edfd10d3e   4 weeks ago      128MB
k8s.gcr.io/kube-controller-manager                        v1.25.0                                                                      1a54c86c03a6   4 weeks ago      117MB
k8s.gcr.io/kube-scheduler                                 v1.25.0                                                                      bef2cf311509   4 weeks ago      50.6MB
k8s.gcr.io/kube-proxy                                     v1.25.0                                                                      58a9a0c6d96f   4 weeks ago      61.7MB
k8s.gcr.io/pause                                          3.8                                                                          4873874c08ef   3 months ago     711kB
k8s.gcr.io/etcd                                           3.5.4-0                                                                      a8a176a5d5d6   3 months ago     300MB
k8s.gcr.io/coredns                                        v1.9.3                                                                       5185b96f0bec   3 months ago     48.8MB
docker/desktop-vpnkit-controller                          v2.0                                                                         8c2c38aa676e   16 months ago    21MB
docker/desktop-storage-provisioner                        v2.0                                                                         99f89471f470   17 months ago    41.9MB
nigelpoulton/gsd                                          <none>                                                                       133e46ff8173   23 months ago    56.3MB
nginx                                                     1.16.1-alpine                                                                5fad07aba15a   2 years ago      21.8MB
nginx                                                     1.17.8-alpine                                                                48c8a7c47625   2 years ago      21.8MB
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker rmi ee5
Untagged: nodeapp:latest
Deleted: sha256:ee503dd44ef43889ae262ed57f60802eeec4599c645b1cbc5614fb9a3c59fe33
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker build -t 9620/nodeapp:1.0 -f .\node.dockerfile .
[+] Building 1.2s (11/11) FINISHED
 => [internal] load build definition from node.dockerfile                                                                                                                                                   0.0s
 => => transferring dockerfile: 37B                                                                                                                                                                         0.0s 
 => [internal] load .dockerignore                                                                                                                                                                           0.0s 
 => => transferring context: 34B                                                                                                                                                                            0.0s 
 => [internal] load metadata for docker.io/library/node:alpine                                                                                                                                              1.1s 
 => [1/6] FROM docker.io/library/node:alpine@sha256:831d5eca5b7437a8132031a25bd18bdb0399e7415d4e8e02a8c14426b6dcf17f                                                                                        0.0s
 => [internal] load build context                                                                                                                                                                           0.0s 
 => => transferring context: 1.54kB                                                                                                                                                                         0.0s 
 => CACHED [2/6] RUN         apk update && apk add nano                                                                                                                                                     0.0s
 => CACHED [3/6] WORKDIR     /var/www                                                                                                                                                                       0.0s 
 => CACHED [4/6] COPY        package.json package-lock.json ./                                                                                                                                              0.0s 
 => CACHED [5/6] RUN         npm install                                                                                                                                                                    0.0s 
 => CACHED [6/6] COPY        . ./                                                                                                                                                                           0.0s 
 => exporting to image                                                                                                                                                                                      0.0s 
 => => exporting layers                                                                                                                                                                                     0.0s 
 => => writing image sha256:ee503dd44ef43889ae262ed57f60802eeec4599c645b1cbc5614fb9a3c59fe33                                                                                                                0.0s 
 => => naming to docker.io/9620/nodeapp:1.0                                                                                                                                                                 0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker images
REPOSITORY                                                TAG                                                                          IMAGE ID       CREATED          SIZE
9620/nodeapp                                              1.0                                                                          ee503dd44ef4   59 seconds ago   253MB
<none>                                                    <none>                                                                       6d6996c8f03a   18 minutes ago   257MB
nigelpoulton/gsd                                          swarm-stack                                                                  37ec379c40b7   40 minutes ago   64.1MB
multi-container-web-fe                                    latest                                                                       3c8f966a1782   57 minutes ago   64.1MB
9620/gsd                                                  first-ctr                                                                    875e37fba1e3   11 hours ago     181MB
canary-app                                                latest                                                                       bfeee798dbdf   13 hours ago     212MB
stable-app                                                latest                                                                       8a868f2d805c   13 hours ago     212MB
redis                                                     alpine                                                                       0139e7020436   37 hours ago     28.5MB
mongo                                                     latest                                                                       d34d21a9eb5b   3 weeks ago      693MB
hubproxy.docker.internal:5000/docker/desktop-kubernetes   kubernetes-v1.25.0-cni-v1.1.1-critools-v1.24.2-cri-dockerd-v0.2.5-1-debian   2042e761d17a   4 weeks ago      363MB
k8s.gcr.io/kube-apiserver                                 v1.25.0                                                                      4d2edfd10d3e   4 weeks ago      128MB
k8s.gcr.io/kube-scheduler                                 v1.25.0                                                                      bef2cf311509   4 weeks ago      50.6MB
k8s.gcr.io/kube-controller-manager                        v1.25.0                                                                      1a54c86c03a6   4 weeks ago      117MB
k8s.gcr.io/kube-proxy                                     v1.25.0                                                                      58a9a0c6d96f   4 weeks ago      61.7MB
k8s.gcr.io/pause                                          3.8                                                                          4873874c08ef   3 months ago     711kB
k8s.gcr.io/etcd                                           3.5.4-0                                                                      a8a176a5d5d6   3 months ago     300MB
k8s.gcr.io/coredns                                        v1.9.3                                                                       5185b96f0bec   3 months ago     48.8MB
docker/desktop-vpnkit-controller                          v2.0                                                                         8c2c38aa676e   16 months ago    21MB
docker/desktop-storage-provisioner                        v2.0                                                                         99f89471f470   17 months ago    41.9MB
nigelpoulton/gsd                                          <none>                                                                       133e46ff8173   23 months ago    56.3MB
nginx                                                     1.16.1-alpine                                                                5fad07aba15a   2 years ago      21.8MB
nginx                                                     1.17.8-alpine                                                                48c8a7c47625   2 years ago      21.8MB
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker login
Authenticating with existing credentials...
Login Succeeded

Logging in with your password grants your terminal complete access to your account.
For better security, log in with a limited-privilege personal access token. Learn more at https://docs.docker.com/go/access-tokens/
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker push 9620/nodeapp:1.0
The push refers to repository [docker.io/9620/nodeapp]
cc1b357419b9: Pushed
ce24343fcb19: Pushed
8ab576995af3: Pushed
838cb81af776: Pushed
dc1876f5afb1: Pushed
59f06579c95e: Mounted from 9620/gsd
2285e09e0a3a: Mounted from 9620/gsd
28d524b96681: Mounted from 9620/gsd
994393dc58e7: Mounted from 9620/gsd
1.0: digest: sha256:74a0b42ba8a903275f7e04f4a9ee30048c846bb13a482b5b59fb0c30282e7324 size: 2207
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker pull 9620/nodeapp:1.0
1.0: Pulling from 9620/nodeapp
Digest: sha256:74a0b42ba8a903275f7e04f4a9ee30048c846bb13a482b5b59fb0c30282e7324
Status: Image is up to date for 9620/nodeapp:1.0
docker.io/9620/nodeapp:1.0
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker pull nginx:alphine
Error response from daemon: manifest for nginx:alphine not found: manifest unknown: manifest unknown
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker pull nginx:alpine 
alpine: Pulling from library/nginx
213ec9aee27d: Already exists
2546ae67167b: Pull complete
23b845224e13: Pull complete
9bd5732789a3: Pull complete
328309e59ded: Pull complete
b231d02e5150: Pull complete
Digest: sha256:082f8c10bd47b6acc8ef15ae61ae45dd8fde0e9f389a8b5cb23c37408642bf5d
Status: Downloaded newer image for nginx:alpine
docker.io/library/nginx:alpine
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker run --help

Usage:  docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

Run a command in a new container

Options:
      --add-host list                  Add a custom host-to-IP mapping
                                       (host:ip)
  -a, --attach list                    Attach to STDIN, STDOUT or STDERR
      --blkio-weight uint16            Block IO (relative weight),
                                       between 10 and 1000, or 0 to
                                       disable (default 0)
      --blkio-weight-device list       Block IO weight (relative device
                                       weight) (default [])
      --cap-add list                   Add Linux capabilities
      --cap-drop list                  Drop Linux capabilities
      --cgroup-parent string           Optional parent cgroup for the
                                       container
      --cgroupns string                Cgroup namespace to use
                                       (host|private)
                                       'host':    Run the container in
                                       the Docker host's cgroup namespace
                                       'private': Run the container in
                                       its own private cgroup namespace
                                       '':        Use the cgroup
                                       namespace as configured by the
                                                  default-cgroupns-mode
                                       option on the daemon (default)
      --cidfile string                 Write the container ID to the file
      --cpu-period int                 Limit CPU CFS (Completely Fair
                                       Scheduler) period
      --cpu-quota int                  Limit CPU CFS (Completely Fair
                                       Scheduler) quota
      --cpu-rt-period int              Limit CPU real-time period in
                                       microseconds
      --cpu-rt-runtime int             Limit CPU real-time runtime in
                                       microseconds
  -c, --cpu-shares int                 CPU shares (relative weight)
      --cpus decimal                   Number of CPUs
      --cpuset-cpus string             CPUs in which to allow execution
                                       (0-3, 0,1)
      --cpuset-mems string             MEMs in which to allow execution
                                       (0-3, 0,1)
  -d, --detach                         Run container in background and
                                       print container ID
      --detach-keys string             Override the key sequence for
                                       detaching a container
      --device list                    Add a host device to the container
      --device-cgroup-rule list        Add a rule to the cgroup allowed
                                       devices list
      --device-read-bps list           Limit read rate (bytes per second)
                                       from a device (default [])
      --device-read-iops list          Limit read rate (IO per second)
                                       from a device (default [])
      --device-write-bps list          Limit write rate (bytes per
                                       second) to a device (default [])
      --device-write-iops list         Limit write rate (IO per second)
                                       to a device (default [])
      --disable-content-trust          Skip image verification (default true)
      --dns list                       Set custom DNS servers
      --dns-option list                Set DNS options
      --dns-search list                Set custom DNS search domains
      --domainname string              Container NIS domain name
      --entrypoint string              Overwrite the default ENTRYPOINT
                                       of the image
  -e, --env list                       Set environment variables
      --env-file list                  Read in a file of environment variables
      --expose list                    Expose a port or a range of ports
      --gpus gpu-request               GPU devices to add to the
                                       container ('all' to pass all GPUs)
      --group-add list                 Add additional groups to join
      --health-cmd string              Command to run to check health
      --health-interval duration       Time between running the check
                                       (ms|s|m|h) (default 0s)
      --health-retries int             Consecutive failures needed to
                                       report unhealthy
      --health-start-period duration   Start period for the container to
                                       initialize before starting
                                       health-retries countdown
                                       (ms|s|m|h) (default 0s)
      --health-timeout duration        Maximum time to allow one check to
                                       run (ms|s|m|h) (default 0s)
      --help                           Print usage
  -h, --hostname string                Container host name
      --init                           Run an init inside the container
                                       that forwards signals and reaps
                                       processes
  -i, --interactive                    Keep STDIN open even if not attached
      --ip string                      IPv4 address (e.g., 172.30.100.104)
      --ip6 string                     IPv6 address (e.g., 2001:db8::33)
      --ipc string                     IPC mode to use
      --isolation string               Container isolation technology
      --kernel-memory bytes            Kernel memory limit
  -l, --label list                     Set meta data on a container
      --label-file list                Read in a line delimited file of labels
      --link list                      Add link to another container
      --link-local-ip list             Container IPv4/IPv6 link-local
                                       addresses
      --log-driver string              Logging driver for the container
      --log-opt list                   Log driver options
      --mac-address string             Container MAC address (e.g.,
                                       92:d0:c6:0a:29:33)
  -m, --memory bytes                   Memory limit
      --memory-reservation bytes       Memory soft limit
      --memory-swap bytes              Swap limit equal to memory plus
                                       swap: '-1' to enable unlimited swap
      --memory-swappiness int          Tune container memory swappiness
                                       (0 to 100) (default -1)
      --mount mount                    Attach a filesystem mount to the
                                       container
      --name string                    Assign a name to the container
      --network network                Connect a container to a network
      --network-alias list             Add network-scoped alias for the
                                       container
      --no-healthcheck                 Disable any container-specified
                                       HEALTHCHECK
      --oom-kill-disable               Disable OOM Killer
      --oom-score-adj int              Tune host's OOM preferences (-1000
                                       to 1000)
      --pid string                     PID namespace to use
      --pids-limit int                 Tune container pids limit (set -1
                                       for unlimited)
      --platform string                Set platform if server is
                                       multi-platform capable
      --privileged                     Give extended privileges to this
                                       container
  -p, --publish list                   Publish a container's port(s) to
                                       the host
  -P, --publish-all                    Publish all exposed ports to
                                       random ports
      --pull string                    Pull image before running
                                       ("always"|"missing"|"never")
                                       (default "missing")
      --read-only                      Mount the container's root
                                       filesystem as read only
      --restart string                 Restart policy to apply when a
                                       container exits (default "no")
      --rm                             Automatically remove the container
                                       when it exits
      --runtime string                 Runtime to use for this container
      --security-opt list              Security Options
      --shm-size bytes                 Size of /dev/shm
      --sig-proxy                      Proxy received signals to the
                                       process (default true)
      --stop-signal string             Signal to stop a container
                                       (default "15")
      --stop-timeout int               Timeout (in seconds) to stop a
                                       container
      --storage-opt list               Storage driver options for the
                                       container
      --sysctl map                     Sysctl options (default map[])
      --tmpfs list                     Mount a tmpfs directory
  -t, --tty                            Allocate a pseudo-TTY
      --ulimit ulimit                  Ulimit options (default [])
  -u, --user string                    Username or UID (format:
                                       <name|uid>[:<group|gid>])
      --userns string                  User namespace to use
      --uts string                     UTS namespace to use
  -v, --volume list                    Bind mount a volume
      --volume-driver string           Optional volume driver for the
                                       container
      --volumes-from list              Mount volumes from the specified
                                       container(s)
  -w, --workdir string                 Working directory inside the container
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker images
REPOSITORY                                                TAG                                                                          IMAGE ID       CREATED             
SIZE
9620/nodeapp                                              1.0                                                                          ee503dd44ef4   12 minutes ago      253MB
<none>                                                    <none>                                                                       6d6996c8f03a   30 minutes ago      257MB
nigelpoulton/gsd                                          swarm-stack                                                                  37ec379c40b7   51 minutes ago      64.1MB
multi-container-web-fe                                    latest                                                                       3c8f966a1782   About an hour ago   64.1MB
9620/gsd                                                  first-ctr                                                                    875e37fba1e3   12 hours ago        181MB
stable-app                                                latest                                                                       8a868f2d805c   13 hours ago        212MB
canary-app                                                latest                                                                       bfeee798dbdf   13 hours ago        212MB
redis                                                     alpine                                                                       0139e7020436   37 hours ago        28.5MB
mongo                                                     latest                                                                       d34d21a9eb5b   3 weeks ago         
693MB
hubproxy.docker.internal:5000/docker/desktop-kubernetes   kubernetes-v1.25.0-cni-v1.1.1-critools-v1.24.2-cri-dockerd-v0.2.5-1-debian   2042e761d17a   4 weeks ago         
363MB
k8s.gcr.io/kube-apiserver                                 v1.25.0                                                                      4d2edfd10d3e   4 weeks ago         
128MB
k8s.gcr.io/kube-scheduler                                 v1.25.0                                                                      bef2cf311509   4 weeks ago         
50.6MB
k8s.gcr.io/kube-controller-manager                        v1.25.0                                                                      1a54c86c03a6   4 weeks ago         
117MB
k8s.gcr.io/kube-proxy                                     v1.25.0                                                                      58a9a0c6d96f   4 weeks ago         
61.7MB
nginx                                                     alpine                                                                       804f9cebfdc5   6 weeks ago         
23.5MB
k8s.gcr.io/pause                                          3.8                                                                          4873874c08ef   3 months ago        711kB
k8s.gcr.io/etcd                                           3.5.4-0                                                                      a8a176a5d5d6   3 months ago        300MB
k8s.gcr.io/coredns                                        v1.9.3                                                                       5185b96f0bec   3 months ago        48.8MB
docker/desktop-vpnkit-controller                          v2.0                                                                         8c2c38aa676e   16 months ago       21MB
docker/desktop-storage-provisioner                        v2.0                                                                         99f89471f470   17 months ago       41.9MB
nigelpoulton/gsd                                          <none>                                                                       133e46ff8173   23 months ago       56.3MB
nginx                                                     1.16.1-alpine                                                                5fad07aba15a   2 years ago         
21.8MB
nginx                                                     1.17.8-alpine                                                                48c8a7c47625   2 years ago         
21.8MB
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker run -p 8080:80 nginx:alpine -d
/docker-entrypoint.sh: exec: line 38: illegal option -d
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker run -p 8080:80 -d nginx:alpine 
5f62aeb4f401a5b5feb88c82654a0d3c3445d24486f7e0be79a3f4c63d5bffef
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
Error response from daemon: You cannot remove a running container cee63fa4db4dd1f1c7308b25ef7f54e6cccdffaf5393cd128e04bf2730311c7b. Stop the container before attempting removal or force remove
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker stop 5f
5f
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker rm 5f
5f
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS                          PORTS     NAMES
307a3692a957   nginx:alpine   "/docker-entrypoint.…"   About a minute ago   Exited (2) About a minute ago             admiring_varahamihira
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker stop 30
Error response from daemon: Multiple IDs found with provided prefix: 30
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker stop 307
307
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker rm 307
307
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker pull 9620/nodeapp:1.0
1.0: Pulling from 9620/nodeapp
Digest: sha256:74a0b42ba8a903275f7e04f4a9ee30048c846bb13a482b5b59fb0c30282e7324
Status: Image is up to date for 9620/nodeapp:1.0
docker.io/9620/nodeapp:1.0
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker run -p 3000:3000 -d 9620/nodeapp:1.0
afe9182b29964f2a07542b06c297cd4ce7b44017778aa0e237d414a761e37674
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
CONTAINER ID   IMAGE              COMMAND       CREATED         STATUS         PORTS                    NAMES
afe9182b2996   9620/nodeapp:1.0   "npm start"   8 seconds ago   Up 7 seconds   0.0.0.0:3000->3000/tcp   determined_vaughan
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker logs afe9182b2996

> expressite@1.0.0 start
> node server.js

Node environment: development
loading config.development.json
Trying to connect to mongodb/funWithDocker MongoDB database
(node:17) [MONGODB DRIVER] Warning: promiseLibrary is a deprecated option
(Use `node --trace-warnings ...` to show where the warning was created)
[development] Listening on http://localhost:3000
connection error: MongooseServerSelectionError: getaddrinfo EAI_AGAIN mongodb
    at Connection.openUri (/var/www/node_modules/mongoose/lib/connection.js:819:32)
    at /var/www/node_modules/mongoose/lib/index.js:379:10
    at /var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:32:5
    at new Promise (<anonymous>)
    at promiseOrCallback (/var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:31:10)
    at Mongoose._promiseOrCallback (/var/www/node_modules/mongoose/lib/index.js:1224:10)
    at Mongoose.connect (/var/www/node_modules/mongoose/lib/index.js:378:20)
    at Object.init (/var/www/lib/database.js:16:22)
    at Object.<anonymous> (/var/www/server.js:41:4)
    at Module._compile (node:internal/modules/cjs/loader:1119:14) {
  reason: TopologyDescription {
    type: 'Unknown',
    servers: Map(1) { 'mongodb:27017' => [ServerDescription] },
    stale: false,
    compatible: true,
    heartbeatFrequencyMS: 10000,
    localThresholdMS: 15,
    logicalSessionTimeoutMinutes: undefined
  },
  code: undefined
}
node:internal/process/promises:288
            triggerUncaughtException(err, true /* fromPromise */);
            ^

MongooseServerSelectionError: getaddrinfo EAI_AGAIN mongodb
    at Connection.openUri (/var/www/node_modules/mongoose/lib/connection.js:819:32)
    at /var/www/node_modules/mongoose/lib/index.js:379:10
    at /var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:32:5
    at new Promise (<anonymous>)
    at promiseOrCallback (/var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:31:10)
    at Mongoose._promiseOrCallback (/var/www/node_modules/mongoose/lib/index.js:1224:10)
    at Mongoose.connect (/var/www/node_modules/mongoose/lib/index.js:378:20)
    at Object.init (/var/www/lib/database.js:16:22)
    at Object.<anonymous> (/var/www/server.js:41:4)
    at Module._compile (node:internal/modules/cjs/loader:1119:14) {
  reason: TopologyDescription {
    type: 'Unknown',
    servers: Map(1) {
      'mongodb:27017' => ServerDescription {
        _hostAddress: HostAddress { isIPv6: false, host: 'mongodb', port: 27017 },
        address: 'mongodb:27017',
        type: 'Unknown',
        hosts: [],
        passives: [],
        arbiters: [],
        tags: {},
        minWireVersion: 0,
        maxWireVersion: 0,
        roundTripTime: -1,
        lastUpdateTime: 5599559,
        lastWriteDate: 0,
        error: MongoNetworkError: getaddrinfo EAI_AGAIN mongodb
            at connectionFailureError (/var/www/node_modules/mongodb/lib/cmap/connect.js:382:20)
            at Socket.<anonymous> (/var/www/node_modules/mongodb/lib/cmap/connect.js:302:22)
            at Object.onceWrapper (node:events:628:26)
            at Socket.emit (node:events:513:28)
            at emitErrorNT (node:internal/streams/destroy:151:8)
            at emitErrorCloseNT (node:internal/streams/destroy:116:3)
            at process.processTicksAndRejections (node:internal/process/task_queues:82:21) {
          [Symbol(errorLabels)]: Set(0) {}
        }
      }
    },
    stale: false,
    compatible: true,
    heartbeatFrequencyMS: 10000,
    localThresholdMS: 15,
    logicalSessionTimeoutMinutes: undefined
  },
  code: undefined
}

Node.js v18.9.0
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
CONTAINER ID   IMAGE              COMMAND       CREATED              STATUS                          PORTS     NAMES
afe9182b2996   9620/nodeapp:1.0   "npm start"   About a minute ago   Exited (1) About a minute ago             determined_vaughan
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker rm af
af
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker run -p 3000:3000 9620/nodeapp:1.0   

> expressite@1.0.0 start
> node server.js

Node environment: development
loading config.development.json
Trying to connect to mongodb/funWithDocker MongoDB database
(node:17) [MONGODB DRIVER] Warning: promiseLibrary is a deprecated option
(Use `node --trace-warnings ...` to show where the warning was created)
[development] Listening on http://localhost:3000
connection error: MongooseServerSelectionError: getaddrinfo EAI_AGAIN mongodb
    at Connection.openUri (/var/www/node_modules/mongoose/lib/connection.js:819:32)
    at /var/www/node_modules/mongoose/lib/index.js:379:10
    at /var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:32:5
    at new Promise (<anonymous>)
    at promiseOrCallback (/var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:31:10)
    at Mongoose._promiseOrCallback (/var/www/node_modules/mongoose/lib/index.js:1224:10)
    at Mongoose.connect (/var/www/node_modules/mongoose/lib/index.js:378:20)
    at Object.init (/var/www/lib/database.js:16:22)
    at Object.<anonymous> (/var/www/server.js:41:4)
    at Module._compile (node:internal/modules/cjs/loader:1119:14) {
  reason: TopologyDescription {
    type: 'Unknown',
    servers: Map(1) { 'mongodb:27017' => [ServerDescription] },
    stale: false,
    compatible: true,
    heartbeatFrequencyMS: 10000,
    localThresholdMS: 15,
    logicalSessionTimeoutMinutes: undefined
  },
  code: undefined
}
node:internal/process/promises:288
            triggerUncaughtException(err, true /* fromPromise */);
            ^

MongooseServerSelectionError: getaddrinfo EAI_AGAIN mongodb
    at Connection.openUri (/var/www/node_modules/mongoose/lib/connection.js:819:32)
    at /var/www/node_modules/mongoose/lib/index.js:379:10
    at /var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:32:5
    at new Promise (<anonymous>)
    at promiseOrCallback (/var/www/node_modules/mongoose/lib/helpers/promiseOrCallback.js:31:10)
    at Mongoose._promiseOrCallback (/var/www/node_modules/mongoose/lib/index.js:1224:10)
    at Mongoose.connect (/var/www/node_modules/mongoose/lib/index.js:378:20)
    at Object.init (/var/www/lib/database.js:16:22)
    at Object.<anonymous> (/var/www/server.js:41:4)
    at Module._compile (node:internal/modules/cjs/loader:1119:14) {
  reason: TopologyDescription {
    type: 'Unknown',
    servers: Map(1) {
      'mongodb:27017' => ServerDescription {
        _hostAddress: HostAddress { isIPv6: false, host: 'mongodb', port: 27017 },
        address: 'mongodb:27017',
        type: 'Unknown',
        hosts: [],
        passives: [],
        arbiters: [],
        tags: {},
        minWireVersion: 0,
        maxWireVersion: 0,
        roundTripTime: -1,
        lastUpdateTime: 5723605,
        lastWriteDate: 0,
        error: MongoNetworkError: getaddrinfo EAI_AGAIN mongodb
            at connectionFailureError (/var/www/node_modules/mongodb/lib/cmap/connect.js:382:20)
            at Socket.<anonymous> (/var/www/node_modules/mongodb/lib/cmap/connect.js:302:22)
            at Object.onceWrapper (node:events:628:26)
            at Socket.emit (node:events:513:28)
            at emitErrorNT (node:internal/streams/destroy:151:8)
            at emitErrorCloseNT (node:internal/streams/destroy:116:3)
            at process.processTicksAndRejections (node:internal/process/task_queues:82:21) {
          [Symbol(errorLabels)]: Set(0) {}
        }
      }
    },
    stale: false,
    compatible: true,
    heartbeatFrequencyMS: 10000,
    localThresholdMS: 15,
    logicalSessionTimeoutMinutes: undefined
  },
  code: undefined
}

Node.js v18.9.0
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
CONTAINER ID   IMAGE              COMMAND       CREATED              STATUS                      PORTS     NAMES
f472f591a55d   9620/nodeapp:1.0   "npm start"   About a minute ago   Exited (1) 37 seconds ago             elegant_cartwright
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker run -p 8080:80 nginx-alpine
Unable to find image 'nginx-alpine:latest' locally
docker: Error response from daemon: pull access denied for nginx-alpine, repository does not exist or may require 'docker login': denied: requested access to the resource is denied.
See 'docker run --help'.
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker run -p 8080:80 nginx:alpine
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/09/24 06:33:14 [notice] 1#1: using the "epoll" event method
2022/09/24 06:33:14 [notice] 1#1: nginx/1.23.1
2022/09/24 06:33:14 [notice] 1#1: built by gcc 11.2.1 20220219 (Alpine 11.2.1_git20220219)
2022/09/24 06:33:14 [notice] 1#1: OS: Linux 5.10.16.3-microsoft-standard-WSL2
2022/09/24 06:33:14 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/09/24 06:33:14 [notice] 1#1: start worker processes
2022/09/24 06:33:14 [notice] 1#1: start worker process 32
2022/09/24 06:33:14 [notice] 1#1: start worker process 33
2022/09/24 06:33:14 [notice] 1#1: start worker process 34
2022/09/24 06:33:14 [notice] 1#1: start worker process 35
2022/09/24 06:33:14 [notice] 1#1: start worker process 36
2022/09/24 06:33:14 [notice] 1#1: start worker process 37
2022/09/24 06:33:14 [notice] 1#1: start worker process 38
2022/09/24 06:33:14 [notice] 1#1: start worker process 39
2022/09/24 06:33:14 [notice] 1#1: start worker process 40
2022/09/24 06:33:14 [notice] 1#1: start worker process 41
2022/09/24 06:33:14 [notice] 1#1: start worker process 42
2022/09/24 06:33:14 [notice] 1#1: start worker process 43
2022/09/24 06:36:13 [notice] 1#1: signal 3 (SIGQUIT) received, shutting down
2022/09/24 06:36:13 [notice] 33#33: gracefully shutting down
2022/09/24 06:36:13 [notice] 32#32: gracefully shutting down
2022/09/24 06:36:13 [notice] 37#37: gracefully shutting down
2022/09/24 06:36:13 [notice] 34#34: gracefully shutting down
2022/09/24 06:36:13 [notice] 38#38: gracefully shutting down
2022/09/24 06:36:13 [notice] 35#35: gracefully shutting down
2022/09/24 06:36:13 [notice] 40#40: gracefully shutting down
2022/09/24 06:36:13 [notice] 39#39: gracefully shutting down
2022/09/24 06:36:13 [notice] 32#32: exiting
2022/09/24 06:36:13 [notice] 36#36: gracefully shutting down
2022/09/24 06:36:13 [notice] 42#42: gracefully shutting down
2022/09/24 06:36:13 [notice] 34#34: exiting
2022/09/24 06:36:13 [notice] 33#33: exiting
2022/09/24 06:36:13 [notice] 40#40: exiting
2022/09/24 06:36:13 [notice] 37#37: exiting
2022/09/24 06:36:13 [notice] 38#38: exiting
2022/09/24 06:36:13 [notice] 39#39: exiting
2022/09/24 06:36:13 [notice] 36#36: exiting
2022/09/24 06:36:13 [notice] 42#42: exiting
2022/09/24 06:36:13 [notice] 35#35: exiting
2022/09/24 06:36:13 [notice] 32#32: exit
2022/09/24 06:36:13 [notice] 40#40: exit
2022/09/24 06:36:13 [notice] 37#37: exit
2022/09/24 06:36:13 [notice] 34#34: exit
2022/09/24 06:36:13 [notice] 42#42: exit
2022/09/24 06:36:13 [notice] 36#36: exit
2022/09/24 06:36:13 [notice] 39#39: exit
2022/09/24 06:36:13 [notice] 33#33: exit
2022/09/24 06:36:13 [notice] 38#38: exit
2022/09/24 06:36:13 [notice] 43#43: gracefully shutting down
2022/09/24 06:36:13 [notice] 35#35: exit
2022/09/24 06:36:13 [notice] 43#43: exiting
2022/09/24 06:36:13 [notice] 43#43: exit
2022/09/24 06:36:13 [notice] 41#41: gracefully shutting down
2022/09/24 06:36:13 [notice] 41#41: exiting
2022/09/24 06:36:13 [notice] 41#41: exit
2022/09/24 06:36:13 [notice] 1#1: signal 17 (SIGCHLD) received from 35
2022/09/24 06:36:13 [notice] 1#1: worker process 35 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: worker process 39 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:36:13 [notice] 1#1: signal 17 (SIGCHLD) received from 39
2022/09/24 06:36:13 [notice] 1#1: signal 17 (SIGCHLD) received from 43
2022/09/24 06:36:13 [notice] 1#1: worker process 43 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:36:13 [notice] 1#1: signal 17 (SIGCHLD) received from 34
2022/09/24 06:36:13 [notice] 1#1: worker process 34 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:36:13 [notice] 1#1: signal 17 (SIGCHLD) received from 36
2022/09/24 06:36:13 [notice] 1#1: worker process 33 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: worker process 36 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: worker process 37 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: worker process 38 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:36:13 [notice] 1#1: signal 17 (SIGCHLD) received from 33
2022/09/24 06:36:13 [notice] 1#1: signal 17 (SIGCHLD) received from 32
2022/09/24 06:36:13 [notice] 1#1: worker process 32 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: worker process 41 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: signal 29 (SIGIO) received
2022/09/24 06:36:13 [notice] 1#1: signal 17 (SIGCHLD) received from 42
2022/09/24 06:36:13 [notice] 1#1: worker process 42 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: signal 17 (SIGCHLD) received from 40
2022/09/24 06:36:13 [notice] 1#1: worker process 40 exited with code 0
2022/09/24 06:36:13 [notice] 1#1: exit
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker ps -a
CONTAINER ID   IMAGE              COMMAND                  CREATED              STATUS                      PORTS                  NAMES
4ad994c24267   nginx:alpine       "/docker-entrypoint.…"   About a minute ago   Up About a minute           0.0.0.0:8080->80/tcp   modest_joliot
f472f591a55d   9620/nodeapp:1.0   "npm start"              14 minutes ago       Exited (1) 13 minutes ago                          elegant_cartwright
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker stop 4a
4a
PS E:\data science\docker\NodeExpressMongoDBDockerApp-main> docker rm 4a
4a

```



