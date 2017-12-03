# coinmarketcap-exporter

A prometheus exporter for <https://coinmarketcap.com/>. Provides Prometheus metrics from the API endpoint of Coinmarketcap, such as US price, Bitcoin price, trading volume, etc.

When running this exporter with both Prometheus and Grafana, [you can create dashboards like](https://grafana.com/dashboards/3890):

![coinmarketcap-single-dashboard](https://github.com/bonovoxly/coinmarketcap-exporter/raw/master/img/coinmarketcap.png "coinmarketcap-exporter with Prometheus and Grafana")

# Developing

- Build the image:

```
docker build -t coinmarketcap-exporter:latest .
```

- Run it while listening on localhost:9100:

```
docker run --rm -p 127.0.0.1:9101:9101 coinmarketcap-exporter:latest
```

- Run it interactively:

```
docker run --rm -it --entrypoint=/bin/bash -p 127.0.0.1:9101:9101 -v ${PWD}:/opt/coinmarketcap-exporter coinmarketcap-exporter:latest
```

- Then to launch:

```
python coinmarketcap.py
```

# Testing the Prometheus Grafana Stack

- In the `prometheus-compose` directory, run:

```
docker-compose up
```

- Go to <http://localhost:3000>.  Log in as `admin/admin`. 
- To import the dashboard, click the "Home" button at the top, then on the right, click "Import Dashboard".
- Enter `3890` in the "Grafana.com Dashboard" field.
- Select the "prometheus" data source.
- Modify the other settings as preferred. Click "Import".
- The new dashboard should be selectable and found at <http://localhost:3000/dashboard/db/coinmarketcap-single>.
- The Prometheus interface can be accessed at <http://localhost:9090>

# Thanks and Links

- Coinmarketcap API link - <https://coinmarketcap.com/api/>
- Prometheus exporters - <https://prometheus.io/docs/instrumenting/writing_exporters/>
- Writing JSON exporters in Python from Robust Perception - <https://www.robustperception.io/writing-json-exporters-in-python/>
- Grafana Dashboard - <https://grafana.com/dashboards/3890>

If you find this useful and want to contribute:

- BTC: `161a2z4A5J5ndVyytBXroN8hGcf6Cc8RA5`
- Ethereum: `0x9de200ba61af4a58c9fced2c1334110087a75f51`
- Litecoin: `LMGHysobMGv9dWUg1s6CDYP78HSasX8gTp`