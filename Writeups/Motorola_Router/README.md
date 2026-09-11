# Motorola SURFBOARD SBG6580    

IoT Hacking writeup on a $8 used router purchased from Goodwill. I'll walk you through recon, signal analysis/interposition, dumping the firmware using jtag, and reverse engineering.  


# 1. Recon 

## What is the intended functionality?              

* 3 Functions       
    a. Router   
    b. Switch   
    c. ? 


## What do we want to do with this device?      
    1. Extract the Firmware 
    2. Root/debug shell to inspect the filesystem   
    3. Uncover any secrets, unique keys, and passwords stored in memory 
    4. Patch/Rewrite firmware   


## Opening the Case & ID'ing chips/components   

* SPANSION 16 PIN Flash 


* Broadcom CPU  



## Open Network Ports & Web Intefaces   




# 2. Foothold   
    - other open vias are 5v+ or 12v+   


## JTAG : Signal Analysis w DMM     

    0. Why could it be JTAG?        
        - 2x7 layout, 14 pin EJTAG, older systems, MIPS arch    


    1. Continuity Test - Identifying GND    
        - not connected to power    
        - pins 2 and 13     

1   2    
3   4   
5   6   
7   8   
9   10  
11  12  
13  14  


    2. Voltage Test     
    - powered on    
3.3     GND     
3.3     3.3     
0.0     3.3     
0.0     0.0     
0.0     3.3     
0.0     0.0     
GND     3.3     


    3. Common EJTAG layout and Datasheet    
        - uses 4 pins, optional reset pin   

    4. Using a Logic Analyzer and Pulseview     
        - dont really know what is TMS,TDO,TDI etc. 


    5. Resistance Test  
        - helps to identify which is reset  
        - ohms 200k, not connected to power 
        - black to GND, and red to pins 
        - 4 pins 140+ likely TMS,TDO,TDI,TCK   (just dont know which is what)   
        - ~0.5 are likely nSRST 

~0.5     GND     
140+     140+     
1        140+  
1        1     
1        140+     
1        1  
GND      ~0.5     


    6. Using a SBC to identify the correct JTAG pins    
        - scripts from void star sec    
        - use 5v relay probably necessary   


    7. Using OpenOCD to interact    


    8. Extracting the firmware  
        - is it available online?   



# 3. Reverse Engineering        






