[![Build Status](https://travis-ci.org/AndriyKalashnykov/tomcat-root-war.svg?branch=master)](https://travis-ci.org/AndriyKalashnykov/tomcat-root-war)
[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FAndriyKalashnykov%2Ftomcat-root-war&count_bg=%2333CD56&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)
# Java Web Application example

ROOT.war replaces Tomcat's default ROOT application - $TOMCAT_HOME/webapps/ROOT

### Test with Jetty web server

```shell
git clone git@github.com:AndriyKalashnykov/tomcat-root-war.git
cd tomcat-root-war
mvn clean package jetty:run

open http://localhost:8080/index.html
```

Access http://localhost:8080/index.html

### Create WAR file

```shell
git clone git@github.com:AndriyKalashnykov/tomcat-root-war.git
cd tomcat-root-war
mvn clean install
```

### List content of generated WAR file

```shell
jar tf ./target/ROOT.war
```
### Replace TOMCAT ROOT application

Edit `$TOMCAT_HOME/conf/server.xml`: `autoDeploy` and `deployOnStartUp` needs to be set to `false`

```xml
<Host name="localhost"  appBase="webapps" unpackWARs="true" autoDeploy="false" deployOnStartUp="false">
```

Remove default ROOT folder and copy ROOT.war
```shell
rm -rf $TOMCAT_HOME/webapps/ROOT
rm -f $TOMCAT_HOME/webapps/ROOT.war
cp ./target/ROOT.war $TOMCAT_HOME/webapps/ROOT.war
```

## Links
[Docker image of this application deployed onto Customized Bitnami Tomcat 9](https://hub.docker.com/r/andriykalashnykov/bitnami-tomcat9-jdk18-root-war)

### Java Web Application UI

Default welcome page -  [http://localhost:8080/](http://localhost:8080/)
![index.html](images/http-8080-root.png)

JSP - [http://localhost:8080/index.jsp](http://localhost:8080/index.jsp)
![infoservlet](images/http-8080-index-jsp.png)

Servlet - [http://localhost:8080/infoservlet](http://localhost:8080/infoservlet)
![infoservlet](images/http-8080-infoservlet.png)

HTML - [http://localhost:8080/index.html](http://localhost:8080/index.html)
![infoservlet](images/http-8080-index-html.png)

