# LayerEdge

![1500x500](https://github.com/user-attachments/assets/b9412116-6613-40ce-b04e-dd49c905bfca)


| X        | Minimum              |
|------------------|----------------------------|
| **CPU**          | ∞ |
| **RAM**          | ∞ GB                     |
| **Storage**      | ∞ GB SDD                   |
| **Network**      | ∞ Mbps (∞ Gbps+ recommended) |

| Server Sağlayıcıları        | Link              | Özellikler |
|------------------|----------------------------|----------------------------|
| **Contabo**          | [Link](https://www.dpbolvw.net/click-101330552-12454592)                     | Ucuz / Kredi Kartı / Paypal  |
| **PQ**      | [Link](https://pq.hosting/?from=627713)                  | Ucuz / Kredi Kartı / Kripto İle Ödeme |
| **NetCup**          | [Link](https://www.netcup.com/en/?ref=261820) | Ucuz / Kredi Kartı / Paypal |

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


# Yüksek CPU Kullanım ; 

## Konfigürasyon

- Siteye bağlandığınız cüzdan adresinin private keyini 'cli-node-private-key' buraya yazın. ; 

- Private key kısmında tırnakların içine yazın tırnakları kaldırmayın.
- Privatekey'in önündeki 0x'i kaldırarak yapıştırdım ben - normal privatekey hata verdi.

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

- CTRL X Y Enter. Kayıt edecek.

## Merkleyi Çalıştırıyoruz.

```bash
screen -S merkle
```
```bash
cd risc0-merkle-service
cargo build && cargo run
```

![image](https://github.com/user-attachments/assets/90462164-c3c0-4735-8877-670543c0afb7)

- Bunu görünce CTRL A + D ile çıkın.

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

![image](https://github.com/user-attachments/assets/4ac59fd4-cc5f-4abd-8430-1da8f867cc7b)


## CLI Puan Görüntüleme ; 

https://light-node.layeredge.io/api/cli-node/points/cuzdanadresi

- Siteden Ekleyin ; 

- https://dashboard.layeredge.io/

![image](https://github.com/user-attachments/assets/cd9ac166-6f9f-4fec-8dfd-caa87454b340)

# Az CPU Kullanım ; 

## Konfigürasyon

- Siteye bağlandığınız cüzdan adresinin private keyini 'cli-node-private-key' buraya yazın. ; 

- Private key kısmında tırnakların içine yazın tırnakları kaldırmayın.
- Privatekey'in önündeki 0x'i kaldırarak yapıştırdım ben - normal privatekey hata verdi.

```bash
nano .env
```

```bash
GRPC_URL=grpc.testnet.layeredge.io:9090
CONTRACT_ADDR=cosmos1ufs3tlq4umljk0qfe8k5ya0x6hpavn897u2cnf9k0en9jr7qarqqt56709
ZK_PROVER_URL=https://layeredge.mintair.xyz/
API_REQUEST_TIMEOUT=100
POINTS_API=https://light-node.layeredge.io
PRIVATE_KEY='cli-node-private-key'
```

- CTRL X Y Enter. Kayıt edecek.


## LayerEdge Light Node'yi Buildliyoruz Sonrada Çalıştırıyoruz.

```bash
screen -S layeredge
```
```bash
go build
./light-node
```

![image](https://github.com/user-attachments/assets/291fec20-bc36-4bd8-bb26-8a55471e8815)


- CTRL A + D

- Çalışınca Public Keyinizi Kaydedin ; 

![image](https://github.com/user-attachments/assets/0e925a9f-3cbf-4e82-9ff3-5d140285bd7f)



## CLI Puan Görüntüleme ; 

https://light-node.layeredge.io/api/cli-node/points/cuzdanadresi

- Siteden Ekleyin ; 

- https://dashboard.layeredge.io/

![image](https://github.com/user-attachments/assets/cd9ac166-6f9f-4fec-8dfd-caa87454b340)


## Service ; 

```bash
sudo tee /etc/systemd/system/layer-edge.service <<EOF
[Unit]
Description=Layer Edge Light Node
After=network.target

[Service]
Type=simple
User=$(whoami)
WorkingDirectory=$HOME/light-node
ExecStart=$HOME/light-node/light-node
Restart=always
RestartSec=5
EnvironmentFile=$HOME/light-node/.env
Environment="PATH=/usr/local/go/bin:/usr/bin:/bin:$HOME/.cargo/bin:$HOME/.risc0/bin"

[Install]
WantedBy=multi-user.target
EOF
```

```bash
sudo systemctl daemon-reload
sudo systemctl enable layer-edge
sudo systemctl start layer-edge
```

## Loglar İçin ; 

```bash
journalctl -fo cat -u layer-edge
```

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=FurkanL0&style=flat-square&color=red&label=Profile+Views+/+Repo+Views+" alt="Repo / Profile Views" />
</p>
