# Blocknode
Shell script to install a [Blocknode Masternode](https://blocknode.tech/) on a Linux server running Ubuntu 16.04.
Use it on your own risk.
***

## VPS installation for version **1.5.2**
```
wget -N https://raw.githubusercontent.com/zoldur/Blocknode/master/blocknode_install.sh
bash blocknode_install.sh
```
***

## Desktop wallet setup

After the Masternode is up and running, you need to configure the desktop wallet accordingly. Here are the steps:
1. Open the Blocknode Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **100000** BND to **MN1**. You need to send all 100000 coins in one single transaction.
4. Wait for 15 confirmations.
5. Go to **Help -> "Debug Window - Console"**
6. Type the following command: **masternode outputs**
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* TxIndex:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
```
startmasternode alias false MN1
```
14. Login to your VPS and check your masternode status by running the following command to confirm your MN is running:
```
blocknode-cli masternode status
```
***

## Usage:
```
blocknode-cli masternode status
blocknode-cli getinfo
blocknode-cli mnsync status
```
Also, if you want to check/start/stop **Blocknode**, run one of the following commands as **root**:

```
systemctl status Blocknode #To check if Blocknode service is running
systemctl start Blocknode #To start Blocknode service
systemctl stop Blocknode #To stop Blocknode service
systemctl is-enabled Blocknode #To check if Blocknode service is enabled on boot
```
***

## Masternode update:
In order to update your Blocknode Masternode to version 1.5.2, please run the following commands:
```
cd /tmp
wget -N https://github.com/blocknodetech/blocknode/releases/download/v1.5.2/blocknode-1.5.2-x86_64-linux-gnu.tar.gz
tar xvzf blocknode-1.5.2-x86_64-linux-gnu.tar.gz --strip 2
systemctl stop Blocknode
mv blocknoded blocknode-cli /usr/local/bin
systemctl start Blocknode
rm blocknode-1.5.2-x86_64-linux-gnu.tar.gz
blocknode-cli getinfo
```
Open your desktop wallet and start the node from there.
***

## Donations
Any donation is highly appreciated

**BND**: B7P5kBybyfHnc8pGE94fkKZxoh6QwkZjbF  
**BTC**: 3MQLEcHXVvxpmwbB811qiC1c6g21ZKa7Jh  
**ETH**: 0x26B9dDa0616FE0759273D651e77Fe7dd7751E01E  
**LTC**: LNZpK4rCd1JVSB3rGKTAnTkudV9So9zexB
