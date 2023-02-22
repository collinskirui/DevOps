## Open Source Monitoring Project using Grafana and Prometheus Server

<p align="center">
 <img src="images/progfraflogo.png?raw=true" alt="Logo" width="27%" height="27%" />
</p>

## Flow Diagaram

<p align="center">
 <img src="images/diagram.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>

## Prometheus

- Prometheus is an open source Linux Server Moniring tool maily used for metrics monitoring, event
monitoring, alert management etc
- Prometheus has changed the way of monitoring systems and that is why it has become the Top-Level
project of Cloud Native Computing Foundation (CNCF)
- Prometheus uses a powerful query langage i.e "PromQl"
- Prometheus use multiple modes used for graphing and dashboard support

### Prometheus Configuration file and Components
1. prometheus.yml - it is the configuration file for prometheus when we can do all changes regarding
configuration of Prometheus
2. Promtool- it is command-line utility tool used to verify the configuration of Prometheus
3. PromQL- Prometheus uses its own query language i.e PromQL 


## Grafana
- Grafana is a free and open source visualization tool mostly used with Prometheus to which monitor metrics
- Grafana provides various dashboards, charts, graphs, alerts for the particular data source
- Grafana allows us to query, visualize, explore metrics and set alerts for the data source which can be a system, server, nodes, cluster etc
- We can also create our own dynamic dashboard for visualization and monitoring
_Main Advantage: Allows one to save their dashboards and share with their team members_

## Container Advisor
- cAdvisor  provides container users an understanding of the resource usage and performance characteristics of their running containers. It is a running daemon that collects, aggregates, processes, and exports information about running containers. Specifically, for each container it keeps resource isolation parameters, historical resource usage, histograms of complete historical resource usage and network statistics. This data is exported by container and machine-wide.

## Node Exporter
- Node exporter is one of the Prometheus exporters which is used to expose server or systems OS metrics
- With the help of Node exporter we can expose various resources of the system like RAM, CPU Utilization, Memory Utilization, disk space
- Node exporter runs as a system service which gathers the metrics of your system and that gathered metrics is displayed with the help of Grafana visualization tool


### Prerequisites and Step by Step Demonstration
1.Install Docker in your enviroment
    _sudo apt install docker.io_

2.Install Docker compose in your environment (will help in spinning up our containers).
    _sudo apt-get install docker-compose -y_

3. Run the command below to create our directory structure
```
mkdir -p promgrafnode/prometheus && \
mkdir -p promgrafnode/grafana/provisioning && \
touch promgrafnode/docker-compose.yml && \
touch promgrafnode/prometheus/prometheus.yml
```

4. Copy repo's docker-compose.yml and edit the user id to match with your own id if it is different
```To check your user id run (id -u) in your machine the change _user_ , _PUID_ and _PGID_.```

5. Run _docker-compose up -d_

6. Run _docker-compose ps_

7. Configure Prometheus -> prometheus.yml file that you we will pull metrics from and feed the Grafana
  _docker stop prometheus_
  _docker stop prometheus_

8. Login to the Grafana-> Point your Grafana to the Prometheus Data Source-> Populate your address with the one of Prometheus installed.

9. Import Community Dashboards either upload json file of paste the Clipboard ID from community sites


  ## Community Dashboards Used For This Demo


| File name                         | ID          | Screenshot |
|:--------------------------------- |:------------|:----------:|
| Node Exporter Full with Node Name |10242        | [LINK](https://grafana.com/api/dashboards/10242/images/6451/image) |
| Windows Exporter Node             | 14510       | [LINK](https://grafana.com/api/dashboards/14510/images/10501/image) |



## Contributing

Feel free to contribute to this project:

- Give a GitHub ⭐ if you like it
- Create an [Issue](https://github.com/collinskirui/DevOps/issues) to make a feature request, report a bug or share an idea.
- Create a [Pull Request](https://github.com/collinskirui/DevOps/pulls) if you want to share code or anything useful to this project.


