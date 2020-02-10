# Panos2Grafana
Steps and configurations to create a complete PaloAlto Firewall dashboard in GRAFANA. The dashboard is compatible with one firewall or with a HA cluster of 2 firewalls. 

This Dashboard is based in a model PA5250 so if you are using a different one, probably some of the sensor graphs (cpu_temp and fan_speed) can be inadequate, but the rest of the graphs should be ok.

# Screenshot

<p align="center"><img src="https://github.com/vbarahona/Panos2Grafana/blob/master/screencapture-paloalto-grafana.png" alt="screenshot" width="400"></p>

# Getting Starting

## Prerequisites
The infraestruture needed is:
- PanOS 8.1 or greater firewall (obviously) ;-)
- InfluxDB
- Telegraf
- Grafana

I am assuming that your PanOS Firewall is configured to answer SNMP queries and you have a InfluxDB, Telegraf and Grafana installed and configured property . I will not cover information about installation and basic configuration.

## Telegraf
First, download [pan-81-snmp-mib-modules.zip](https://github.com/vbarahona/Panos2Grafana/blob/master/pan-81-snmp-mib-modules.zip?raw=true) and uncompress all the files in /etc/telegraf/telegraf.d/.snmp/mibs/

We will collect data using Telegraf with the SNMP plugin. Just download [panos_snmp.conf](https://github.com/vbarahona/Panos2Grafana/raw/master/panos_snmp.conf), modifies the agents and communities variables, copy the file in /etc/telegraf/telegraf.d/ and reload telegraf
```
sudo service telegraf reload
```
After some seconds, it's a good idea to check if everything is working
```
sudo service telegraf status
```
## Grafana
Finally, you can import the Dashboard number [11321](https://grafana.com/dashboards/11321) from [grafana.com](https://grafana.com/dashboards/11321)
