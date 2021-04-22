# Prometheus

## **Architecture**

This diagram illustrates the architecture of Prometheus and some of its ecosystem components:

![architecture](/README/image/architecture.png)

### **Components**

The Prometheus ecosystem consists of multiple components, many of which are optional:

- 一個已時間時序為主的多維度資料模型，以`Metric`資料名稱與`key/values`來呈現。
- 透過`PromQL`查詢語言，取得時序資料。
- 不需依賴分佈式存儲，單節點儲存即可。
- 透過`HTTP`協定`pull`模式收集時序資料。
- 透過`PushGateway`角色，支持推送時序資料。
- 通過 "ServiceDiscovery" 或 "**靜態配置**" 去確認監控`Targets`。
- 支援多種圖形和儀表板。

For notification mechanisms not natively supported by the Alertmanager, the webhook receiver allows for integration.

![example.png](/README/image/monitor.png)

## Installation

- [https://www.prometheus.io/docs/introduction/first_steps/](https://www.prometheus.io/docs/prometheus/latest/getting_started/)
- reference: docker-compose.yaml

```bash
$ docker-compose up -d
## 進入prometheus container
$ docker exec -it prometheus sh
## 查看可用的配置
$ prometheus -h
```

[Configuration file](https://www.prometheus.io/docs/prometheus/latest/configuration/configuration/)

- reference: prometheus.yml

Querying

- reference:  rules/*yml

How Prometheus Monitoring works | Prometheus Architecture explained

- reference: [https://www.youtube.com/watch?v=h4Sl21AKiDg&feature=share](https://www.youtube.com/watch?v=h4Sl21AKiDg&feature=share)

## GRAFANA SUPPORT FOR PROMETHEUS

![Untitled.png](/README/image/grafana_configuring_datasource.png)

- [https://www.prometheus.io/docs/visualization/grafana/](https://www.prometheus.io/docs/visualization/grafana/)
- [https://ops.tips/blog/initialize-grafana-with-preconfigured-dashboards/](https://ops.tips/blog/initialize-grafana-with-preconfigured-dashboards/)

## Alertmanager

The Alertmanager handles alerts sent by client applications such as the Prometheus server. It takes care of deduplicating, grouping, and routing them to the correct receiver integration such as email, PagerDuty, or OpsGenie.

**ALERTING OVERVIEW**

The main steps to setting up alerting and notifications are:

- Setup and [configure](https://www.prometheus.io/docs/alerting/latest/configuration/) the Alertmanager
- [Configure Prometheus](https://www.prometheus.io/docs/prometheus/latest/configuration/configuration/#alertmanager_config) to talk to the Alertmanager
- Create [alerting rules](https://www.prometheus.io/docs/prometheus/latest/configuration/alerting_rules/) in Prometheus

### [configuration](https://prometheus.io/docs/alerting/latest/configuration/)

- reference: alertmanager.yml

```bash
## 進入prometheus container
$ docker exec -it alertmanager sh
## 查看可用的配置
$ alertmanager -h
```

[rules](https://www.prometheus.io/docs/alerting/latest/notification_examples/)

- reference:  ./rules/*.yml

## Exporter

- [EXPORTERS AND INTEGRATIONS](https://prometheus.io/docs/instrumenting/exporters/)

## node-exporter

- reference: [https://www.prometheus.io/docs/guides/node-exporter/](https://www.prometheus.io/docs/guides/node-exporter/)

The Prometheus Node Exporter exposes a wide variety of hardware- and kernel-related metrics.

```jsx
curl http://localhost:9100/metrics
```

## cadvisor

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ac2bfd08-9687-4610-b670-fc6392f8480a/Untitled.png](/README/image/20170909222324259.png)

- reference:
- [https://www.prometheus.io/docs/guides/cadvisor/](https://www.prometheus.io/docs/guides/cadvisor/)
- [https://blog.csdn.net/huwh_/article/details/77918507](https://blog.csdn.net/huwh_/article/details/77918507)

## chatbot

chatbot 會根據product 將告警分送給正確地接收者

- 依據label namespace區分

![namespace.png](/README/image/image.png)

```docker
## check monitor network
$ docker network ls
## connect chatbot container with monitor network
$ docker network connect NETWORK CONTAINER
```