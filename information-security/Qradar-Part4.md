- **Deployment**
    1. Normal **Deploy -> change of something small : log source** 
    2. Full **Deploy -> change of something big : Add & Remove hosts** 
    3. Full Deploy  will restart the the services and rebuild the config 
    4. `/opt/qradar/bin/local_transformation.sh -l -f`
    5. Manual Deployment from CLI ->  `/opt/qradar/upgrade/util/setup/upgrades/do_deploy`
