# LayerEdge

![1500x500](https://github.com/user-attachments/assets/b9412116-6613-40ce-b04e-dd49c905bfca)


| X        | Minimum              |
|------------------|----------------------------|
| **CPU**          | X |
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

## 1. Server Güncellemece : 

```bash
sudo apt update -y && sudo apt upgrade -y
```
## 2. Paketleri Yükleyelim:

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

## Risc0

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

## LayerEdge ; 

```bash
git clone https://github.com/Layer-Edge/light-node.git
```
```bash
cd light-node
```

## Konfigürasyon

- Siteye bağlandığınız cüzdan adresinin private keyini 'cli-node-private-key' buraya yazın. ; 

- Private key kısmında tırnakların içine yazın tırnakları kaldırmayın.
- Privatekey'in önündeki 0x'i kaldırarak yapıştırdım ben - normal privatekey hata verdi.

```bash
nano .env
```

```bash
export GRPC_URL=34.31.74.109:9090
export CONTRACT_ADDR=cosmos1ufs3tlq4umljk0qfe8k5ya0x6hpavn897u2cnf9k0en9jr7qarqqt56709
export ZK_PROVER_URL=http://127.0.0.1:3001
export API_REQUEST_TIMEOUT=100
export POINTS_API=http://127.0.0.1:8080
export PRIVATE_KEY='cli-node-private-key'
```

- CTRL X Y Enter. Kayıt edecek.

## Merkleyi Çalıştırıyoruz.

```bash
screen -S merkle
```
```bash
cd risc0-merkle-service
cargo build && cargo run
```

## LayerEdge Light Node'yi Buildliyoruz Sonrada Çalıştırıyoruz.

```bash
screen -S layeredge
```

```bash
go build
./light-node
```

- CTRL A + D

- Çalışınca Public Keyinizi Kaydedin ; 

![image](https://github.com/user-attachments/assets/0e925a9f-3cbf-4e82-9ff3-5d140285bd7f)


## CLI Puan Görüntüleme ; 

https://light-node.layeredge.io/api/cli-node/points/cuzdanadresi

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=FurkanL0&style=flat-square&color=red&label=Profile+Views+/+Repo+Views+" alt="Repo / Profile Views" />
</p>
