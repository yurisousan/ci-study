FROM tomcat:8-jre8

ENV RUN_USER            tomcat
ENV RUN_GROUP           tomcat

# Add a tomcat user
RUN groupadd -r ${RUN_GROUP} && useradd -g ${RUN_GROUP} -d ${CATALINA_HOME} -s /bin/bash ${RUN_USER}
RUN chown -R tomcat:tomcat $CATALINA_HOME
RUN echo "export JAVA_OPTS=\"-Dapp.env=staging\"" > /usr/local/tomcat/bin/setenv.sh  

ADD tomcat-users.xml /usr/local/tomcat/conf/
ADD context.xml /usr/local/tomcat/webapps/HelpdeskApp/META-INF/
ADD context.xml /usr/local/tomcat/webapps/host-manager/META-INF/
ADD context.xml /usr/local/tomcat/webapps/manager/META-INF/

CMD ["catalina.sh", "run"]  