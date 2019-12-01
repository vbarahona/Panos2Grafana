# Panos2Grafana
Steps and configurations to create a complete PaloAlto Firewall dashboard in GRAFANA.

This Dashboard is based in a PA5250 so if you are using a different model probably some of the sensor graphs (cpu_temp and fan_speed) can be inadequate, but the rest of the graphs should be ok.

# Getting Starting

## Prerequisites
The infraestruture needed is:
- PanOS 8.1 or greater firewall (obviously) ;-)
- InfluxDB
- Telegraf
- Grafana

I am assuming that your PanOS Firewall is configured to answer SNMP queries and you have a InfluxDB, Telegraf and Grafana installed and configured property . I will not cover information about installation and basic configuration.

## Telegraf
First, download [PAN-COMMON-MIB.my](https://github.com/vbarahona/Panos2Grafana/raw/master/PAN-COMMON-MIB.my)  and copy it in /etc/telegraf/telegraf.d/.snmp/mibs/PAN-COMMON-MIB.my

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
