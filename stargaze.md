## Download latest snapshot (using the example of Stargaze)  
Stop Stargaze service  
```
systemctl stop starsd.service
```  

Remove old data in directory `~/.starsd/data`  
```
rm -rf ~/.starsd/data; \
mkdir -p ~/.starsd/data; \
cd ~/.starsd/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s http://cosmos-snap.staketab.com/stargaze/ | egrep -o ">stargaze-1.*tar" | tr -d ">"); \
wget -O - http://cosmos-snap.staketab.com/stargaze/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start starsd.service; \
journalctl -u starsd.service -f --no-hostname
```
