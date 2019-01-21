---
title: SonarQubeScanner for MSBuild 使用 Jenkins Pipeline
date: 2019-01-15 15:55:17
categories:
- SonarQube
tags:
- SonarQube
- Jenkins
- Pipeline
---
## SonarQubeScanner for MSBuild 使用 Jenkins Pipeline

> 使用 Jenkins Plugin 可以參考[這篇](https://ste5022424.github.io/2018/11/21/SonarQube-%E7%A8%8B%E5%BC%8F%E7%A2%BC%E5%93%81%E8%B3%AA%E5%88%86%E6%9E%90%E5%B7%A5%E5%85%B7-%E4%BD%BF%E7%94%A8-Jenkins/)，此篇是使用 Pipeline 來實現 SonarQube 掃描


### Msbuild
> sonar-scanner-msbuild-4.4.2.1543-net46 可以去[官網](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner+for+MSBuild)下載

```
node {

   VERSION = VersionNumber([projectStartDate: '2015-01-01', versionNumberString: '${YEARS_SINCE_PROJECT_START}.${BUILD_MONTH}.${BUILD_DAY}.${BUILDS_TODAY}', versionPrefix: '', worstResultForIncrement: 'NOT_BUILT'])
   TheJobName ="${env.JOB_NAME}"

    stage('Sonarqube Scan Begin'){
        echo "Sonarqube Scan Begin Start"
        bat "D:\\tools\\sonar-scanner-msbuild-4.4.2.1543-net46\\SonarQube.Scanner.MSBuild.exe begin /k:${TheJobName} /n:${TheJobName} /v:${VERSION} /d:sonar.exclusions=obj\\*,bin\\*,packages\\**,Properties\\*"
        echo "Sonarqube Scan Begin OK"
   }
   stage('Msbuild'){
       echo "Msbuild Start"
       bat "\"C:/Program Files (x86)/MSBuild/14.0/bin/amd64/msbuild.exe\" ${TheJobName}.sln /t:Rebuild /p:Configuration=Release"
       echo "Msbuild OK"
   }
   stage('Sonarqube Scan End'){
       echo "Sonarqube Scan End Start"
        bat "D:\\tools\\sonar-scanner-msbuild-4.4.2.1543-net46\\SonarQube.Scanner.MSBuild.exe end"
        echo "Sonarqube Scan End OK"
   }
}

```
### .Net Core

 > 因為要產生 coverage.opencover.xml，所以專案要先安裝 coverlet.msbuild

```
dotnet add package coverlet.msbuil
```

#### 1. Server 安裝 dotnet-sonarscanner

```
dotnet tool install --global dotnet-sonarscanner --version 4.3.1
```
#### 2. Pipeline

```
node {

   VERSION = VersionNumber([projectStartDate: '2015-01-01', versionNumberString: '${YEARS_SINCE_PROJECT_START}.${BUILD_MONTH}.${BUILD_DAY}.${BUILDS_TODAY}', versionPrefix: '', worstResultForIncrement: 'NOT_BUILT'])
   TheJobName ="${env.JOB_NAME}"

    stage('dotnet sonarscanner begin') {
        echo "dotnet sonarscanner begin Start"
        bat  "dotnet sonarscanner begin /k:${TheJobName} /n:${TheJobName} /v:${VERSION} /d:sonar.exclusions=obj\\*,bin\\*,packages\\**,Properties\\* /d:sonar.cs.opencover.reportsPaths=\"${TheJobName}.Test\\coverage.opencover.xml\" "
        echo "dotnet sonarscanner begin OK"
    }
    stage('dotnet sonarscanner build') {
        echo "dotnet sonarscanner build Start"
        bat  "dotnet build ${TheJobName}.sln -c Release -p:Version=${VERSION}"
        echo "dotnet sonarscanner build OK"
    }
    stage("dotnet sonarscanner end") {
        echo "dotnet sonarscanner end Start"
        bat  "dotnet sonarscanner end"
        echo "dotnet sonarscanner end OK"
    }
}

```
## 參考

[Analyzing with SonarScanner for MSBuild](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner+for+MSBuild)
[Code Coverage Results Import (C#, VB.NET)](https://docs.sonarqube.org/pages/viewpage.action?pageId=6389770)

[Cross platform code coverage arrives for .NET Core](http://tattoocoder.com/cross-platform-code-coverage-arrives-for-net-core/)

[Collecting test coverage using Coverlet and SonarQube for a .net core project](https://medium.com/agilix/collecting-test-coverage-using-coverlet-and-sonarqube-for-a-net-core-project-ef4a507d4b28)