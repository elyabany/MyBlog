# Installation  
قبل ما نتكلم في مرحله ال Installation عاوزين نعرف الاول ايه هي مكونات ال  Guardium
بتقسم ال Guardium الي 3 مكونات 


1. Collectors: The collector performs real-time capture and analysis of the database activity, and logs it for further analysis and use in alerting.
2. Aggregators: Guardium aggregators collect and merge information from multiple Guardium collectors 
3. Central Managers: The central manager (CM) is a specialized functionality that is enabled on an aggregato - Managed ALL

---
1.Guardium ISO - Collector | CM - central management
![image](https://user-images.githubusercontent.com/63524369/221241171-e58dd06a-9e1a-423d-9b4c-04979a846ef6.png)

بعد ما ينتهي من Installation هتلاقي CLI فهتدخل الاتي 

1.  **Username: `cli` , PASS: `guardium`**
2. `**store network interface ip $IP**`
3. `**store network interface mask $netmask`** 
4. `**store network routes defaultroute $Gatway**`
5. `**store system hostname $HostName`** 
6. **—> no** 
7. `**store network resolvers $DNS**`
8. `**restart network**`
9. **Check Unit Type → `show unit type`** 
10. **Check Network Interface → `show network interface all`** 
11. **Check network is working → `ping $Gatway`**
12. **Uploda License** there is 2 of them                                                                                                          
