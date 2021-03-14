# MPTCP beNetFlow Demo

Demo deployment for bwNetFlow with MPTCP support as a ready to use docker-compose file.
This docker compose file contains all bwNetFlow components and MPTCP Aggregator.

Deploy MPTCP-Sniffer (https://github.com/SubmergedTree/MPTCP-Sniffer)
and flowexport (https://github.com/cha87de/flowexport/blob/master/Dockerfile)
to server on which to observe traffic.



### Action required: Topics must be created manually.
Open shell of Kafka container and execute:

    /opt/bitnami/kafka/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic mptcp-bwnetflow-aggregator-output

    /opt/bitnami/kafka/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic mptcp-packets

    /opt/bitnami/kafka/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic mptcp-joined

    /opt/bitnami/kafka/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic flows-enriched


Update line 26 and add ip addresses of deployed kafka brokers
    - KAFKA_CFG_ADVERTISED_LISTENERS=CLIENT://kafka:9092,EXTERNAL:TODO EXTERNAL RESOLVABLE IPs


# For detailed explanation see: 
https://github.com/SubmergedTree/Monitoring-Multipath-TCP-in-bwNetFlow/blob/master/MPTCP%20Flow%20Monitoring.pdf