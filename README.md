# wormholes-testnet
The Wormholes Chain solves the blockchain trilemma, which entails a necessary tradeoff between scalability, security, and decentralization, by building the technology to achieve the ideal balance between these three metrics, creating a highly scalable and secure blockchain system that doesn’t sacrifice decentralization

Website : www.wormholes.com

Wallet :  www.limino.com

Explorer : https://www.wormholesscan.com/

Manual guide : https://www.wormholes.com/docs/Install/run/docker/index.html

Spesifikasi :

CPU   : 4-core 2,9GHz

Memory: 8GB

SSD   : 500GB

Network bandwidth: 6 MB or higher

`***Open port 30303 dan 8545***`
```
ufw allow 22/tcp && ufw allow 30303/tcp && ufw allow 8545 && ufw enable
```

# install docker engine
```
sudo apt-get install ca-certificates curl gnupg lsb-release -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
```
# install docker compose
```
mkdir -p ~/.docker/cli-plugins/
curl -SL https://github.com/docker/compose/releases/download/v2.6.1/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
chmod +x ~/.docker/cli-plugins/docker-compose
sudo chown $USER /var/run/docker.sock
```
# clone dari github wormholes
```
git clone https://github.com/wormholes-org/wormholes
```
# run docker
```
cd wormholes
```
```
bash ./wormholes_install.sh
```
` ""ketik Y : jika baru pertama kali run node""`

`"tekan Enter jika sudah pernah menjalankannya"`

`***isi dengan privatekey wallet***`

# check wormholes log
```
tail -f /wm/.wormholes/wormholes.log | grep -i 'your adress'
```
` *** ganti your address dengan address testnet ***`
# stop node
```
docker stop wormholes
```
# Next step
`
*** membutuhkan 70k ERB to join validator ***`

Follow this https://wormholes.com/docs/Install/stake/index.html

# Monitor your node
```
wget -O monitor.sh https://raw.githubusercontent.com/mesahin001/wormholes/master/monitor.sh && chmod +x monitor.sh && ./monitor.sh
```

`*** gunakan ./monitor.sh jika setelah keluar dari vps ***`

# check versi node
```
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"eth_version","id":64}' http://127.0.0.1:8545
```
# check conection node
```
curl -X POST -H 'Content-Type:application/json' --data '{"jsonrpc":"2.0","method":"net_peerCount","id":1}' http://127.0.0.1:8545
```
`*** ganti youradrees dengan address yang dipake dinode ***`
# check block
```
curl -X POST -H 'Content-Type:application/json' --data '{"jsonrpc":"2.0","method":"eth_blockNumber","id":1}' http://127.0.0.1:8545
```
# check balance account
```
curl -X POST -H 'Content-Type:application/json' --data '{"jsonrpc":"2.0","method":"eth_getBalance","params":["youradress","pending"],"id":1}' http://127.0.0.1:8545

```
# check your private key

`***Must same at on wallet***`

```
docker exec -it wormholes /usr/bin/cat /wm/.wormholes/wormholes/nodekey
```
