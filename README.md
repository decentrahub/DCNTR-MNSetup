# Decentrahub Masternode Setup (Ubuntu 16.04 / 18.04)
This guide will assist you in setting up a DecentraHub Masternode on a Linux Server running Ubuntu 16.04 / 18.04

If you require further assistance, contact the support team at <a href="https://discord.gg/SVjbNTg" target="_blank">Discord</a>
***
- [Decentrahub Masternode Setup](#decentrahub-masternode-setup)  
  	* [Requirements](#requirements) 
  * [Connecting to the VPS and installing the masternode script](#Connecting-to-the-VPS-and-installing-the-masternode-script)  
         [1. Log into the VPS with **root**](#1-log-into-the-vps-with-root)  
         [2. Git Installation](#2-git-installation)  
         [3. Clone MN setup script](#3-clone-mn-setup-script)  
         [4. Start MN setup script](#4-start-mn-setup-script)  
         [5. Copy Masternode Private Key](#5-copy-masternode-private-key-from-vps-console-window-and-pres-enter)
  * [Setup QT wallet](#setup-qt-wallet)  
         [1. Create new receiving address and copy it](#1-create-new-receiving-address-and-copy-it)  
	 [2. Send Collateral amount of DCNTR to copied address](#2-send-collateral-amount-of-dcntr-to-copied-address)  
	 [3. Get MN output and Set Masternode Configuration File](#3-open-console-get-mn-output-and-set-masternode-configuration-file-and-save-it)  
	 [4. Wait at least 15 confirmation of transaction](#4-wait-at-least-15-confirmation-of-transaction)  
         [5. Restart QT wallet](#5-restart-qt-wallet)  
         [6. Start MN in QT wallet console](#6-start-mn-in-qt-wallet-console)  
	 [7. Check Masternode Status in VPS](#7-check-masternode-status-in-vps)  

***
## Requirements
- 1000 DCNTR coins.
- A VPS running Linux Ubuntu 16.04 or 18.04 with 1 CPU & 1GB Memory minimum (2gb Recommended) from [Vultr](https://www.vultr.com/?ref=8622028) or any other providers.
- DecentraHub Wallet (Local Wallet)
- An SSH Client (<a href="https://www.putty.org/" target="_blank">Putty</a> or <a href="https://dl.bitvise.com/BvSshClient-Inst.exe" target="_blank">Bitvise</a>)

***
## Connecting to the VPS and installing the masternode script
***
##### 1. Log into the VPS with **root**  
[![Vps](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/1.png)]
***
##### 2. Git Installation:  
- ```sudo apt-get install -y git-core```  

[![Git](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/2.png)]
***
##### 3. Clone MN setup script: 
- ```git clone https://github.com/decentrahub/DCNTR-MNSetup.git```  

***
##### 4. Start MN setup script: 
- ```cd DCNTR-MNSetup && chmod +x DCNTR-16.04.sh && ./DCNTR-16.04.sh```  
**OR**  
- ```cd DCNTR-MNSetup && chmod +x DCNTR-18.04.sh && ./DCNTR-18.04.sh```   

[![Script2](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/4.png)]  

**Now ask for VPS Public IP Address** 
[![Script3](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/5.png)]

**Now you need to wait some time, while script preparing the VPS to setup**  
***
##### 5. Copy masternode private key from VPS console window and pres "Enter":
[![Download Bitvise](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/6.png)] 

- if you see this, you are on the right track:
[![QT1](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/7.png)]

- to check VPS daemon status, type: ```decentrahub-cli getinfo```
[![QT2](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/8.png)]

**Don't close this window!** 
***		

## Setup QT wallet
##### 1. Create new receiving address and copy it
[![QT3](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/9.png)] 

***
##### 2. Send Collateral amount of DCNTR to copied address
[![QT4](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/10.png)]
***
##### 3. Open console Get MN output and set masternode configuration file and save it
- ```mn1 VPS_IP:2120 masternode_genkey masternode_output output_index```:
[![QT5](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/11.png)]
***
##### 4. Wait at least 15 confirmation of transaction
[![QT6](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/12.png)]
***
##### 5. Restart QT wallet  
- **it's important**
***
##### 6. Start MN in QT wallet console:
- ```startmasternode alias false DCNTR_MN1```

[![QT7](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/13.png)]
***
##### 7. Check Masternode Status in VPS:
- ```decentrahub-cli startmasternode local false``` 
- ```decentrahub-cli getmasternodestatus```  
[![QT8](https://raw.githubusercontent.com/decentrahub/DCNTR-MNSetup/master/assets/14.png)]  
***
**Сongratulations you did it!**


# Additional Notes:

## Use autocombinerewards features for combine Masternode Rewards.

### For Use it in Local (Windows/Linux/MacOS) Wallet  follow below Step:

- Go to SETTINGS -> Debug -> Console and fire below command in console windows.  

- 	```autocombinerewards true 500```

- Here 500 is the Amount of DCNTR Coin, Wallet will automatically monitor for coins with value below that amount, 
and combine them in one transaction. So you can keep that amount whatever you want to combine. (Ex. 100 or 200 or 500 or 2000 as you wish).  

- After complete this process if you stop or Exit from wallet and start again than you have to do this same process again.
Otherwise you can start that wallet 24*7.

### For VPS follow below step: 

- Start daemon in VPS after that fire below command:  

- 	```./decentrahub-cli autocombinerewards true 500```

- Same as above here also you can change amount in place of 500 whatever you want to combine.	