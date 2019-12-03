#BZX
Use this shell script to install a [BZX Masternode](https://www.bitcoinzerox.net/) on a Linux server running Ubuntu 16.04.  
This will require a VPS, I use [Vultr](https://www.vultr.com/?ref=7310394).  I recommend using a $5 server.
This script will install **BZX Core v5.0.3.5 **.
***

## Installation:
Log into the server using ssh (Putty for windows or terminal for Mac users) and run the following commands:
```
wget -q https://raw.githubusercontent.com/lockdawg/BZX/master/bzx_install.sh
bash bzx_install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows/Mac Wallet:
1. Open the BCX Core Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **45000** **BZX** to **MN1**.
4. Wait for ~15 confirmations before starting the node.
5. Go to **Help -> "Debug window - Console"**
6. Type the following command: **bznode outputs**
7. Type the following command: **bznode genkey**
8. Open masternode.conf from the following folder %appdata%\bitcoinzero (windows) or ~/Library/Application Support/ (hidden folder for Mac users)
9. Add the following entry:
```
Alias Address Genkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:29301**
* Genkey: **Masternode GenKey**
* TxHash: **First value from Step 6** 
* Output index:  **Second value from Step 6** It can be **0** or **1**
10. Click OK and exit the Wallet.
11. Open BCZ Core Wallet, go to **Masternode Tab**.
12. Click **Update status** to see your node. If it is not shown, close the wallet and start it again.
13. Click **Start All** or **Start Alias**
12. If you are not able to see your **Masternode**, try to close and open your desktop wallet.
***

## Usage:
```
bitcoinzero-cli getinfo
bitcoinzero-cli xnode status
```
Also, if you want to check/start/stop **BZX** , run one of the following commands as **root**:
```
systemctl status BZX #To check the service is running.
systemctl start BZX #To start BZX service.
systemctl stop BZX #To stop BZX service.
systemctl is-enabled BZX #To check whether BZX service is enabled on boot or not.
```
***

## Updating BZX
The first line (rm bcz_update.sh) is not required the very first time you update the node and will return an error if you run it.  This is fine, continue with the update script.
```
rm bzx_update.sh*
wget -q https://raw.githubusercontent.com/lockdawg/BZX/master/bzx_update.sh
bash bzx_update.sh
```
***

## Donations:  

**BZX**: XXiddZsJZBdo3sVzo7tLPszFAjCMFP4S5n  
**BTC**: 33mkLq6fmwfCz5dfK54giowZYygtBxypXr  
**ETH**: 0x1CCa2B182516a2bdC6989606F52E28407751A9D3  
**LTC**: MTkeGVv99gTeoyGnGppPCVDQ2Xz9sF6UVn
