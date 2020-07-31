# AG stafi-grafana-dashboard

![dashboard](https://github.com/AGx10k/stafi-grafana-dashboard/blob/master/stafi-grafana-dashboard.png?raw=true)

You will need [Prometheus](https://github.com/prometheus/prometheus#install) and [Grafana](https://grafana.com/docs/grafana/latest/installation/) installed and connected to each other. This is out of scope of this manual. For example [this manual](https://www.scaleway.com/en/docs/configure-prometheus-monitoring-with-grafana/) looks pretty useful

## Installation
1. start stafi with prometheus metrics enabled: `stafi --prometheus-external`
2. add job named `stafi` to `prometheus.yml`:
```
  - job_name: stafi
    static_configs:
      - targets: ['stafi-validator.host.com:9615', 'stafi-sentry.host2.com:9615']

```

3. import `dashboard.json` to new grafana dashboard
4. add notification channels to `block sync rate` and `Number of network gossip peers` panels
5. if prometheus job is named not `stafi` (`stafi-sitara` for example) then go to Settings\Variables and change `$job`
6. in case prometheus job is not `stafi` need to change it in 2 alerts manually - `block sync rate`, `Number of network gossip peers`:

![dashboard](https://github.com/AGx10k/stafi-grafana-dashboard/blob/master/stafi-grafana-dashboard-jobname-change.png?raw=true)

7. for monitoring and alerting system overall parameters i recomment using [Prometheus Node Exporter](https://github.com/prometheus/node_exporter) and just creating alerts for mem <20%, disk < 20%, cpu > 80%
8. for monitoring new version i recommend subscribing to [stafi-node](https://github.com/stafiprotocol/stafi-node) github notifications:
![subscribe stafi](https://github.com/AGx10k/stafi-grafana-dashboard/blob/master/stafi-subscribe-notifications.png?raw=true)
9. also i recommend to try my script to monitor and restart when sync is stalled: https://github.com/AGx10k/substrate-restart-stalled-blocks
