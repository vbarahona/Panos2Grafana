# Panos2Grafana
Steps and configurations to create a complete PanOS Firewall dashboard in GRAFANA.

This Dashboard is based in a PA5250 so if you are using a different model probably some of the sensors graphs can be inadequate, but rest of the graphs should be ok.

# Getting Starting

## Prerequisites
The infraestruture needed is:
- PanOS 8.1 or greater firewall (obiously) ;-)
- InfluxDB
- Telegraf
- Grafana

I am asuming that your PanOS Firewall is configured to anwer SNMP queries and you have a InfluxDB, Telegraf and Grafana instaled and configured propertly . I will not cover information about instalation and basic configuration.

## Telegraf
First, download [PAN-COMMON-MIB.my](https://github.com/vbarahona/Panos2Grafana/raw/master/PAN-COMMON-MIB.my)  and copy it in /etc/telegraf/telegraf.d/.snmp/mibs/PAN-COMMON-MIB.my

We will colect data using Telegraf with the SNMP plugin. Just download [panos_snmp.conf](https://github.com/vbarahona/Panos2Grafana/raw/master/panos_snmp.conf), modify the agents and comunities variables, copy the file in /etc/telegraf/telegraf.d/ and reload telegraf
```
sudo service telegraf reload
```
After some seconds, its a good idea to check if everything is working
```
sudo service telegraf status
```
## Grafana
Finally you can import the Dashboard number xxxx from [grafana.com](https://grafana.com/dashboards/xxxx)
