FROM openjdk:8-alpine

ENV SONAR_VERSION=7.4 \
    SONARQUBE_HOME=/opt/sonarqube \
    SQ_GIT_VERSION=1.5.0.1176 \
    SQ_SVN_VERSION=1.8.0.1158 \
    SQ_JAVA_VERSION=5.6.0.14668 \
    SQ_JS_VERSION=4.1.0.6281 \
    SQ_TS_VERSION=1.7.0.2913 \
    SQ_PHP_VERSION=2.14.0.3223 \
    SQ_PY_VERSION=1.11.0.2212 \
    SQ_CSHARP_VERSION=7.3.0.5654 \
    SQ_XML_VERSION=1.6.0.1499 \
    SQ_WEB_VERSION=2.7.0.1155 \
    SQ_LDAP_VERSION=2.2.0.671 \
    SQ_GITHUB_VERSION=1.5.0.1280 \
    SQ_GO_VERSION=1.2.0.1628 \
    SQ_GITLAB_VERSION=3.0.1 \
    SQ_FINDSEC_VERSION=3.7.0 \
    SQ_PITEST_VERSION=0.9.1 \
    SQ_DPCHECK_VERSION=1.1.0 \
    SQ_OIDC_VERSION=1.0.4 \
    SQ_CITY_VERSION=1.0.1 \
    # Database configuration
    # Defaults to using H2
    SONARQUBE_JDBC_USERNAME=sonar \
    SONARQUBE_JDBC_PASSWORD=sonar \
    SONARQUBE_JDBC_URL=

# Http port
EXPOSE 9000

RUN addgroup -S sonarqube && adduser -S -G sonarqube sonarqube

RUN set -x \
    && apk add --no-cache gnupg unzip \
    && apk add --no-cache libressl wget \
    && apk add --no-cache su-exec \
    && apk add --no-cache bash \
    && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys F1182E81C792928921DBCAB4CFCA4A29D26468DE \
    && mkdir /opt \
    && cd /opt \
    && wget -O sonarqube.zip --no-verbose https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-$SONAR_VERSION.zip \
    && wget -O sonarqube.zip.asc --no-verbose https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-$SONAR_VERSION.zip.asc \
    && gpg --batch --verify sonarqube.zip.asc sonarqube.zip \
    && unzip sonarqube.zip \
    && mv sonarqube-$SONAR_VERSION sonarqube \
    && chown -R sonarqube:sonarqube sonarqube \
    && rm sonarqube.zip* \
    && rm -rf $SONARQUBE_HOME/extensions/plugins/* \
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
    && wget --no-verbose https://repox.sonarsource.com/sonarsource-public-builds/org/sonarsource/go/sonar-go-plugin/$SQ_GO_VERSION/sonar-go-plugin-$SQ_GO_VERSION.jar \
    && wget --no-verbose https://github.com/gabrie-allaigre/sonar-gitlab-plugin/releases/download/$SQ_GITLAB_VERSION/sonar-gitlab-plugin-$SQ_GITLAB_VERSION.jar \
    && wget --no-verbose https://github.com/SonarQubeCommunity/sonar-findbugs/releases/download/$SQ_FINDSEC_VERSION/sonar-findbugs-plugin-$SQ_FINDSEC_VERSION.jar \
    && wget --no-verbose https://github.com/VinodAnandan/sonar-pitest/releases/download/v$SQ_PITEST_VERSION/sonar-pitest-plugin-$SQ_PITEST_VERSION.jar \
    && wget --no-verbose https://github.com/stevespringett/dependency-check-sonar-plugin/releases/download/$SQ_DPCHECK_VERSION/sonar-dependency-check-plugin-$SQ_DPCHECK_VERSION.jar \
    && wget --no-verbose https://github.com/vaulttec/sonar-auth-oidc/releases/download/v$SQ_OIDC_VERSION/sonar-auth-oidc-plugin-$SQ_OIDC_VERSION.jar \
    && wget --no-verbose https://github.com/stefanrinderle/softvis3d/releases/download/softvis3d-$SQ_CITY_VERSION/sonar-softvis3d-plugin-$SQ_CITY_VERSION.jar \
    && rm -rf $SONARQUBE_HOME/bin/*

VOLUME "$SONARQUBE_HOME/data"

WORKDIR $SONARQUBE_HOME
COPY run.sh $SONARQUBE_HOME/bin/
RUN dos2unix $SONARQUBE_HOME/bin/run.sh && chmod +x $SONARQUBE_HOME/bin/run.sh

RUN chmod -R 777 $SONARQUBE_HOME
RUN chown -R sonarqube:sonarqube $SONARQUBE_HOME
USER sonarqube

ENTRYPOINT ["./bin/run.sh"]
