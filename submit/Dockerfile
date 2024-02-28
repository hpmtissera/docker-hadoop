FROM bde2020/hadoop-base:2.0.0-hadoop3.2.1-java8

MAINTAINER Ivan Ermilov <ivan.s.ermilov@gmail.com>

RUN java -version
COPY WordCount.java /opt/hadoop/applications/WordCount.java
COPY WordCount.jar /opt/hadoop/applications/WordCount.jar
WORKDIR /opt/hadoop/applications/
ENV HADOOP_CLASSPATH=${JAVA_HOME}/lib/tools.jar
RUN /opt/hadoop-3.2.1/bin/hadoop com.sun.tools.javac.Main WordCount.java
RUN jar cf wc.jar WordCount*.class

ENV JAR_FILEPATH="/opt/hadoop/applications/wc.jar"
ENV CLASS_TO_RUN="WordCount"
ENV PARAMS="/input /output"

ADD run.sh /run.sh
RUN chmod a+x /run.sh

CMD ["/run.sh"]
