

# Download kafka-connect-twitter from https://www.confluent.io/hub/jcustenborder/kafka-connect-twitter
```bash
wget https://d1i4a15mxbxib1.cloudfront.net/api/plugins/jcustenborder/kafka-connect-twitter/versions/0.3.33/
```

# write Dockerfile
```bash
FROM quay.io/strimzi/kafka:0.23.0-kafka-2.7.0
USER root:root
COPY ./jcustenborder-kafka-connect-twitter-0.3.33.zip /opt/
RUN unzip /opt/jcustenborder-kafka-connect-twitter-0.3.33.zip -d /opt/kafka/plugins
RUN rm /opt/jcustenborder-kafka-connect-twitter-0.3.33.zip
USER 1001
```

# Build Docker and push it

```bash
docker build . -t otassetti/kafka-connect-twitter:0.3.33 
docker push otassetti/kafka-connect-twitter:0.3.33 
```

# write twitter-credentials.properties
```bash
accessToken=<access_token>
accessTokenSecret=<access_token_secret>
consumerKey=p<consumer_key>
consumerSecret=<consumer_secret>
```

# Put Properties as secret

```bash
kubectl -n kafka create secret generic twitter-credentials \
  --from-file=twitter-credentials.properties
```

# Create Kafka connect cluster

# Create kakfka connector