FROM index.alauda.cn/tutum/centos:6.5

# install jdk1.7
ADD jdk-7u51-linux-x64.tar.gz /usr/local/src
ENV JAVA_HOME=/usr/local/src/jdk1.7.0_51
ENV PATH=$JAVA_HOME/bin:$PATH
ENV CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

# install tomcat7
ADD apache-tomcat-7.0.55.tar.gz /usr/local/src
ENV CATALINA_HOME=/usr/local/src/apache-tomcat-7.0.55

#RUN rm -rf $CATALINA_HOME/webapps/*

# deploy the war
COPY jt-manage-web.war $CATALINA_HOME/webapps/ROOT/ROOT.war
WORKDIR $CATALINA_HOME/webapps/ROOT
RUN jar xvf ROOT.war
RUN rm -rf ROOT.war

expose 8080 
CMD ["/usr/local/src/apache-tomcat-7.0.55/bin/catalina.sh", "run"]
