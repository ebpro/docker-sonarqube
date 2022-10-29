FROM sonarqube:9.7.1-community

ENV SONARQUBE_HOME /opt/sonarqube

RUN wget -nv "https://github.com/checkstyle/sonar-checkstyle/releases/download/9.2/checkstyle-sonar-plugin-9.2.jar" && \
	wget -nv "https://github.com/willemsrb/sonar-jdepend-plugin/releases/download/sonar-jdepend-plugin-1.1.1/sonar-jdepend-plugin-1.1.1.jar" && \
	wget -nv "https://github.com/sbaudoin/sonar-yaml/releases/download/v1.7.0/sonar-yaml-plugin-1.7.0.jar" && \
	wget -nv "https://github.com/kwoding/sonar-webdriver-plugin/releases/download/sonar-webdriver-plugin-1.0.10/sonar-webdriver-plugin-1.0.10.jar" && \
	wget -nv "https://github.com/sbaudoin/sonar-shellcheck/releases/download/v2.5.0/sonar-shellcheck-plugin-2.5.0.jar" && \
	wget -nv "https://github.com/spotbugs/sonar-findbugs/releases/download/4.0.5/sonar-findbugs-plugin-4.0.5.jar" && \
	wget -nv "https://github.com/edwinyangzh/sonar-java-i18n-checks/releases/download/v0.1.0/java-i18n-rules-0.1.0.jar" && \
	wget -nv "https://github.com/dependency-check/dependency-check-sonar-plugin/releases/download/2.0.8/sonar-dependency-check-plugin-2.0.8.jar" && \
	wget -nv "https://github.com/mc1arke/sonarqube-community-branch-plugin/releases/download/1.10.0/sonarqube-community-branch-plugin-1.10.0.jar" && \
    	mv *.jar $SONARQUBE_HOME/extensions/plugins && \
        sed -i 's#.*sonar.web.javaAdditionalOpts=.*#sonar.web.javaAdditionalOpts=-javaagent:./extensions/plugins/sonarqube-community-branch-plugin-1.10.0.jar=web#' /opt/sonarqube/conf/sonar.properties && \
        sed -i 's#.*sonar.ce.javaAdditionalOpts=.*#sonar.ce.javaAdditionalOpts=-javaagent:./extensions/plugins/sonarqube-community-branch-plugin-1.10.0.jar=ce#' /opt/sonarqube/conf/sonar.properties 
