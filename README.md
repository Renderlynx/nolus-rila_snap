# nolus-rila snapshot (updated every 24 hours) Size: ~5GB
Stop node and remove old db
```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
mkdir $HOME/.nolus/data
```
Download snapshot
```
wget -O - http://95.216.65.177/nolus/nolus_latest.tar | tar xf - -C $HOME/.nolus/data
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```

Restart node & check logs
```
sudo systemctl start nolusd && sudo journalctl -fu nolusd -o cat
```
