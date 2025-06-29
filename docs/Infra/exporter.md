# Exporter

## SNMP Exporter

公式のsnmp.yamlをとりあえず利用する

```
wget https://raw.githubusercontent.com/prometheus/snmp_exporter/refs/heads/main/snmp.yml
```

`compose.yaml`

```yaml
services:
  snmp-expoter:
    image: prom/snmp-exporter
    container_name: snmp-exporter
    ports:
      - '9116:9116'
    volumes:
      - './snmp.yml:/etc/snmp_exporter/snmp.yml'
```

`prometheus.yml`

```yaml
  - job_name: 'snmp'
    static_configs:
      - targets:
        - 192.168.0.254
    metrics_path: /snmp
    params:
      auth: [public_v2]
      module: [if_mib]
    relabel_configs:
      - source_labels: [__address__]
        target_label: __param_target
      - source_labels: [__param_target]
        target_label: instance
      - target_label: __address__
        replacement: 192.168.0.200:9116
  - job_name: 'snmp_exporter'
    static_configs:
      - targets: ['192.168.0.200:9116']
```

Dashboard

[https://grafana.com/grafana/dashboards/21962-snmp-exporter/](https://grafana.com/grafana/dashboards/21962-snmp-exporter/)
