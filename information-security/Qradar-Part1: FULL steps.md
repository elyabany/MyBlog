#Qradar install Full steps 
1. Install Red Hat Linux  

```jsx
RedHat 7.6 ----> QRadar 7.3.* 
RedHat 7.7 ----> QRadar 7.4.* 
RefHat 7.9 ----> QRadar 7.5 
```

1.  Setup the Partition for the `RedHat` like below 

![image](https://user-images.githubusercontent.com/63524369/221180038-0e33d1bf-7cf2-47d0-917b-db7b13fb5ac9.png)


1. Burn QRadar ISO to USB 
2. Insert USB into the server 
3. After installing RedHat and But USB Run this command 
    
    ```bash
    lsblk                                # TO see if the usb is exist and what it call 
    mkdir -p /media/cdrom                # Create cdrom folder in media 
    mount -o loop /dev/sdb /media/cdrom  # Mount usb to cdrom folder 
    /media/cdrom/setup -t                # For the test mode 
    /media/cdrom setup                   # For the patch mode 
    
    ```
    
 
 ---
    
 ## Select one of the Appliance type by functionality options.
    
    - Appliance Install (purchased as an Appliance).
    - Software install (Hardware was purchased separately).
    - High Availability Appliance
    - APPHOST Appliance
        
    
   ![image](https://user-images.githubusercontent.com/63524369/221180099-db38ac5b-16d2-4777-a3d8-e05fce0b6d43.png)
    
 
 ---
    
 # Qradar Console All-in-one
    
  ![image](https://user-images.githubusercontent.com/63524369/221180177-04dc379f-26b0-4841-9225-00e3411c3c1f.png)
   ![image](https://user-images.githubusercontent.com/63524369/221180297-f36b45b2-0f11-47a2-8390-3be3770280c1.png)
   ![image](https://user-images.githubusercontent.com/63524369/221180358-b76bbe1b-70bf-4f61-b3b4-71cd2378270c.png)
    ![image](https://user-images.githubusercontent.com/63524369/221180391-8e403831-3a47-4a76-8e4d-a1206f8d6686.png)
   ![image](https://user-images.githubusercontent.com/63524369/221180423-ba05148d-fca9-48cf-bd74-aae53e9e7fec.png)

 
 ---
    
# Event Collector
    
   ![image](https://user-images.githubusercontent.com/63524369/221180580-7a3f1f99-626b-4c5b-9bd9-617714f0eea0.png)

  ## then same steps 
 
 ---
    
# APP HOST Appliance
  ![image](https://user-images.githubusercontent.com/63524369/221180668-a1eb33f2-3aea-40f9-a004-ec167f694d20.png)
  ![image](https://user-images.githubusercontent.com/63524369/221180691-68edaa26-0eba-46fb-87cf-ea077384b94e.png)

  ## then same steps 
 
 ---

# QRM
    
   ![image](https://user-images.githubusercontent.com/63524369/221180748-baa9a4b6-fe31-4f4e-813c-e27b252b86a9.png)
    ## then same steps 
    ---
    
 # High Availability Appliance
    
   ![image](https://user-images.githubusercontent.com/63524369/221180806-539d5c02-521f-4162-b8ca-96906533c564.png)
   ![image](https://user-images.githubusercontent.com/63524369/221180835-69deab97-ab74-4d31-b4e0-115fcf78fe51.png)

   
   1. Yes : if your are using HA for Console 
   2. No : if your are using HA for collector 
  
   ## then same steps 
 
