# SonarQube

## Install
Clone this repository and run :

```console
docker-compose up -d
```

ElisaticSearch in sonarQube needs a specifi system configuration :
```console
sysctl -w vm.max_map_count=262144
```
to make it permanent  
```console
echo "vm.max_map_count=262144" >> /etc/sysctl.conf
```

Read the docker-compose.yml for details.

Browse http://localhost:9000 with admin/admin (need to be changed at first run).

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
export SONAR_TOKEN=....
```

and run a maven compilation and a sonar analysis (see the [documentation](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-maven/) for details).

```console
mvn clean install
mvn sonar:sonar  \
	-D sonar.branch.name="$(git rev-parse --abbrev-ref HEAD|tr / _ )" \
	-DskipTests=true \
	--activate-profiles sonar
```
