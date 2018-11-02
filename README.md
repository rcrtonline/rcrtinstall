# RCRT
Shell script to install a RCRT Masternode on a Linux server running Ubuntu 14.04, 16.04 or 18.04. Use it on your own risk.

***
## Installation:
```
git clone https://github.com/lpcproject/lpcinstall.git
cd lpcinstall
bash lpc-install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the RCRT Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **5000** **RCRT** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Open **Debug Console** and type:
```
startmasternode "alias" "0" "MN1"
```
***

## Usage:
```
recruit-cli getinfo
recruit-cli mnsync status
recruit-cli masternode status
```
Also, if you want to check/start/stop **RCRT** , run one of the following commands as **root**:

**Ubuntu 16.04**:
```
systemctl status recruitd #To check the service is running.
systemctl start recruitd #To start RCRT service.
systemctl stop recruitd #To stop RCRT service.
systemctl is-enabled recruitd #To check whetether RCRT service is enabled on boot or not.
```
**Ubuntu 14.04**:  
```
/etc/init.d/recruitd start #To start RCRT service
/etc/init.d/recruitd stop #To stop RCRT service
/etc/init.d/recruitd restart #To restart RCRT service
```
***
