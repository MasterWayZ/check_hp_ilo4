# check_hp_ilo4
nagios check for HP ILO4 service processor health

# Requirements
perl, snmp

# Setup

You will need a section similar to the following in the commands.cfg file on the nagios server:
```
# 'check_hp_ilo4' command definition
define command{
   command_name    check_hp_ilo4
   command_line    $USER1$/check_hp_ilo4 -H $HOSTADDRESS$ -C $ARG1$ 
   }
```

You will need a section similar to the following in the services.cfg file on the nagios server:
```
# Check HP ILO4
# Requires SNMP enabled on ILO
# syntax is check_hp_ilo4!optional_snmp_community
define service {
   use                             generic-service
   hostgroup_name                  all_hp_ilo4
   service_description             HP ILO4
   check_command                   check_hp_ilo4!optional_snmp_community
   }
```

# Output
You will see output similar to the following:
```
HP ILO4 OK - Ambient_Temperature:21C Power_Redundancy:ok Fan_Status:8/8ok Physical_Disks:3/3ok Logical_disks:1/1ok Processors:2/2ok Memory_Modules:24/24ok 
