# Zabbix-ArubaVirtualController
## Overview
This repository provides a Zabbix Templates for Aruba Virtual Controller.
SNMP is used to gather values.
It is heavily inspired by https://github.com/dvirsolomon/zabbix
## Setup
Add a SNMP Interface to your host and link the template.
## Discovery rules
Name|Description|Type|Key and additional info
--|--|--|--
Discover AP| Discover APs | Dependent Item | aruba.discover.AP

## Items collected
Name|Description|Type|Key and additional info
--|--|--|--
Virtual Controller Software Version| Software Version of VC| SNMP agent| aiVirtualControllerVersion.0
Virtual Controller Name| Virtual Controller Name| SNMP agent| aiVirtualControllerName.0
Virtual Controller IP| Virtual Controller IP| SNMP agent| aiVirtualControllerIPAddress.0
Get AP data|get AP data for LLD| SNMP agent| aruba.get.APData
AP CPU UTILIZATION - {#APNAME}| CPU Utilization|Dependent Item|aiAPCPUUtilization.[{#APNAME}]
AP IP ADDRESS - {#APNAME}| IP Address|Dependent Item|aiAPIPAddress.[{#APNAME}]
AP MAC ADDRESS - {#APNAME}| Mac Adress|Dependent Item|aiAPMACAddress.[{#APNAME}]
AP MEMORY FREE - {#APNAME}| Memory Free|Dependent Item|aiAPMemoryFree.[{#APNAME}]
AP MEMORY TOTAL - {#APNAME}| Total Memory|Dependent Item|aiAPTotalMemory.[{#APNAME}]
AP MEMORY USED - {#APNAME} | Memory used in Bytes| Calculated Item|iAPUsedMemory.[{#APNAME}]
AP MODEL NAME- {#APNAME}| Model Name|Dependent Item|aiAPModelName.[{#APNAME}]
AP SERIAL NUMBER- {#APNAME}| Serial Number|Dependent Item|aiAPSerialNum.[{#APNAME}]
AP Status - {#APNAME}| AP Status 1 is up 2 is down|Dependent Item|aiAPStatus.[{#APNAME}]
AP Up Time- {#APNAME}| uptime|Dependent Item|aiAPUptime.[{#APNAME}]

## Triggers
Name|Description|Expression|Priority
--|--|--|--
AP is down for more than 5 Minutes- {#APNAME}|Status is higer than 1 for 5 Minutes|max(/Aruba Virtual Controller by SNMP/aiAPStatus.[{#APNAME}],5m)>1|Warning
## References
https://github.com/dvirsolomon/zabbix provided a similar template. I took this one and changed a few things.
