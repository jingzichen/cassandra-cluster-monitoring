FROM cassandra:3.11.3

COPY cassandra.yaml ${CASSANDRA_CONFIG}/cassandra.yaml

RUN mkdir /prometheus
ADD "https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/0.12.0/jmx_prometheus_javaagent-0.12.0.jar" /prometheus
RUN chmod 644 /prometheus/jmx_prometheus_javaagent-0.12.0.jar
ADD config.yml /prometheus/cassandra.yml

# ADD  JVM_OPTS "$JVM_OPTS -javaagent:/prometheus/jmx_prometheus_javaagent-0.12.0.jar=6121:/prometheus/cassandra.yml"

RUN echo 'JVM_OPTS="$JVM_OPTS -javaagent:/prometheus/jmx_prometheus_javaagent-0.12.0.jar=6121:/prometheus/cassandra.yml"' >> /etc/cassandra/cassandra-env.sh

EXPOSE 6121

