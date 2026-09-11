# Gabba-Goods-G-Home-Security-Camera
IoT Hacking Writeup on a cheap home security camera. I'll walk you through recon, signal analysis/interposition, dumping firmware, and reverse engineering.


![Camera](camera.png)


# 1. Recon  

## What is the intended functionality?    

* G-Home by Gabba Goods App
  - the user can link their camera to their own G-Home account using their app upon setup
  - the user can then see live camera feed through the app, including features such as live audio and mic input
   


## What do we want to do with this device?  
  1. Extract Firmware    
  2. Root/Debug shell to inspect the filesystem     
  3. Understand the authentication protocol between the device and the app    
  4. Uncover any secrets(unique keys, passwords in flash)
  5. Patch/Rewrite the firmware to create a backdoor     

## Opening the Case and ID'ing chips/components  

* MVT3610S2_DB V1.1
  - Silk Screen board number    
  - PCB revision of a Wireless Smart CCTV IP Security Camera    
  - FCC Identity: Smarti Fact Technology Inc    


* Winbond 2564JVSTQ 2084    
  - Winbond SpiFlash Memory Series (supports std,dual,quad SPI)    
  - 64 megabits = 8MB of storage    
  - 8 Pin SOIC (Small Outline Integrated Circuit)     
  - Quad SPI enabled by default    


* ULN2803A 2026AH
  - Darlington transistor array
  -  


## Open Network Ports  




# 2. Foothold


## UART  


## Dumping SPI NOR Flash Memory  

![EEPROM](IMG_1665.jpeg)

![flashrom](SPIFLASH.png)

![stringscmd](stringsPoC.png)

![rooting](greproot.png)



# 3. Reverse Engineering  



