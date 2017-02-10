# To this:
FROM krallin/ubuntu-tini:trusty

####installing [software-properties-common] so that we can use [apt-add-repository] to add the repository [ppa:webupd8team/java] form which we install Java8
RUN apt-get update -y
RUN apt-get install software-properties-common -y
RUN apt-add-repository ppa:webupd8team/java -y
RUN apt-get update -y

####automatically agreeing on oracle license agreement that normally pops up while installing java8
RUN echo debconf shared/accepted-oracle-license-v1-1 select true | sudo debconf-set-selections
RUN echo debconf shared/accepted-oracle-license-v1-1 seen true | sudo debconf-set-selections

####installing java
RUN apt-get install -y oracle-java8-installer

RUN wget http://d3kbcqa49mib13.cloudfront.net/spark-1.6.2-bin-hadoop2.6.tgz
RUN tar -xzf spark-1.6.2-bin-hadoop2.6.tgz

RUN mv spark-1.6.2-bin-hadoop2.6 /opt/spark

CMD ["/opt/spark/sbin/start-slave.sh"]
