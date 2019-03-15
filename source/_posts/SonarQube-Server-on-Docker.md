---
title: SonarQube Server on Docker
date: 2019-01-15 16:34:30
categories:
- SonarQube
tags:
- SonarQube
- Docker
- docker-compose
- PostgreSql
---

## SonarQube Server on Docker

### 1. 建立持久層資料夾

```
mkdir -p -m 777 ./sonarqube && mkdir -p -m 777 ./sonarqube/conf && mkdir -p -m 777 ./sonarqube/data && mkdir -p -m 777 ./sonarqube/logs && mkdir -p -m 777 ./sonarqube/extensions
```

### 2. docker-compose.yml

```
version: "3.5"
services:
    postgresql:
                container_name: "postgresql"
                image: "postgres"
                ports:
                - "5432:5432"
                volumes:
                - "/postgresql:/var/lib/postgresql/data"
                environment:
                - "POSTGRES_USER=sonar"
                - "POSTGRES_PASSWORD=sonar"
                
    sonarqube:
                container_name: "sonarqube"
                image: "sonarqube:lts"
                ports:
                - "9000:9000"
                volumes:
                - "/sonarqube/conf:/opt/sonarqube/conf"
                - "/sonarqube/data:/opt/sonarqube/data"
                - "/sonarqube/logs:/opt/sonarqube/logs"
                - "/sonarqube/extensions:/opt/sonarqube/extensions"
                environment:
                - "sonar.jdbc.username=sonar"
                - "sonar.jdbc.password=sonar"
                - "sonar.jdbc.url=jdbc:postgresql://postgresql/sonar"
                links:
                - "postgresql:postgresql"

```

### ADserver 設定

> [設定](https://docs.sonarqube.org/latest/instance-administration/delegated-auth/)

```
# LDAP configuration
# General Configuration
sonar.security.realm=LDAP
ldap.url=ldap://myserver.mycompany.com
ldap.bindDn=my_bind_dn
ldap.bindPassword=my_bind_password
  
# User Configuration
ldap.user.baseDn=ou=Users,dc=mycompany,dc=com
ldap.user.request=(&(objectClass=inetOrgPerson)(uid={login}))
ldap.user.realNameAttribute=cn
ldap.user.emailAttribute=mail
 
# Group Configuration
ldap.group.baseDn=ou=Groups,dc=sonarsource,dc=com
ldap.group.request=(&(objectClass=posixGroup)(memberUid={uid}))
```



#參考
[sonarqube-postgres-docker.md](https://gist.github.com/ceduliocezar/b3bf93125024482b5f2f479696842046)
[postgres docker](https://hub.docker.com/_/postgres)
[sonarqube docker](https://hub.docker.com/_/sonarqube/)