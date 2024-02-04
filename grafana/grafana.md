sudo apt-get install -y apt-transport-https software-properties-common

wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -


echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list


sudo apt-get update

sudo apt-get -y install grafana


sudo systemctl enable grafana-server


sudo systemctl start grafana-server


sudo systemctl status grafana-server


http://<ip>:3000
username admin
password admin


and add data source and import dashbord. 

![image](https://github.com/imanabr77/CI-CD-with-Monitoring-DevSecops/assets/92488673/1939d1fe-f095-4d83-99ca-1e27108df4ff)



Install the Prometheus Plugin and Integrate it with the Prometheus server : 

Let's Monitor JENKINS SYSTEM

Need Jenkins up and running machine

Goto Manage Jenkins --> Plugins --> Available Plugins

Search for Prometheus and install it

sudo vim /etc/prometheus/prometheus.yml


  - job_name: 'jenkins'
    metrics_path: '/prometheus'
    static_configs:
      - targets: ['<jenkins-ip>:8080']


promtool check config /etc/prometheus/prometheus.yml
curl -X POST http://localhost:9090/-/reload

http://<ip>:9090/targets


Click On Dashboard --> + symbol --> Import Dashboard

Use Id 9964 and click on load


