# [TASK 1: Setup Development Environment](https://gitcoin.co/issue/29741)

> Hackathon: Concordium Hackathon - The Future of Identity

* Mainnet Addr: 3LRiBNQjJ8BrNe9D8QMHSmvvN6gwVwEjk5jnUNpVpkWaiiCN7r

## 1. Setup 'rust lang' toolchain.
```
export RUSTUP_HOME=$HOME/Library/Toolchain/rustup
export CARGO_HOME=$HOME/Library/Toolchain/cargo

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

source "$HOME/Library/Toolchain/cargo/env"
rustup target add wasm32-unknown-unknown
```

### 2. Install cargo 'concordium' extension.
```
wget https://distribution.concordium.software/tools/macos/signed/cargo-concordium_2.7.0
mv cargo-concordium_2.7.0 $CARGO_HOME/bin/cargo-concordium

chmod +x $CARGO_HOME/bin/cargo-concordium

cargo concordium

```

![2. Install cargo 'concordium' extension.](./Screenshot%202566-02-08%20at%2011.01.48.png "2. Install cargo 'concordium' extension.")


### 3. Install 'concordium' client.

```
concordium-client consensus status --grpc-port 10000 --grpc-ip node.testnet.concordium.com
```

![3 - Install 'concordium' client.](./Screenshot%202566-02-08%20at%2011.03.34.png "3 - Install 'concordium' client.")

### 4. Create ID & Acc then export private key.

![Setting up](./Screenshot%202566-02-08%20at%2010.32.13.png "1-2-3")

* Addr (Testnet): 3PTTUfC2hToowW4saZFjqU9VstvAyzEiS5QQWQ1BBB1nj5xyDp


### 5. Import Testnet key to concordium client's config.
```
concordium-client config account import 3PTTUfC2hToowW4saZFjqU9VstvAyzEiS5QQWQ1BBB1nj5xyDp.export --name concordium-hackathon

Enter encryption password: 
Loaded the following account from the testnet chain:
- 3PTTUfC2hToowW4saZFjqU9VstvAyzEiS5QQWQ1BBB1nj5xyDp 'concordium-hackathon'.
All signing keys have been encrypted with the password used for this import.
Note that accounts are not transferable between different chains, e.g., from testnet to mainnet or vice-versa.
...

Added name mapping: 'concordium-hackathon' --> '3PTTUfC2hToowW4saZFjqU9VstvAyzEiS5QQWQ1BBB1nj5xyDp'.
Warning: Importing account without a secret encryption key provided. This account will not support encrypted transfers.
The keys were successfully written to disk.

```


