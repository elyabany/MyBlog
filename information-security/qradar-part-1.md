# Qradar - Installation 

1. install RedHat Linux  

```jsx
RedHat 7.6 ----> QRadar 7.3.* 
RedHat 7.7 ----> QRadar 7.4.* 
RefHat 7.9 ----> QRadar 7.5 
```

1.  Setup the Partition for the `RedHat` like below 

![image](https://user-images.githubusercontent.com/63524369/221177914-41a8eec9-48cb-420a-bc7e-5e23ee6fbf82.png)

1. Burn QRadar ISO to USB 
2. Insert USB into the server 
 # Select one of the Appliance type by functionality options.
    
    1. Appliance Install (purchased as an Appliance).
    2. Software install (Hardware was purchased separately).
    3. High Availability 
    4. APPHOST
    
    Choose Your appliance  from functionality options.


4. After installing RedHat and But USB Run this command 
    
    ```bash
    lsblk                                # TO see if the usb is exist and what it call 
    mkdir -p /media/cdrom                # Create cdrom folder in media 
    mount -o loop /dev/sdb /media/cdrom  # Mount usb to cdrom folder 
    /media/cdrom/setup -t                # For the test mode 
    /media/cdrom setup                   # For the patch mode 
    
    ```
    
   
