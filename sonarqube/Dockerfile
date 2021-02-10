FROM sonarqube:8.6.1-community

ENV SONARQUBE_HOME /opt/sonarqube

RUN wget -nv "https://github.com/checkstyle/sonar-checkstyle/releases/download/8.39/checkstyle-sonar-plugin-8.39.jar" && \
	wget -nv "https://github.com/willemsrb/sonar-jdepend-plugin/releases/download/sonar-jdepend-plugin-1.1.1/sonar-jdepend-plugin-1.1.1.jar" && \
	wget -nv "https://github.com/sbaudoin/sonar-yaml/releases/download/v1.5.2/sonar-yaml-plugin-1.5.2.jar" && \
	wget -nv "https://github.com/kwoding/sonar-webdriver-plugin/releases/download/sonar-webdriver-plugin-1.0.7/sonar-webdriver-plugin-1.0.7.jar" && \
	wget -nv "https://github.com/sbaudoin/sonar-shellcheck/releases/download/v2.4.0/sonar-shellcheck-plugin-2.4.0.jar" && \
	wget -nv "https://github.com/ZoeThivet/sonar-l10n-fr/releases/download/1.15.1/sonar-l10n-fr-plugin-1.15.1.jar"  && \
	wget -nv "https://github.com/spotbugs/sonar-findbugs/releases/download/4.0.3/sonar-findbugs-plugin-4.0.3.jar" && \
	wget -nv "https://github.com/edwinyangzh/sonar-java-i18n-checks/releases/download/v0.1.0/java-i18n-rules-0.1.0.jar" && \
	wget -nv "https://github.com/dependency-check/dependency-check-sonar-plugin/releases/download/2.0.7/sonar-dependency-check-plugin-2.0.7.jar" && \
	wget -nv "https://github.com/mc1arke/sonarqube-community-branch-plugin/releases/download/1.6.0/sonarqube-community-branch-plugin-1.6.0.jar" && \
	cp sonarqube-community-branch-plugin-1.6.0.jar $SONARQUBE_HOME/lib/common && \ 
    	mv *.jar $SONARQUBE_HOME/extensions/plugins && \
    	ls -lah $SONARQUBE_HOME/extensions/plugins
