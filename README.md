- Snapshot : https://snapshot.node.sarjananode.studio/bb/
- Snapshot File : https://snapshot.node.sarjananode.studio/bb/snapshot_latest.tar.lz4

________________________________________________

## Auto install
```
wget -O bonusblock.sh https://raw.githubusercontent.com/SaujanaOK/BonusBlock/main/bonusblock.sh && chmod +x bonusblock.sh && ./bonusblock.sh
```

### Pasca install
```
source $HOME/.bash_profile
```
________________________________________________
## SNAPSHOT
### Stop Node
```
sudo apt install lz4 -y
sudo systemctl stop bonus-blockd
cp $HOME/.bonusblock/data/priv_validator_state.json $HOME/.bonusblock/priv_validator_state.json.backup
rm -rf $HOME/.bonusblock/data
```
### Use our Snapshot
```
curl -L  https://snapshot.node.sarjananode.studio/bb/snapshot_latest.tar.lz4 | lz4 -dc - | tar -xf - -C $HOME/.bonusblock
mv $HOME/.bonusblock/priv_validator_state.json.backup $HOME/.bonusblock/data/priv_validator_state.json
```
### Start Node
```
sudo systemctl restart bonus-blockd && sudo journalctl -u bonus-blockd -f --no-hostname -o cat
```
