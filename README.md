# Panos2Grafana
Steps and configurations to create a complete PaloAlto Firewall dashboard in GRAFANA. The dashboard is compatible with a standalone firewall, with one HA cluster of 2 firewalls and with multiple clusters. 

At this time its provided tested support for models PA5250, PA3020 and PA820.

If you are using a different one, probably some sensor graphs (cpu_temp and fan_speed) can be inadequate, but rest of the panels should be ok.

# Screenshot

<p align="center"><img src="https://github.com/vbarahona/Panos2Grafana/blob/master/screencapture-paloalto-grafana.png" alt="screenshot" width="400"></p>

# Getting Starting

## Prerequisites
The infraestruture needed is:
- PanOS 8.1 or greater firewall (obviously) ;-)
- InfluxDB
- Telegraf
- Grafana

Your PanOS Firewall must be configured to answer SNMP queries.  Your TIG environment (Telegraf/InfluxDB/Grafana) also installed and configured property. I will not cover information about installation and basic configuration as a lot of step by step tutorials can be found.

## Telegraf

Data will be collected by Telegraf SNMP plugin. Just download the appropriate configuration file for your model (5250.conf for PA5250 for example).

Modify according with your enviroment:
* agents: ip or hostname firewalls
* community: snmp read comunity of your firewalls 
* cluster: tag_name for your cluster. If you have only one cluster (or one firewall) default value "cluster1" is ok. Otherwise look for "[inputs.snmp.tags]" and modify it.

Copy the config file in /etc/telegraf/telegraf.d/ and reload telegraf
```
sudo systemctl restart telegraf
```
After some seconds, it's a good idea to check if everything is working
```
sudo systemctl status telegraf
```
You can config as many clusters as you needs. Each cluster needs a new config file with . Just creating a copy of the first one if hardware model is the same or repeat the proccess with other config file according to your hardware.

## Grafana
Finally, import Dashboard number [11321](https://grafana.com/dashboards/11321) from [grafana.com](https://grafana.com/dashboards/11321) and the magic will happen. 
