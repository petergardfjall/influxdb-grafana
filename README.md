# docker-grafana

A script for running an InfluxDB side-by-side with Grafana in Docker containers.

Note: requires `docker` and `docker-compose` to be installed on your system.

The script takes care of creating a database in InfluxDB to which metrics
can be reported, and also sets up influxdb as the default data source in
Grafana.

The script can be tuned with the following environment variables:

- `INFLUXDB_API_PORT`: Host port to publish influxdb api port on. 
  Default: `8086`.
- `INFLUXDB_UI_PORT`: Host port to publish influxdb ui port on. 
  Default: `8083`.
- `INFLUXDB_DATABASE`: A metrics database to create in influxdb. 
  Default: `metricsdb`.
- `GRAFANA_PORT`: Host port to publish grafana on Default: `3000`.
- `GRAFANA_PASSWORD`: Grafana admin user password. Default: `secret`.


## Start containers
Start InfluxDB and Grafan via:

    ./stack up

Data will be written to directories `grafana-data` and `influxdb-data` on the
host (in the `stack` script directory) to make data survive container restarts.


## Stop and remove containers

Stop and remove containers via:

    ./stack down
	
*Note: the data directories are left untouched, so data will persist to the next
`./stack up`.*
	
	
## Clear database contents
Clear the data directories with:

    ./stack clean
