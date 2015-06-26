# How to build the hadoop docker image (image name is "hadoopmaster")
# $ docker build --force-rm -t hadoopmaster .

# used linux distribution 
FROM ubuntu:14.04
# maintainer / author
MAINTAINER Sebastian Nemak <sebastian.nemak@th-wildau.de> and Philipp Säume <philipp.saeume@th-wildau.de>

# prepare for hadoop
RUN apt-get update && apt-get upgrade -y && apt-get install -y ssh rsync openjdk-7-jdk

ENV JAVA_HOME /usr/java/default
ENV PATH $PATH:$JAVA_HOME/bin

#passphraseless ssh
RUN ssh-keygen -t dsa -P '' -f ~/.ssh/id_dsa 
RUN cat ~/.ssh/id_dsa.pub >> ~/.ssh/authorized_keys

# install hadoop
RUN wget -O /usr/local/hadoop.tar.gz http://ftp.halifax.rwth-aachen.de/apache/hadoop/common/hadoop-2.7.0/hadoop-2.7.0.tar.gz
RUN mkdir /usr/local/hadoop
RUN tar -zxvf /usr/local/hadoop.tar.gz -C /usr/local/hadoop
RUN cp -a /usr/local/hadoop/hadoop-2.7.0/. /usr/local/hadoop/
RUN rm -rf /usr/local/hadoop/hadoop-2.7.0/
RUN rm usr/local/hadoop.tar.gz

# TODO add native libs http://dl.bintray.com/sequenceiq/sequenceiq-bin/hadoop-native-64-2.7.0.tar

ENV HADOOP_HOME /usr/local/hadoop
ENV HADOOP_CONF_DIR /usr/local/hadoop/etc/hadoop
ENV HADOOP_MAPRED_HOME=$HADOOP_HOME
ENV YARN_HOME=$HADOOP_HOME
ENV HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
ENV HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib"

ENV PATH $PATH:$HADOOP_HOME/bin
ENV PATH $PATH:$HADOOP_HOME/sbin

ADD hadoop-env.sh $HADOOP_HOME/etc/hadoop/hadoop-env.sh
ADD hdfs-site.xml $HADOOP_HOME/etc/hadoop/hdfs-site.xml
ADD core-site.xml $HADOOP_HOME/etc/hadoop/core-site.xml
ADD yarn-site.xml $HADOOP_HOME/etc/hadoop/yarn-site.xml
#ADD mapred-site.xml $HADOOP_PREFIX/etc/hadoop/mapred-site.xml

# start ssh
RUN service ssh start
# start hadoop (hdfs, yarn)
RUN $HADOOP_HOME/bin/hdfs namenode -format BIGDATA_VAW_CLUSTER
RUN $HADOOP_HOME/sbin/start-dfs.sh
#RUN $HADOOP_HOME/sbin/start-yarn.sh

# admin ports
EXPOSE 50070 50030 9000 22 80
# hdfs ports
EXPOSE 50010 50020 50070 50075 50090
# mapred ports
#EXPOSE 19888
# yarn ports
#EXPOSE 8030 8031 8032 8033 8040 8042 8088
# other ports
#EXPOSE 49707 2122
