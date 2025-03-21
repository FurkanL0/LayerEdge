# LayerEdge
 
![1500x500](https://github.com/user-attachments/assets/b9412116-6613-40ce-b04e-dd49c905bfca)
 
| X        | Minimum              |
|------------------|----------------------------|
| **CPU**          | X                     |
| **RAM**          | X GB                     |
| **Storage**      | X GB SDD                   |
| **Network**      | X Mbps (1 Gbps+ recommended) |
 

 
| Server Provider        | Link              | Features |
|------------------|----------------------------|----------------------------|
| **Contabo**          | [Link](https://www.dpbolvw.net/click-101330552-12454592)                     | Cheap / Paypal  |
| **PQ**      | [Link](https://pq.hosting/?from=627713)                  | Cheap / Crypto Payment |
| **NetCup**          | [Link](https://www.netcup.com/en/?ref=261820) | Cheap / Paypal |
 

 
## Port : 
 
- Mercle : 3001

# SETUP

## 1. Server Update : 

```bash
sudo apt update -y && sudo apt upgrade -y
```
 
## 2. Install Packages:
 

 
```bash
sudo apt install htop ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev tmux iptables curl nvme-cli git wget make jq libleveldb-dev build-essential pkg-config ncdu tar clang bsdmainutils lsb-release libssl-dev libreadline-dev libffi-dev jq gcc screen unzip lz4 -y
```
 
## GO ;
 

```bash
wget https://go.dev/dl/go1.22.0.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.22.0.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
source ~/.bashrc
go version 
```

## Rust ; 

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
 
- 1 - Enter.

```bash
source $HOME/.cargo/env
rustc --version 
```
 
## Risc0 Toolchain
 
```bash 
curl -L https://risczero.com/install | bash
```
 
```bash 
source "/root/.bashrc"
```
```bash
rzup install
```
```bash
rzup --version
```

## Docker ; 
```bash
sudo apt install -y docker.io
sudo systemctl enable --now docker
sudo usermod -aG docker $(whoami)
docker --version
```
## LayerEdge ; 

```bash
git clone https://github.com/Layer-Edge/light-node.git
```
 
```bash
cd light-node
```

 
## Configure Environment Variables

- Change 'cli-node-private-key' with Layeredge Connected Wallet Adress if dosent work delete 0x on the privatekey. ; 

```bash
nano .env
```

 
```bash
GRPC_URL=grpc.testnet.layeredge.io:9090
CONTRACT_ADDR=cosmos1ufs3tlq4umljk0qfe8k5ya0x6hpavn897u2cnf9k0en9jr7qarqqt56709
ZK_PROVER_URL=http://127.0.0.1:3001
API_REQUEST_TIMEOUT=100
POINTS_API=https://light-node.layeredge.io
PRIVATE_KEY='cli-node-private-key'
```
 

 
## Start the Merkle Service
 

 
```bash
screen -S merkle
```
 
```bash
cd risc0-merkle-service
cargo build && cargo run
```
 
- CTRL A + D
 
## Build and Run the LayerEdge Light Node
 

 
```bash
screen -S layeredge

```
 

 
```bash
go build
./light-node
```

CTRL A + D

- Save your Public Key when it works;

![image](https://github.com/user-attachments/assets/0e925a9f-3cbf-4e82-9ff3-5d140285bd7f)
 
## Fetch Points via CLI ; 
 
- https://light-node.layeredge.io/api/cli-node/points/walletadress

- Add from the site ;

- https://dashboard.layeredge.io/

![image](https://github.com/user-attachments/assets/cd9ac166-6f9f-4fec-8dfd-caa87454b340)



<p align="center">
 
  <img src="https://komarev.com/ghpvc/?username=FurkanL0&style=flat-square&color=red&label=Profile+Views+/+Repo+Views+" alt="Repo / Profile Views" />
 
</p>
