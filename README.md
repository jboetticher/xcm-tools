# xcm-tools
A set if scripts to help XCM initialization, asset registration and chanel set up
## Install dependencies
From this directory

`yarn install`

## register-asset script
Scipt that allows to register an asset in a moonbeam runtime. It particulary does three things:

- Registers the asset
- Sets the asset units per second to be charged
- Sets the revert code in the asset precompile

The script accepts these inputs fields:
- `--ws-provider or -w`, which specifies the websocket provider to which we will be issuing our requests
- `--asset or -a`, the MultiLocation identifier of the asset to be registered
- `--units-per-second or -u`, optional, specifies how much we should charge per second of execution in the registered asset.
- `--name or -n`, the name of the asset
- `--symbol or --sym`, the symbol of the asset
- `--decimals or -d`, the number of decimals of the asset
- `--existential-deposit or --ed`, the existential deposit of the registered asset
- `--sufficient or --suf`, boolean indicating whether the asset should exist without a provider reference
- `--revert-code or --revert`, boolean specifying whether we want register the revert code in the evm
- `--account-priv-key or -a`, which specifies the account that will submit the proposal
- `--send-preimage-hash or -h`, boolean specifying whether we want to send the preimage hash
- `--send-proposal or -s`, optional, but if providede needs to be "democracy" or "council-external" specifying whether we want to send the proposal through regular democracy or as an external proposal that will be voted by the council
- `--collective-threshold or -c`, Optional, number specifying the number of council votes that need to aprove the proposal. If not provided defautls to 1.

### Example to note Pre-Image and propose
`yarn register-asset -w ws://127.0.0.1:34102  --asset  '{ "parents": 1, "interior": "Here" }' -u 1 --name "DOT" --sym "DOT" -d 12 --ed 1 --sufficient true --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h true -s democracy --revert-code true`

### Example to note Pre-Image and propose through council
`yarn register-asset -w ws://127.0.0.1:34102  --asset  '{ "parents": 1, "interior": "Here" }' -u 1 --name "Parent" --sym "DOT" -d 12 --ed 1 --sufficient true --account-priv-key "0x8075991ce870b93a8870eca0c0f91913d12f47948ca0fd25b49c6fa7cdbeee8b" -h true -s council-external -c 2`

## xcm-initializer script
Scipt that allows to initialize xcm in a moonbeam runtime. It particularly does:

- Sets the default xcm version to be used if we dont know the version supported by the other end
- Sets the revert code in the xtokens precomipe
- Sets the revert code in the xcm-transactor precompile

The script accepts these inputs fields:
- `--ws-provider or -w`, which specifies the websocket provider to which we will be issuing our requests
- `--default-xcm-version or -d`, optional, provides the new default xcm version we want to set
- `--xtokens-address or --xt`, optional, if provided, it will set the revert code at that address.
- `--xcm-transactor-address or --xcmt`, optional, if provided, it will set the revert code at that address.
- `--account-priv-key or -a`, which specifies the account that will submit the proposal
- `--send-preimage-hash or -h`, boolean specifying whether we want to send the preimage hash
- `--send-proposal or -s`, optional, but if providede needs to be "democracy" or "council-external" specifying whether we want to send the proposal through regular democracy or as an external proposal that will be voted by the council
- `--collective-threshold or -c`, Optional, number specifying the number of council votes that need to aprove the proposal. If not provided defautls to 1.

### Example to note Pre-Image and propose
`yarn initialize-xcm -w ws://127.0.0.1:34102  --default-xcm-version 2 --xcm-transactor-address "0x0000000000000000000000000000000000000806" --xtokens-address "0x0000000000000000000000000000000000000804" --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h true -s democracy`

### Example to note Pre-Image and propose through council
`yarn initialize-xcm -w ws://127.0.0.1:34102  --default-xcm-version 2 --xcm-transactor-address "0x0000000000000000000000000000000000000806" --xtokens-address "0x0000000000000000000000000000000000000804" --account-priv-key "0x8075991ce870b93a8870eca0c0f91913d12f47948ca0fd25b49c6fa7cdbeee8b" -h true -s council-external -c 2`

## hrmp-manipulator script
Scipt that allows to initiate an HRMP action in the relay from the parachain. In particular, the script allows to open a channel, accept an existing open channel request, cancel an existing open channel request, or closing an existing HRMP channel.

The script accepts these inputs fields:
- `--parachain-ws-provider or --wp`, which specifies the parachain websocket provider to which we will be issuing our requests
- `--relay-ws-provider or --wr`, which specifies the relay websocket provider to which we will be issuing our requests
- `--hrmp-action or --hrmp`, one of "accept", "close", "cancel", or "open".
- `--target-para-id or -p`, The target paraId with which we interact.
- `--max-capacity or --mc`, Optional, only for "open". The max capacity in messages that the channel supports.
- `--max-message-size or -mms`, Optional, only for "open". The max message size that the channel supports.
- `--account-priv-key or -a`, which specifies the account that will submit the proposal
- `--send-preimage-hash or -h`, boolean specifying whether we want to send the preimage hash
- `--send-proposal or -s`, optional, but if providede needs to be "democracy" or "council-external" specifying whether we want to send the proposal through regular democracy or as an external proposal that will be voted by the council
- `--collective-threshold or -c`, Optional, number specifying the number of council votes that need to aprove the proposal. If not provided defautls to 1.

### Example to note Pre-Image and propose
`yarn hrmp-manipulator --wp ws://127.0.0.1:34102  --relay-ws-provider ws://127.0.0.1:34002 --hrmp-action accept --target-para-id 2003 --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h true -s democracy`

