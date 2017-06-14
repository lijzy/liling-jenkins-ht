FROM index.alauda.cn/tutum/centos:6.5

# install jdk1.7.0_51
ADD jdk-8u131-linux-x64.tar.gz /home/app
ENV JAVA_HOME=/home/app/jdk1.8.0_131
ENV PATH=$JAVA_HOME/bin:$PATH
ENV CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

# install tomcat7
ADD apache-tomcat-7.0.55.tar.gz /home/app
ENV CATALINA_HOME=/home/app/apache-tomcat-7.0.55
RUN rm -rf $CATALINA_HOME/webapps/*

#deploy the war
COPY ./HT1610/target/HT1610-0.0.1-SNAPSHOT.war $CATALINA_HOME/webapps/ROOT/ROOT.war
WORKDIR $CATALINA_HOME/webapps/ROOT
RUN jar xvf ROOT.war
RUN rm -rf ROOT.war

#expose 8080
CMD ["/usr/local/src/apache-tomcat-7.0.55/bin/catalina.sh", "run"]

