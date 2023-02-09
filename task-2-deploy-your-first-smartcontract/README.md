# TASK 2: Deploy Your First Smart Contract

> Hackathon: Concordium Hackathon - The Future of Identity

* Mainnet Addr: 3LRiBNQjJ8BrNe9D8QMHSmvvN6gwVwEjk5jnUNpVpkWaiiCN7r

### 1. Install and init project.

```
cargo install --locked cargo-generate
cargo concordium init

```

### 2. Build, Test's smartcontract.

```
cd counter-template

cargo concordium build -e --out ./my_concordium_project.wasm.v1
cargo concordium test
```


### 3. Build dist and Deploy.

```
mkdir dist

cargo concordium build --out dist/module.wasm.v1 --schema-out dist/schema.bin

concordium-client module deploy dist/module.wasm.v1 --sender concordium-hackathon --name counter_template --grpc-port 10000 --grpc-ip node.testnet.concordium.com

```

![3. Build dist and Deploy.](./Screenshot%202566-02-09%20at%2012.03.55.png "3. Build dist and Deploy.")

* Transaction: c27a9570fc70484d123213fbf0df13f295b707cdd93c9fd1623701091c287e16
* Block: 5833d58870f14df49ae87b3345e677a25a8f44c1d938fb765251a8a6eabf659b
* Module: 056f6c5ea6d79822b2ad6a36902c9c28a9cda4a1b8fa3eedacd773f5f2ac263a


<details>
  <summary> Console log "Deploy CounterTemplate contract". </summary>


```
Using default energy amount of 27878 NRG.
Deploy the module 'dist/module.wasm.v1' and name it 'counter_template'.
Allowing up to 27878 NRG to be spent as transaction fee.
Confirm [yN]: y
y
Deploying module...
Enter password for credential with index 0 and signing key with index 0: 
Transaction 'c27a9570fc70484d123213fbf0df13f295b707cdd93c9fd1623701091c287e16' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status c27a9570fc70484d123213fbf0df13f295b707cdd93c9fd1623701091c287e16'.
[12:03:16] Waiting for the transaction to be committed......
Transaction is committed into block 5833d58870f14df49ae87b3345e677a25a8f44c1d938fb765251a8a6eabf659b with status "success" and cost 52.083395 CCD (27878 NRG).
[12:03:23] Waiting for the transaction to be finalized....
Transaction is finalized into block 5833d58870f14df49ae87b3345e677a25a8f44c1d938fb765251a8a6eabf659b with status "success" and cost 52.083395 CCD (27878 NRG).
[12:03:29] Transaction finalized.
Module successfully deployed with reference: '056f6c5ea6d79822b2ad6a36902c9c28a9cda4a1b8fa3eedacd773f5f2ac263a'.
Module reference 056f6c5ea6d79822b2ad6a36902c9c28a9cda4a1b8fa3eedacd773f5f2ac263a was successfully named 'counter_template'.

```
 
</details>

<br/>

### 4. Initialize smartcontract.

```
concordium-client contract init 056f6c5ea6d79822b2ad6a36902c9c28a9cda4a1b8fa3eedacd773f5f2ac263a --sender concordium-hackathon --energy 30000 --contract counter_template --grpc-port 10000 --grpc-ip node.testnet.concordium.com
```

![4. Initialize smartcontract.](./Screenshot%202566-02-09%20at%2017.40.35.png "4. Initialize smartcontract.")

* Transaction: 4ee71a6b0d30c85979e0b20930bb09319b1fcf66b5167ed867f20cbe1cb2f255
* Block: b5b808689515e611288b22f70e1c66f8d9963675d1f5da171636918b331effc3
* Instance: 2843

<details>
  <summary> Console log "Init CounterTemplate contract". </summary>


```
Initialize contract 'counter_template' from module '056f6c5ea6d79822b2ad6a36902c9c28a9cda4a1b8fa3eedacd773f5f2ac263a' with no parameters. Sending 0.000000 CCD.
Allowing up to 30000 NRG to be spent as transaction fee.
Transaction expires on Thu,  9 Feb 2023 10:46:04 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0: 

Transaction '4ee71a6b0d30c85979e0b20930bb09319b1fcf66b5167ed867f20cbe1cb2f255' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status 4ee71a6b0d30c85979e0b20930bb09319b1fcf66b5167ed867f20cbe1cb2f255'.
[17:39:29] Waiting for the transaction to be committed.....
Transaction is finalized into block b5b808689515e611288b22f70e1c66f8d9963675d1f5da171636918b331effc3 with status "success" and cost 2.429889 CCD (1266 NRG).
[17:39:36] Transaction finalized.
Contract successfully initialized with address: {"index":2843,"subindex":0}
```

</details>

<br/>

### 5. Call 'increment' with pass6 (+6)

```
concordium-client contract update 2843 --entrypoint increment --parameter-json param/pass6.json --schema dist/schema.bin --sender concordium-hackathon  --energy 6000 --grpc-port 10000 --grpc-ip node.testnet.concordium.com
```

![5. Call 'increment' with pass6 (+6)](./Screenshot%202566-02-09%20at%2019.22.21.png "5. Call 'increment' with pass6 (+6)")

* Transaction: 35dd2adeb29fb566acd3d12dc9ff761aef2ab0c9a2963e050c173cc7b1c54005
* Block: ada4aebd5ec5138b1fc9f02705b516ee26995de67dafa65d9aee96d561dd4fa7
* Instance: 2843
* Parameter: 6 (param/pass6.json)

<details>
  <summary> Console log "Increment CounterTemplate contract". </summary>

```
Update contract 'counter_template' using the function 'increment' with JSON parameters from 'param/pass6.json'. Sending 0.000000 CCD.
Allowing up to 6000 NRG to be spent as transaction fee.
Transaction expires on Thu,  9 Feb 2023 12:30:59 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0: 
Transaction '35dd2adeb29fb566acd3d12dc9ff761aef2ab0c9a2963e050c173cc7b1c54005' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status 35dd2adeb29fb566acd3d12dc9ff761aef2ab0c9a2963e050c173cc7b1c54005'.
[19:21:14] Waiting for the transaction to be committed....
Transaction is finalized into block ada4aebd5ec5138b1fc9f02705b516ee26995de67dafa65d9aee96d561dd4fa7 with status "success" and cost 2.060623 CCD (1063 NRG).
[19:21:16] Transaction finalized.
Successfully updated contract instance {"index":2843,"subindex":0} using the function 'increment'.
```

</details>

<br/>

### 6. View result 'counter' on smartcontract.

```
concordium-client contract invoke 2843 --entrypoint view --schema dist/schema.bin --grpc-port 10000 --grpc-ip node.testnet.concordium.com
```

![6. View result 'counter' on smartcontract.](./Screenshot%202566-02-09%20at%2019.27.53.png "6. View result 'counter' on smartcontract.")
