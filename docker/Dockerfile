FROM sonarqube:6.4-alpine

ENV SQ_GIT_VERSION=1.2 \
    SQ_SVN_VERSION=1.4.0.522 \
    SQ_JAVA_VERSION=4.12.0.10807 \
    SQ_JS_VERSION=3.1.1.5128 \
    SQ_PHP_VERSION=2.10.0.2087 \
    SQ_PY_VERSION=1.8.0.1496 \
    SQ_CSHARP_VERSION=6.0.0.2033 \
    SQ_XML_VERSION=1.4.2.885 \
    SQ_WEB_VERSION=2.5.0.476 \
    SQ_LDAP_VERSION=2.2.0.608 \
    SQ_GO_VERSION=1.2.8 \
    SQ_CF_VERSION=1.4.0 \
    SQ_FINDSEC_VERSION=3.5.0 \
    SQ_GITHUB_VERSION=1.4.1.822 \
    SQ_GITLAB_VERSION=2.1.0-beta1 \
    SQ_CITY_VERSION=0.9.0

RUN set -x \
    && rm -rf $SONARQUBE_HOME/lib/bundled-plugins/* \
    && cd  $SONARQUBE_HOME/extensions/plugins/ \
    && wget --no-verbose https://sonarsource.bintray.com/Distribution/sonar-scm-git-plugin/sonar-scm-git-plugin-$SQ_GIT_VERSION.jar \
    && wget --no-verbose https://sonarsource.bintray.com/Distribution/sonar-scm-svn-plugin/sonar-scm-svn-plugin-$SQ_SVN_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/java/sonar-java-plugin/$SQ_JAVA_VERSION/sonar-java-plugin-$SQ_JAVA_VERSION.jar \
    && wget --no-verbose https://sonarsource.bintray.com/Distribution/sonar-javascript-plugin/sonar-javascript-plugin-$SQ_JS_VERSION.jar \
    && wget --no-verbose https://sonarsource.bintray.com/Distribution/sonar-php-plugin/sonar-php-plugin-$SQ_PHP_VERSION.jar \
    && wget --no-verbose https://sonarsource.bintray.com/Distribution/sonar-python-plugin/sonar-python-plugin-$SQ_PY_VERSION.jar \
    && wget --no-verbose https://sonarsource.bintray.com/Distribution/sonar-csharp-plugin/sonar-csharp-plugin-$SQ_CSHARP_VERSION.jar \
    && wget --no-verbose https://sonarsource.bintray.com/Distribution/sonar-xml-plugin/sonar-xml-plugin-$SQ_XML_VERSION.jar \
    && wget --no-verbose https://sonarsource.bintray.com/Distribution/sonar-web-plugin/sonar-web-plugin-$SQ_WEB_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/ldap/sonar-ldap-plugin/$SQ_LDAP_VERSION/sonar-ldap-plugin-$SQ_LDAP_VERSION.jar \
    && wget --no-verbose https://sonarsource.bintray.com/Distribution/sonar-github-plugin/sonar-github-plugin-$SQ_GITHUB_VERSION.jar \
    && wget --no-verbose https://github.com/uartois/sonar-golang/releases/download/v$SQ_GO_VERSION/sonar-golang-plugin-$SQ_GO_VERSION.jar \
    && wget --no-verbose https://github.com/stepstone-tech/sonar-coldfusion/releases/download/$SQ_CF_VERSION/sonar-coldfusion-plugin-$SQ_CF_VERSION.jar \
    && wget --no-verbose https://github.com/gabrie-allaigre/sonar-gitlab-plugin/releases/download/$SQ_GITLAB_VERSION/sonar-gitlab-plugin-$SQ_GITLAB_VERSION.jar \
    && wget --no-verbose https://github.com/SonarQubeCommunity/sonar-findbugs/releases/download/$SQ_FINDSEC_VERSION/sonar-findbugs-plugin.jar \
    && wget --no-verbose https://github.com/stefanrinderle/softvis3d/releases/download/softvis3d-$SQ_CITY_VERSION/sonar-softvis3d-plugin-$SQ_CITY_VERSION.jar

WORKDIR $SONARQUBE_HOME
COPY run.sh $SONARQUBE_HOME/bin/
RUN chmod +x $SONARQUBE_HOME/bin/run.sh
ENTRYPOINT ["./bin/run.sh"]
