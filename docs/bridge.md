---
id: deposit_withdrawal
title:  How to Deposit & Withdraw CKB on Godwoken
---
import useBaseUrl from "@docusaurus/useBaseUrl";

For deposit and withdrawal operations on Godwoken, two options are available:

1. Using a UI deposit or withdrawal provided by [yokaiswap](https://testnet.yokaiswap.com/bridge/deposit) to perform the relevant actions.
2. Using `gw-tools` deposit or withdrawal to perform the relevant actions.

---

### Using GW-tools to Deposit

Use `--help` to view the available commands.

```shell
cargo run --bin gw-tools -- deposit-ckb --help
```

<details>
<summary>Click to view the detailed output</summary>

```
gw-tools-deposit-ckb
Deposit CKB to godwoken

USAGE:
	 gw-tools deposit-ckb [OPTIONS] --capacity <capacity> --config-path <config-path>  --privkey-path <privkey-path>  --scripts-deployment-path <scripts-deployment-path>

FLAGS:
	 -h, --help				Prints help informaiton
	 -V, --version				Prints version information

OPTIONS:
	 -c, --capacity <capacity>		CKB capacity to deposit
	     --ckb-rpc <ckb-rpc-url>		CKB jsonrpc rpc sever URL [default: http://127.0.0.1:8114]

	 -o, --config-path <config-path>	The config.homl file path
	 -e, --eth-address <eth-address>	Target eth address, calculated by private key in default
	 -f, --fee <fee>			Transaction fee, default to 0.0001 CKB [default: 0.0001]
	 -g, --godwoken-rpc-url <godwoken-rpc-url>
	 					Godwoken jsonrpc rpc sever URL [default: http://127.0.0.1:8119]

	 -k, --privkey-path <privkey-path>	The private key file path
	     --scripts-deployment-path <scripts-deployment-path>	
	 					The scripts deployment results json file path

```
</details>

For more information on the CKB RPC, refer to [CKB Wiki](https://github.com/nervosnetwork/ckb/wiki/Chains)

### <code>gw-tool deposit</code> Subcommands

|command|description|
|---|---|
|capacity          |The amount of CKB to deposit (unit:  CKB)|
|ckb-rpc           |CKB node URL that defaults to http://127.0.0.1:8114/|
|config-path          |The config.toml file required for Godwoken to run|
|eth-address          |The target eth address to deposit|
|fee          |The transaction fee in a CKB transaction (The default rate is 0.0001 CKB.)|
|godwoken-rpc-url          |The RPC address of Godwoken that defaults to http://127.0.0.1:8119/|
|privkey-path          |A file written with the private key (hex string) which is used to pay the deposit fee|
|scripts-deployment-path          |json file path of the [script's deployment results](https://github.com/nervosnetwork/godwoken-public/blob/master/testnet/config/scripts-deploy-result.json)|

---

### Using GW-tools to Withdraw

Use `--help` to view the available commands.

```shell
cargo run --bin gw-tools -- withdraw --help
```

<details>
<summary>Click to view the detailed output</summary>


```
gw-tools-withdraw
withdraw CKB / sUDT from godwoken

USAGE:
	 gw-tools withdraw [OPTIONS] --capacity <capacity> --config-path <config-path> --owner-ckb-address <owner-ckb-address> --privkey-path <privkey-path>  --scripts-deployment-path <scripts-deployment-path>

FLAGS:
	 -h, --help				Prints help informaiton
	 -V, --version				Prints version information

OPTIONS:
	 -m, --amount <amount>		 sUDT amount to withdrawal [default: 0]
	 -c, --capacity <capacity>		CKB capacity to withdrawal
	 -o, --config-path <config-path>	The config.homl file path
	 -g, --godwoken-rpc-url <godwoken-rpc-url>
	 					Godwoken jsonrpc rpc server URL [default: http://127.0.0.1:8119]

	 -a, --owner-ckb-address <owner-ckb-address>	owner ckb address (to)
	 -k, --privkey-path <privkey-path>	The private key file path
	     --scripts-deployment-path <scripts-deployment-path>	
	 					The scripts deployment results json file path

	 	 -sudt-script-hash <sudt-script-hash>	l1 sudt script hash, default for withdrawal CKB [default: 0x0000000000000000000000000000000000000000000000000000000000000000]

```
</details>

For more information on Godwoken RPC, refer to [Godwoken Public Network](/#godwoken-public-networks).

### <code>gw-tool withdraw</code> Subcommands

|command|description|
|---|---|
|amount             |The amount of sUDT|
|capacity             |The amount of CKB to withdraw (unit: CKB)|
|config-path             |The config.toml file required for Godwoken to run|
|godwoken-rpc-url             |The RPC address of Godwoken that defaults to http://127.0.0.1:8119/|
|owner-ckb-address             |CKB address of the recipient|
|privkey-path             |A file written with the private key (hex string) which is used to pay the deposit fee|
|scripts-deployment-path             |json file path of the [script's deployment results](https://github.com/nervosnetwork/godwoken-public/blob/master/testnet/config/scripts-deploy-result.json)|
|sudt-script-hash             |The script hash of sudt on Layer 1 that defaults to 0x0000000000000000000000000000000000000000000000000000, indicating only CKB is redeemed (amount left unfilled or filled with 0)|
