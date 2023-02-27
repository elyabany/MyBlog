ديه Tools مبنيه في Qradar هتسعدك في حل مشاكل 

Website: https://www.ibm.com/community/qradar/home/tools/
- Get Logs:    `/opt/qradar/support/get_logs.sh -h`
- Get Logs:     `/opt/qradar/bin/scrub.pl /var/log/qradar.error /tmp/scrubbedqradar.log`
- Disk space & partitions:      `/opt/qradar/support/partitionDiagnostic -n`
- Disk space & partitions:     `df -Th`
- Health:     `/opt/qradar/support/cliniq -h`
- Services:     `/opt/qradar/upgrade/util/setup/upgrades/wait_for_start.sh`
- Event Collector:     `/opt/qradar/support/validate_ecs_services.sh`
- Check Version:     `/opt/qradar/bin/myver -v`
- Deployment Info:     `/opt/qradar/support/deployment_info.sh -OS`
- Check on all servers:    `/opt/qradar/support/all_servers.sh -h`
- Network:     `tcpdump -nnAs0 -i eth0 port 514 -c 4`
- Network:    `tcpdump -s 0 -A host 192.168.1.1 and udp port 514`
- Inspector:    ` /opt/qradar/support/defect-inspector`
- Replication:    `/opt/qradar/support/replicationVerify.pl`
- Recon:               `/opt/qradar/support/recon ps`
- Performance:           /`opt/qradar/support/findExpensiveCustomRules.sh -d /root`
- Performance:          ` /opt/qradar/support/threadTop.sh`
- Performance:          `/opt/qradar/support/collectGvStats.sh -s`
- Services:          `journalctl -u hostcontext`
