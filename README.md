# check_brocade_health
nagios check for Brocade fibre channel switches

# Requirements
perl, snmpget, snmpwalk on nagios server

# Configuration

You will need a section in the services.cfg file on the nagios server that looks similar to the following.
```
    define service{
       use                             generic-24x7-service
       host_name                       fcswitch2
       service_description             Brocade health check
       check_command                   check_brocade_health!public
       }
```

You will also need a command definition similar to the following in commands.cfg on the nagios server
```
    # 'check_brocade_health' command definition
    define command{
       command_name    check_brocade_health!public
       command_line    $USER1$/check_brocade_health -H $HOSTADDRESS$ -c $ARG1$
       }
```
