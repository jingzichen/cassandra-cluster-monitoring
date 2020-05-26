# cassandra-cluster-monitoring
```
.
├── cassandra_config
│   ├── cassandra.yaml                    # Cassandra storage config YAML
│   ├── config.yml                        # Cassandra metric exporter
│   └── Dockerfile                        # Dockerfile that adds cassandra configs to the image
├── docker-compose.yaml
├── grafana_config
│   ├── config.ini
│   ├── dashboards
│   │   ├── cassandra-docker.json          # Sample dashboard
│   │   ├── cassandra-node.json
│   │   └── cassandra-service.json
│   ├── Dockerfile                         # Dockerfile that adds grafana configs to the image
│   └── provisioning
│       ├── dashboards                     # holds a list of .yaml files with configuration files that tell Grafana where to look for dashboards to initialize on startup;
│       │   └── all.yml
│       └── datasources                    # holds a list of .yaml files that configure data sources (e.g, Prometheus instance …)
│           └── all.yml
├── prometheus_config
│   └── prometheus.yml                     # Prometheus config
└── README.md
```
> grafana dashboards just sample, you can import it by grafana console