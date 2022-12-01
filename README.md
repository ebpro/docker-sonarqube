# SonarQube

A ready to use sonarqube in a container.

## Configure 

ElisaticSearch in sonarQube needs a specific system configuration of the host or the VM :

```console
sysctl -w vm.max_map_count=262144
```

to make it permanent  

```console
echo "vm.max_map_count=262144" >> /etc/sysctl.conf
```

## Install
Clone this repository and run :

```console
docker-compose up -d
```


1. Read and edit the `docker-compose.yml` for details of parameters (ports and volumes).
2. Browse http://localhost:9000 with admin/admin (need to be changed at first run).
3. Generate a User security token : http://localhost:9000/account/security/ 

## Usage

Sets the environment variables SONAR_URL and SONAR_TOKEN.

```console
export SONAR_URL=http://localhost:9000
export SONAR_TOKEN=....
```

and run a maven compilation and a sonar analysis (see the [documentation](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-maven/) for details).

```console
mvn clean verify \
	sonar:sonar \
	-Dsonar.host.url=$SONAR_URL \
	-Dsonar.login=$SONAR_TOKEN \
	-Dsonar.exclusions="**/module-info.java"
```

or add a profile in `settings.xml` for a global configuration :

```xml
<profile>
  <id>sonar</id>
  <properties>
    <sonar.host.url>${env.SONAR_URL}</sonar.host.url>
    <sonar.login>${env.SONAR_TOKEN}</sonar.login>
    <sonar.exclusions>**/module-info.java</sonar.exclusions>
  </properties>
</profile>
```

```console
mvn clean verify sonar:sonar
```

if needed to run in two steps like in CI :

```console
mvn clean install
mvn sonar:sonar  \
	-D sonar.branch.name="$(git rev-parse --abbrev-ref HEAD|tr / _ )" \
	-DskipTests=true \
	--activate-profiles sonar
```
