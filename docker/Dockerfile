FROM sonarqube:6.7-alpine

ENV SQ_GIT_VERSION=1.4.0.939 \
    SQ_SVN_VERSION=1.7.0.916 \
    SQ_JAVA_VERSION=4.16.0.12584 \
    SQ_JS_VERSION=3.4.0.5769 \
    SQ_TS_VERSION=1.3.0.1511 \
    SQ_PHP_VERSION=2.13.0.2896 \
    SQ_PY_VERSION=1.9.0.1726 \
    SQ_CSHARP_VERSION=6.8.0.4273 \
    SQ_XML_VERSION=1.5.0.1225 \
    SQ_WEB_VERSION=2.6.0.896 \
    SQ_LDAP_VERSION=2.2.0.640 \
    SQ_GITHUB_VERSION=1.4.2.1056 \
    SQ_GO_VERSION=1.2.11-rc7 \
    SQ_CF_VERSION=1.5.0 \
    SQ_GITLAB_VERSION=2.1.0 \
    SQ_FINDSEC_VERSION=3.6.0 \
    SQ_PITEST_VERSION=0.9 \
    SQ_DPCHECK_VERSION=1.1.0 \
    SQ_CITY_VERSION=1.0

RUN set -x \
    && rm -rf $SONARQUBE_HOME/lib/bundled-plugins/* \
    && cd  $SONARQUBE_HOME/extensions/plugins/ \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/scm/git/sonar-scm-git-plugin/$SQ_GIT_VERSION/sonar-scm-git-plugin-$SQ_GIT_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/scm/svn/sonar-scm-svn-plugin/$SQ_SVN_VERSION/sonar-scm-svn-plugin-$SQ_SVN_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/java/sonar-java-plugin/$SQ_JAVA_VERSION/sonar-java-plugin-$SQ_JAVA_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/javascript/sonar-javascript-plugin/$SQ_JS_VERSION/sonar-javascript-plugin-$SQ_JS_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/typescript/sonar-typescript-plugin/$SQ_TS_VERSION/sonar-typescript-plugin-$SQ_TS_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/php/sonar-php-plugin/$SQ_PHP_VERSION/sonar-php-plugin-$SQ_PHP_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/python/sonar-python-plugin/$SQ_PY_VERSION/sonar-python-plugin-$SQ_PY_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/dotnet/sonar-csharp-plugin/$SQ_CSHARP_VERSION/sonar-csharp-plugin-$SQ_CSHARP_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/xml/sonar-xml-plugin/$SQ_XML_VERSION/sonar-xml-plugin-$SQ_XML_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/web/sonar-web-plugin/$SQ_WEB_VERSION/sonar-web-plugin-$SQ_WEB_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/ldap/sonar-ldap-plugin/$SQ_LDAP_VERSION/sonar-ldap-plugin-$SQ_LDAP_VERSION.jar \
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/github/sonar-github-plugin/$SQ_GITHUB_VERSION/sonar-github-plugin-$SQ_GITHUB_VERSION.jar \
    && wget --no-verbose https://github.com/uartois/sonar-golang/releases/download/v$SQ_GO_VERSION/sonar-golang-plugin-$SQ_GO_VERSION.jar \
    && wget --no-verbose https://github.com/stepstone-tech/sonar-coldfusion/releases/download/$SQ_CF_VERSION/sonar-coldfusion-plugin-$SQ_CF_VERSION.jar \
    && wget --no-verbose https://github.com/gabrie-allaigre/sonar-gitlab-plugin/releases/download/$SQ_GITLAB_VERSION/sonar-gitlab-plugin-$SQ_GITLAB_VERSION.jar \
    && wget --no-verbose https://github.com/SonarQubeCommunity/sonar-findbugs/releases/download/$SQ_FINDSEC_VERSION/sonar-findbugs-plugin-$SQ_FINDSEC_VERSION.jar \
    && wget --no-verbose https://github.com/VinodAnandan/sonar-pitest/releases/download/$SQ_PITEST_VERSION/sonar-pitest-plugin-$SQ_PITEST_VERSION.jar \
    && wget --no-verbose https://github.com/stevespringett/dependency-check-sonar-plugin/releases/download/$SQ_DPCHECK_VERSION/sonar-dependency-check-plugin-$SQ_DPCHECK_VERSION.jar \
    && wget --no-verbose https://github.com/stefanrinderle/softvis3d/releases/download/softvis3d-$SQ_CITY_VERSION/sonar-softvis3d-plugin-$SQ_CITY_VERSION.jar

WORKDIR $SONARQUBE_HOME
COPY run.sh $SONARQUBE_HOME/bin/
RUN dos2unix $SONARQUBE_HOME/bin/run.sh && chmod +x $SONARQUBE_HOME/bin/run.sh
ENTRYPOINT ["./bin/run.sh"]
