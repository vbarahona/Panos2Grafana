# Panos2Grafana
Steps and configurations to create a complete PaloAlto Firewall dashboard in GRAFANA. The dashboard is compatible with one firewall or with a HA cluster 'of 2 firewalls. 

At this time its provided support for models PA5250, PA3020 and PA820, but if you are using a different one, probably some of the sensor graphs (cpu_temp and fan_speed) can be inadequate, but the rest of the panels should be ok.

# Screenshot

<p align="center"><img src="https://github.com/vbarahona/Panos2Grafana/blob/master/screencapture-paloalto-grafana.png" alt="screenshot" width="400"></p>

# Getting Starting

## Prerequisites
The infraestruture needed is:
- PanOS 8.1 or greater firewall (obviously) ;-)
- InfluxDB
- Telegraf
- Grafana

Your PanOS Firewall must be configured to answer SNMP queries.  Your TIG environment (Telegraf/InfluxDB/Grafana) also installed and configured property. I will not cover information about installation and basic configuration.

## SNMP Mibs
HOST-RESOURCES-MIB is required for some panel. The easiest way is install the packages for SNMP MIBs in your distribution.

Ubuntu/Debian
```
apt-get install snmp-mibs-downloader
```
Centos/RedHat
```
yum install net-snmp-libs
```

## Telegraf

Data will be collected by Telegraf SNMP plugin. Just download the appropriate configuration file for your model (5250.conf for PA5250 for example), modify the agents and communities variables, copy the file in /etc/telegraf/telegraf.d/ and reload telegraf
```
sudo systemclt restart telegraf
```
After some seconds, it's a good idea to check if everything is working
```
sudo systemctl status telegraf
```
## Grafana
Finally, import Dashboard number [11321](https://grafana.com/dashboards/11321) from [grafana.com](https://grafana.com/dashboards/11321)
