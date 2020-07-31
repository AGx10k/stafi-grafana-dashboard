# AG stafi-grafana-dashboard

![dashboard](https://github.com/AGx10k/stafi-grafana-dashboard/blob/master/stafi-grafana-dashboard.png?raw=true)

you will need prometheus and grafana installed and connected to each other. this is out of scope of this manual.

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
