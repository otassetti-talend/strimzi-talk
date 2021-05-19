FROM quay.io/strimzi/kafka:0.23.0-kafka-2.7.0
USER root:root
COPY ./jcustenborder-kafka-connect-twitter-0.3.33.zip /opt/
RUN unzip /opt/jcustenborder-kafka-connect-twitter-0.3.33.zip -d /opt/kafka/plugins
RUN rm /opt/jcustenborder-kafka-connect-twitter-0.3.33.zip
USER 1001