### Example to note Pre-Image and propose through council
`yarn hrmp-manipulator --wp ws://127.0.0.1:34102  --relay-ws-provider ws://127.0.0.1:34002 --hrmp-action accept --target-para-id 2003 --account-priv-key "0x8075991ce870b93a8870eca0c0f91913d12f47948ca0fd25b49c6fa7cdbeee8b" -h true  -s council-external -c 2`

`yarn hrmp-manipulator --wp ws://127.0.0.1:34102  --relay-ws-provider ws://127.0.0.1:34002 --hrmp-action open --target-para-id 2003 --mc 8 --mms 512 --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h true -s democracy`

## xcm-transactor-info-setter script
Scipt that allows to set the transactor info in the xcm-transactor pallet. For a given chain, this allows to set:

- The amount of extra weight involved in the transact operations
- The amount of fee the chain charges per weight unit.

The script accepts these inputs fields:
- `--ws-provider or -w`, which specifies the websocket provider to which we will be issuing our requests
- `--destination or --d`, the MultiLocation identifier of the destination for which to set the transact info
- `--fee-per-weight or --fw`, the amount of fee the destination will charge per weight
- `--extra-weight or --ew`, the amount of extra weight that sending the transact xcm message involves
- `--account-priv-key or -a`, which specifies the account that will submit the proposal
- `--send-preimage-hash or -h`, boolean specifying whether we want to send the preimage hash
- `--send-proposal or -s`, optional, but if providede needs to be "democracy" or "council-external" specifying whether we want to send the proposal through regular democracy or as an external proposal that will be voted by the council
- `--collective-threshold or -c`, Optional, number specifying the number of council votes that need to aprove the proposal. If not provided defautls to 1.

### Example to note Pre-Image and propose
`yarn set-transact-info -w ws://127.0.0.1:34102  --destination  '{ "parents": 1, "interior": "Here" }' --fee-per-weight 8 --extra-weight 3000000000 --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h true -s democracy`

### Example to note Pre-Image and propose through council
`yarn set-transact-info -w ws://127.0.0.1:34102  --destination  '{ "parents": 1, "interior": "Here" }' --fee-per-weight 8 --extra-weight 3000000000 --account-priv-key "0x8075991ce870b93a8870eca0c0f91913d12f47948ca0fd25b49c6fa7cdbeee8b" -h true -s council-external -c 2`

## xcm-derivative-index-registrator script
Scipt that allows to register a parachain account for a derivative index usage in a sovereign account. This will allows the parachain account to issue transact commands to a derivative index of the sovereign account

The script accepts these inputs fields:
- `--ws-provider or -w`, which specifies the websocket provider to which we will be issuing our requests
- `--owner or --o`, the parachain account that will own the derivative index
- `--index or --i`, the index that the owner will own
- `--account-priv-key or -a`, which specifies the account that will submit the proposal
- `--send-preimage-hash or -h`, boolean specifying whether we want to send the preimage hash
- `--send-proposal or -s`, optional, but if providede needs to be "democracy" or "council-external" specifying whether we want to send the proposal through regular democracy or as an external proposal that will be voted by the council
- `--collective-threshold or -c`, Optional, number specifying the number of council votes that need to aprove the proposal. If not provided defautls to 1.

### Example to note Pre-Image and propose
`yarn register-derivative-index -w ws://127.0.0.1:34102  --index  0 --owner "0xf24FF3a9CF04c71Dbc94D0b566f7A27B94566cac" --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h true -s democracy`

### Example to note Pre-Image and propose through council
`yarn register-derivative-index -w ws://127.0.0.1:34102  --index  0 --owner "0xf24FF3a9CF04c71Dbc94D0b566f7A27B94566cac" --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h true -s council-external -c 2`


## statemint-hrmp-relay-proposal-generator script
Scipt that allows to build and send the relay call necessary to make statemine accept an already open channel request target-para-id -> statemine and open a new one in the opposite direction. This is meant to be proposed/executed in the relay.

The script accepts these inputs fields:
- `--statemint-ws-provider or -ws`, which specifies the statemint websocket provider
- `--relay-ws-provider or --wr`, which specifies the relay websocket -provider
- `--target-para-id or -p`, The target paraId to which the proposal from statemint will be sent.
- `--max-capacity or --mc`, The max capacity in messages that the channel supports.
- `--max-message-size or --mms`, The max message size that the channel supports.
- `--send-deposit-from or -s`, where the deposit of KSM to statemint sovereign account will be made.  one of "sovereign" or "external-account".
- `--external--account or -e`, Optional, only for "external-account" choices in the previous argument. The account from which we will send the KSM
- `--account-priv-key or -a`, which specifies the account that will submit the preimage
- `--send-preimage-hash or -h`, boolean specifying whether we want to send the preimage hash

### Example to note Pre-Image with external account

` yarn statemint-hrmp-propose --ws wss://statemine-rpc.polkadot.io  --relay-ws-provider wss://kusama-rpc.polkadot.io --target-para-id 2000 --mc 1000 --mms 102400 --send-deposit-from "external-account" --external-account 0x6d6f646c70792f74727372790000000000000000000000000000000000000000  --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h true`

### Example to note Pre-Image with sovereign

` yarn statemint-hrmp-propose --ws wss://statemine-rpc.polkadot.io  --relay-ws-provider wss://kusama-rpc.polkadot.io --target-para-id 2000 --mc 1000 --mms 102400 --send-deposit-from "sovereign"  --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h true`

### Example to send sudo as call with external account

` yarn statemint-hrmp-propose --ws wss://statemine-rpc.polkadot.io  --relay-ws-provider wss://kusama-rpc.polkadot.io --target-para-id 2000 --mc 1000 --mms 102400 --send-deposit-from "external-account" --external-account 0x6d6f646c70792f74727372790000000000000000000000000000000000000000  --account-priv-key "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133" -h false -s sudo`