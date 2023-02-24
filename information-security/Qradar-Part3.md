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
