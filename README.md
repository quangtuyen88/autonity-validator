# Autonity validator node.

## Step One
```
User root user
cd ~
git clone https://github.com/quangtuyen88/autonity-validator.git
cd autonity-validator
./tools/install_requirements_ubuntu.sh && ./tools/generate_env_passwords && ./tools/start_autonity &&  ./tools/setup_shell_environment && source ~/.bashrc && ./tools/node_add_peers_piccadilly && ./tools/generate_oracle_key && ./tools/generate_account main
```

## Step Two (form 1)
### Open form.(faucet registratuin)  https://game.autonity.org/getting-started/register.html

`Address:`
```
cat .data/.autonity/main.public
```
`Signature:`
```
./tools/validator_create_faucet_signature
```

`wait 5 minutes for token delivery`

### TopUp Oracle balance
```
./tools/topup_oracle_balance 0.1
```

### Register validator
1. Run command `register`

```
./tools/validator_register main
```
   
Here your validator id:
![image](https://github.com/web3cdnservices/autonity-validator-toolkit/assets/115787312/1bec3c07-cbea-4cfc-bf6d-f74aae5eb22f)


3. Run command `bound`
   ```
   ./tools/validator_bound_tokens
   ```
Paste here your validatorId.
& password.

## step Three form confirmation.

Import Nodekey with command:
```
./tools/validator_import_nodekey
```

### Open form https://game.autonity.org/awards/register-validator.html

- Enode:  
```
aut node info | jq -r ".admin_enode"
```

- Signature of message validator onboarded:
```
./tools/validator_create_validator_conformation_signature
```


## Configure APIs for Oracle. (obrain keys)
`Process registration in services and save api keys`
- `https://currencyfreaks.com`
- `https://openexchangerates.org`
- `https://currencylayer.com`
- `https://www.exchangerate-api.com`

Open nano and edit configuration file. Uncomment blocks and paste API keys.

```
nano .data/autonity_oracle/plugins-conf.yml

```


`PS: save is Ctrl+X`
