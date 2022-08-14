# RM-Config-Server
Referral Managment configuration are externalized using the spring cloud config server.

## Externalization sources
We have checked with github server,Postgresql and Redis as config server

### Prerequisite for application 
Before starting the application.Filling the application.properties
If you are going to start postgresql or redis. You may use docker for easy exit.
#### server.port = 8888
#### Git Config
    You have to create a repo in github and save files {applicationname}-{profile}.properties
    eg: server-development.properties, server-production.properties, server.properties
    1.spring.profiles.active=git
    2.spring.cloud.config.server.git.uri=
    3.spring.cloud.config.server.git.cloneOnStart=true
    4.spring.cloud.config.server.git.username=
    5.spring.cloud.config.server.git.password=
    6.spring.cloud.config.server.git.default-label=master
The password is token.You can generate token from your github repository.
Once the server is started.You can check the properties.
eg: http://localhost:8888/{applicationname}/{profile}

### JDBC Config
    1.spring.datasource.hikari.connection-timeout=5000
    2.spring.datasource.hikari.maximum-pool-size=10
    3.spring.datasource.driver-class-name=org.postgresql.Driver
    4.spring.datasource.url=jdbc:postgresql://localhost:5432/springconfig?useSSL=false
    5.spring.cloud.config.server.jdbc.sql= SELECT KEY, VALUE from PROPERTIES where APPLICATION=? and PROFILE=? and LABEL=?
    6.spring.datasource.username=
    7.spring.datasource.password=
    8.spring.jpa.show-sql=true
Once the server is started.You can check the properties.
eg: http://localhost:8888/{applicationname}/{profile}
### Redis config
    1.spring.redis.host=127.0.0.1
    2.spring.redis.port=6379
http://localhost:8888/{applicationname}/{profile}
