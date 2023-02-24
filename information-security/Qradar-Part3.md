# Troubleshooting Checklist  
![image](https://user-images.githubusercontent.com/63524369/221185355-012f59c8-59f9-4300-ab1d-aa55e154a187.png)


1. `ssh -vv` 
2. `/opt/qradar/support/deployment_info.sh -OH` 
3. all hosts: `/opt/qradar/support/all_servers.sh  -Ck "/opt/qradar/bin/myver -tf”`
4. `systemctl status hostcontext`
5. `df -Th` 
6. `ls /opt/qradar/conf/hostcontext.NODOWNLOAD`
7. `/opt/qradar/support/validate_deployment.sh`   `md5sum `locate host.token`` 
8. bandwith: `grep "Replication download" /var/log/qradar.log | tail`
---
## ▪ Check logs:

`var/log/setup/<Qradar Buidup id>/patches.log`

 `var/log/qradar.error`

 `/store/backup/marathon`

## ▪ Pretest:

>> `/opt/qradar/support/validate_deployment.sh`

## ▪ Check version:

>> `/opt/qradar/support/all_servers.sh -Ck "/opt/qradar/bin/myver -tf"`

## ▪ Check for space:

>> `df -h /storetmp /var/log | tee diskchecks.txt`

## ▪ Updates:

>> `/opt/qradar/support/apar/aqlValidator`

## ▪ WinCollect:

>> `yum list all | grep -i AGENT-WINCOLLECT`

>> `psql -U qradar -c "select * from ale_component_type"`

## ▪ EPS Commands:

>> `tail -f /var/log/qradar.log | grep -i 'incoming raw'/opt/qradar/support/jmx.sh 7782 | grep Queries`

>> `/opt/qradar/support/jmx.sh 7782 | grep Queries`

>> `watch -n1 '/opt/qradar/support/jmx.sh -p 7787 -b"com.q1labs.sem:application=ecs-ec-ingress.ecs-ec-ingress,type=sources,name=Source Monitor"'`

## ▪ Export CMD:

```bash
echo "COPY (select fg.name, sd.id, sd.hostname, sd.devicename,st.devicetypename, sd.devicedescription,(to_timestamp(sd.timestamp_last_seen/1000)), sd.deviceenabled from sensordevice sd left join sensordevicetype st on sd.devicetypeid=st.id leftjoin fgroup_link fl on trim(both ' ' from to_char(sd.id, '99999'))=fl.item_id
left join fgroup fg on fl.fgroup_id=fg.id where sd.deviceenabled='t' order by fg.name) TO STDOUT with CSV HEADER" | psql -U qradar -o /root/SIEMLogsources.csv qradar
```

## ▪ Extract Logs:

>> `/opt/qradar/support/get_logs.sh -S`
---
# APPS Health Check : [Link](https://www.ibm.com/support/pages/how-check-if-qradar-application-app-running)
```bash 
psql -U qradar -c "select i.id,i.name,i.status,i.task_status,i.managed_host_id, m.hostname from installed_application_instance as i left join managedhost as m on m.id = i.managed_host_id;"

```
---
# Network [Link](https://www.ibm.com/support/pages/qradar-networking-troubleshooting-interfaces-and-connections-using-command-line)
---
# Deployment 
Check `/opt/qradar/conf/deployment.xml`


