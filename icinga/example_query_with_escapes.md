## example_query_with_escapes

### /etc/nagios/nrpe.d/check_prometheus.cfg

```
command[check_prometheus]=/usr/lib64/nagios/plugins/check_prometheus mode $ARG1$ --address 'http://localhost:9090/prometheus' '$ARG2$'
command[check_prometheus_ping]=/usr/lib64/nagios/plugins/check_prometheus mode ping --address 'http://localhost:9090/prometheus'
command[check_prometheus_query]=/usr/lib64/nagios/plugins/check_prometheus mode query --address 'http://localhost:9090/prometheus' -q $ARG1$
command[check_prometheus_targets_health]=/usr/lib64/nagios/plugins/check_prometheus mode targets_health --address 'http://localhost:9090/prometheus' $ARG1$
```

### icinga_lconf_command
Command name:
* `check_prometheus_query`
Commandline:
* `$USER1$/check_nrpe$_HOSTNRPE_BUFFER$ $ARG3$ -u -t 30 -H prometheus-host -c check_prometheus_query -a $ARG1$`

### icinga_lconf_service_command

`check_prometheus_query!"\\(wmi_mssql_databases_log_files_size_bytes{hostname=\\'database-1\\'}/1024/1024\\) -w 70000 -c 92160 --search '.*database=\\"(.*?)\\".*hostname=\\"(.*?)\\".*' --replace '\\$$2\\\\\\$$1' -a 'MSSQL Database log file size in MB'"`
