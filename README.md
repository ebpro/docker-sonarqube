# SonarQube

## Install
Clone this repository.
Copy the asset version 1.6.0 from https://github.com/mc1arke/sonarqube-community-branch-plugin/releases in the current directory.
```console
docker-compose up -d
```

Browse http://localhost:9000 with admin/admin

Generate a security token : http://localhost:9000/account/security/ 

## Usage

Configure ~/.m2/settings.xml

```xml
<settings>
...
 <profiles>
    <profile>
      <id>sonar</id>
      <properties>
        <sonar.host.url>http://pc-bruno:9000</sonar.host.url>
        <sonar.login>${env.SONAR_TOKEN}</sonar.login>
      </properties>
    </profile>
 </profiles>
...
</settings>
```
Sets the env variable SONAR_TOKEN

```console
mvn clean install
mvn sonar:sonar  \
	-D sonar.branch.name="$(git rev-parse --abbrev-ref HEAD|tr / _ )" \
	-DskipTests=true \
	--activate-profiles sonar
```
