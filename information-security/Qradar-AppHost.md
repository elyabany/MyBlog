# Make Qradar Run apps in APP Host  
![image](https://user-images.githubusercontent.com/63524369/228890264-72e60d43-a306-4a31-8d82-69c0bb108ecb.png)
![image](https://user-images.githubusercontent.com/63524369/228890294-3b09c834-43ad-4208-aeb9-4546291ff42f.png)

## How to downloads apps 
1. Got to App exchange [LINK](https://exchange.xforce.ibmcloud.com/hub)
2. Choose what app you like 
3. On the QRadar Console, click `AdminExtensions Management`
4. In the `Extension Management` window, click `Add` and select the app archive that you want to upload to the console.
5. Select the Install immediately checkbox.

## Applications Troubleshooting
### If you got `Another preview/install/uninstall task is currently in progress, please try again later`
1. restart hostcontext -> `systemctl restart hostcontext`
2. check the app for database `psql -U qradar -c "select id, name, version, hub_id, file_location, content_status from content_package;"`
---
