# History of XCM-tools execution on Moonriver

## 2022-01-06 \[Moonriver-1101\] default XCM version

Set default XCM version (we cannot use XCM otherwise). This script also sets the revert code for Xtokens and Xcm-transactor precompiles.

```
yarn initialize-xcm --ws-provider wss://wss.moonriver.moonbeam.network --default-xcm-version 2 --xcm-transactor-address "0x0000000000000000000000000000000000000806" --xtokens-address "0x0000000000000000000000000000000000000804" --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 2
```

## 2022-01-06 \[Moonriver-1101\] Open HRMP channel request to Statemine

Send a XCM message to the relay to make an open channel request to Statemine.

```
yarn hrmp-manipulator --parachain-ws-provider wss://wss.moonriver.moonbeam.network --relay-ws-provider wss://kusama-rpc.polkadot.io --hrmp-action open --max-capacity 1000 --max-message-size 102400 --target-para-id 1000 --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 2
```

## 2022-01-06 \[Kusama-9130\] Register KSM on Moonriver

Add KSM to the asset pallet from relay chain. Also add the precompile to access it through EVM.

```
yarn register-asset -w wss://wss.moonriver.moonbeam.net --asset '{ "parents": 1, "interior": "Here" }' --units-per-second 130000000000 --name "xcKSM" --sym "xcKSM" --decimals 12 --ed 1 --sufficient true --account-priv-key "<council_member_priv_key>" --revert-code true --send-preimage-hash true --send-proposal-as council-external --collective-threshold 2
```

## 2022-01-17 \[Moonriver-1102\] Accept HRMP channel from Statemine

Send a XCM message to the relay to accept channel from Statemine.

```
yarn hrmp-manipulator --parachain-ws-provider wss://wss.moonriver.moonbeam.network --relay-ws-provider wss://kusama-rpc.polkadot.io --hrmp-action accept --target-para-id 1000 --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 2
```

## 2022-01-18 \[Moonriver-1102\] Adding RMRK Asset from Statemine

Add RMRK to the asset pallet from parachain 1000. Also add the precompile to access it through EVM.

```
yarn register-asset -w wss://wss.moonriver.moonbeam.network/ --asset '{ "parents": 1, "interior": {"X2": [ { "Parachain": 1000 }, { "GeneralIndex": 8 }]}}' -u 13000000000 --name "xcRMRK" --sym "xcRMRK" -d 10 --ed 1 --sufficient true --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 2 --revert-code true
```

## 2022-02-18 \[Moonriver-1102\] Open HRMP channel request to Kintsugi

Send a XCM message to the relay to make an open channel request to Kintsugi.

```
yarn hrmp-manipulator --parachain-ws-provider wss://wss.moonriver.moonbeam.network --relay-ws-provider wss://kusama-rpc.polkadot.io --hrmp-action open --max-capacity 1000 --max-message-size 102400 --target-para-id 2092 --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 3
```

## 2022-02-18 \[Moonriver-1102\] Accept HRMP channel from Kintsugi

Send a XCM message to the relay to accept channel from Kintsugi.

```
yarn hrmp-manipulator --parachain-ws-provider wss://wss.moonriver.moonbeam.network --relay-ws-provider wss://kusama-rpc.polkadot.io --hrmp-action accept --target-para-id 2092 --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 2
```

## 2022-02-23 \[Moonriver-1102\] Adding KINT Asset from Kintsugi

Add KINT to the asset pallet from parachain 2092. Also add the precompile to access it through EVM.

```
yarn register-asset -w wss://wss.moonriver.moonbeam.network/ --asset '{ "parents": 1, "interior": {"X2": [ { "Parachain": 2092 }, { "GeneralKey": "0x000c" }]}}' -u 1056250000000 --name "Kintsugi Native Token" --sym "xcKINT" -d 12 --ed 1 --sufficient true --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 3 --revert-code true
```

## 2022-02-23 \[Moonriver-1102\] Adding KBTC Asset from Kintsugi

Add KINT to the asset pallet from parachain 2092. Also add the precompile to access it through EVM.

```
yarn register-asset -w wss://wss.moonriver.moonbeam.network/ --asset '{ "parents": 1, "interior": {"X2": [ { "Parachain": 2092 }, { "GeneralKey": "0x000b" }]}}' --name "Kintsugi Wrapped BTC" --sym "xcKBTC" -d 8 --ed 1 --sufficient true --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 3 --revert-code true
```

## 2022-03-03 \[Moonriver-1300\] Open HRMP channel request to Karura

Send a XCM message to the relay to make an open channel request to Karura.

```
yarn hrmp-manipulator --parachain-ws-provider wss://wss.moonriver.moonbeam.network --relay-ws-provider wss://kusama-rpc.polkadot.io --hrmp-action open --max-capacity 1000 --max-message-size 102400 --target-para-id 2000 --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 3
```

## 2022-03-03 \[Moonriver-1300\] Accept HRMP channel from Karura

Send a XCM message to the relay to accept channel from Karura.

```
yarn hrmp-manipulator --parachain-ws-provider wss://wss.moonriver.moonbeam.network --relay-ws-provider wss://kusama-rpc.polkadot.io --hrmp-action accept --target-para-id 2000 --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 3
```

## 2022-03-03 \[Moonriver-1300\] Adding KAR Asset from Karura

Add KAR to the asset pallet from parachain 2000. Also add the precompile to access it through EVM.

```
yarn register-asset -w wss://wss.moonriver.moonbeam.network/ --asset '{ "parents": 1, "interior": {"X2": [ { "Parachain": 2000 }, { "GeneralKey": "0x0080" }]}}' -u 12350000000000 --name "Karura" --sym "xcKAR" -d 12 --ed 1 --sufficient true --account-priv-key "<council_member_priv_key>" --send-preimage-hash true --send-proposal-as council-external -c 3 --revert-code true
```

## 2022-03-14 \[Moonriver-1300\] Open HRMP channel request to Bifrost

Send a XCM message to the relay to make an open channel request to Bifrost.

```
yarn hrmp-manipulator --parachain-ws-provider wss://wss.moonriver.moonbeam.network --relay-ws-provider wss://kusama-rpc.polkadot.io --hrmp-action open --max-capacity 1000 --max-message-size 102400 --target-para-id 2001 --account-priv-key "<priv_key>" --send-preimage-hash true --send-proposal-as democracy
```

## 2022-03-14 \[Moonriver-1300\] Adding BNC Asset from Bifrost

Add BNC to the asset pallet from parachain 2001. Also add the precompile to access it through EVM.

```
yarn register-asset -w wss://wss.moonriver.moonbeam.network/ --asset '{ "parents": 1, "interior": {"X2": [ { "Parachain": 2001 }, { "GeneralKey": "0x0001" }]}}' -u 35230000000000 --name "xcBNC" --sym "xcBNC" -d 12 --ed 1 --sufficient true --account-priv-key "<priv_key>" --send-preimage-hash true --send-proposal-as democracy --revert-code true
```

## 2022-04-06 \[Moonriver-1300\] Open/Accept HRMP channel request to/from Shadow (Crust), Register CSM asset

Sends a batched proposal to Open/Accept HRMP channel to/from Shadow (Crust), it also register CSM as an XC-20

```
yarn generic-call-propose -w wss://wss.moonriver.moonbeam.network/  --call "0x67000101000210000400000000070010a5d4e81300000000070010a5d4e8010700f2052a01060002286bee383c00dc070000e8030000009001000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x67000101000210000400000000070010a5d4e81300000000070010a5d4e8010700f2052a01060002286bee183c01dc0700000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x690000010100711f64437275737420536861646f77204e617469766520546f6b656e14786343534d0c000100000000000000000000000000000001" --call "0x690100010100711f0088d54781480400000000000000000005000000" --call "0x00050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181abc7aca49466b2e4f57b79c214866260bffffffff519811215e05efa24830eebe9c43acd7181460006000fd" --account-priv-key "<priv_key>" --send-preimage-hash true
```

## 2022-04-08 \[Moonriver-1300\] Adding aUSD Asset from Karura

Add aUSD to the asset pallet from parachain 2000. Also add the precompile to access it through EVM.

```
yarn register-asset -w wss://wss.moonriver.moonbeam.network/ --asset '{ "parents": 1, "interior": {"X2": [ { "Parachain": 2000 }, { "GeneralKey": "0x0081" }]}}' --name "Acala Dollar" --sym "xcAUSD" -d 12 --ed 1 --sufficient true --account-priv-key "<priv_key>" --send-preimage-hash true --revert-code true
```

## 2022-04-11 \[Moonriver-1300\] Accept HRMP channel request from Bifrost

Send a XCM message to the relay to accept channel from Bifrost.

```
yarn hrmp-manipulator --parachain-ws-provider wss://wss.moonriver.moonbeam.network --relay-ws-provider wss://kusama-rpc.polkadot.io --hrmp-action accept --target-para-id 2001 --account-priv-key "<priv_key>" --send-preimage-hash true
```

## 2022-04-13 \[Moonriver-1300\] Adds aUSD as Fee Token

Add aUSD as a fee token to pay for XCM execution on Moonriver.

```
yarn generic-call-propose -w wss://wss.moonriver.moonbeam.network/ --call "0x690100010200411f0608008100ec019ccc120000000000000000000007000000" --account-priv-key "<priv_key>" --send-preimage-hash true
```

## 2022-04-19 \[Moonriver-1401\] Adding USDT Asset from Statemine

Add USDT to the asset pallet from parachain 1000. Also add the precompile to access it through EVM.

```
yarn register-asset -w wss://wss.api.moonriver.moonbeam.network/ --asset '{ "parents": 1, "interior": {"X3": [ { "Parachain": 1000 }, {"PalletInstance": 50}, { "GeneralIndex": 1984 }]}}' -u 25000000 --name "Tether USD" --sym "xcUSDT" -d 6 --ed 1 --sufficient true --account-priv-key "<priv_key>" --send-preimage-hash true --revert-code true
```

## 2022-04-20 \[Moonriver-1401\] Open/Accept HRMP channel request to/from Khala, Register PHA asset

Sends a batched proposal to Open/Accept HRMP channel to/from Khala, it also register PHA as an XC-20

```
yarn generic-call-propose -w wss://wss.moonriver.moonbeam.network/  --call "0x67000101000210000400000000070010a5d4e81300000000070010a5d4e8010700f2052a01060002286bee183c01d40700000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x67000101000210000400000000070010a5d4e81300000000070010a5d4e8010700f2052a01060002286bee383c00d4070000e8030000009001000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x690000010100511f2c5068616c6120546f6b656e1478635048410c000100000000000000000000000000000001" --call "0x690100010100511f00fc299eb7420000000000000000000011000000" --call "0x00050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181a733349a86c9e5369cf9458d31b5d3301ffffffff8e6b63d9e447b6d4c45bda8af9dc9603181460006000fd" --account-priv-key  "<priv_key>" --send-preimage-hash true
```

## 2022-04-25 \[Moonriver-1401\] Set new transactInfo for release v0.9.19

Sets new transact info after 0.9.19 release in Moonriver

```
yarn set-transact-info --ws-provider wss://wss.api.moonriver.moonbeam.network  --destination  '{ "parents": 1, "interior": "Here" }' --fee-per-second  41485177350 --extra-weight 3000000000 --max-weight 20000000000 --send-preimage-hash true --account-priv-key "<priv_key>"
```

=======
## 2022-05-16 \[Moonriver-1502\] Open/Accept HRMP channel request to/from Calamari, Register KMA asset

Sends a batched proposal to Open/Accept HRMP channel to/from Calamari, it also register KMA as an XC-20

```
yarn generic-call-propose -w wss://wss.moonriver.moonbeam.network/  --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee183c01240800000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee383c0024080000e8030000009001000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x1e020c69000001010091202043616c616d6172691478634b4d410c0001000000000000000000000000000000016901000101009120aba8cdcf29b9670000000000000000001300000000050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181a9663dacd60a0781792df8466393c1106ffffffffa083189f870640b141ae1e882c2b5bad181460006000fd" --account-priv-key "<priv_key>" --send-preimage-hash true --send-proposal-as democracy
```

## 2022-05-17 \[Moonriver-1502\] Open/Accept HRMP channel request to/from Heiko, Register HKO asset

Sends a batched proposal to Open/Accept HRMP channel to/from Heiko, it also register HKO as an XC-20

```
yarn generic-call-propose -w wss://wss.moonriver.moonbeam.network/  --call "0x670001010002100004000000000700e40b540213000000000700e40b5402010700f2052a01060002286bee183c01250800000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x670001010002100004000000000700e40b540213000000000700e40b5402010700f2052a01060002286bee383c0025080000e8030000009001000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x1e020c6900000102009520060c484b4f0c484b4f147863484b4f0c0001000000000000000000000000000000016901000102009520060c484b4fb6cdd5800c2c030000000000000000001300000000050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181a555827465153c27bd1cb4ecb05bd36cdffffffff394054bcda1902b6a6436840435655a3181460006000fd" --account-priv-key  "<priv_key>" --send-preimage-hash true
```

## 2022-05-24 \[Moonriver-1502\] Open/Accept HRMP channel request to/from Crab, Register CRAB asset

Sends a batched proposal to Open/Accept HRMP channel to/from Crab, it also register CRAB as an XC-20

```
yarn generic-call-propose -w wss://wss.moonriver.moonbeam.network/  --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee183c01390800000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee383c0039080000e8030000009001000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x1e020c690000010200e520040550437261622050617261636861696e20546f6b656e1878634352414212000100000000000000000000000000000001690100010200e5200405497df38cb33960f51d030000000000001500000000050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181a04b9ee56f293441166ad0f2a4968c8ceffffffff8283448b3cb519ca4732f2dddc6a6165181460006000fd" --account-priv-key  "<priv_key>" --send-preimage-hash true --send-proposal-as democracy
```

## 2022-06-07 \[Moonriver-1504\] Open/Accept HRMP channel request to/from Integritee, Register TEER asset

Sends a batched proposal to Open/Accept HRMP channel to/from Integritee, it also register TEER as an XC-20

```
yarn generic-call-propose -w wss://wss.moonriver.moonbeam.network/  --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee183c01df0700000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee383c00df070000e8030000009001000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x1e020c6900000102007d1f0610544545521054454552187863544545520c0001000000000000000000000000000000016901000102007d1f0610544545524118eacdaf1e000000000000000000001600000000050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181afe8e0cac0d77ebd88a476097da34fe0dffffffff4f0cd46769550e5938f6bee2f5d4ef1e181460006000fd" --account-priv-key  "<priv_key>" --send-preimage-hash true --send-proposal-as democracy
```

## 2022-07-08 \[Moonriver-1606\] Open/Accept HRMP channel request to/from Shiden, Register SDN asset

Sends a batched proposal to Open/Accept HRMP channel to/from Shiden, it also register SDN as an XC-20

```
yarn generic-call-propose -w wss://wss.moonriver.moonbeam.network/  --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee183c01d70700000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee383c00d7070000e8030000009001000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x1e020c6900000101005d1f1853686964656e14786353444e120001000000000000000000000000000000016901000101005d1f9f732c79e022c54e04000000000000001700000000050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181a43978d284fa908a0e6d41980ebc91eefffffffff0ca324c842330521525e7de111f38972181460006000fd" --account-priv-key  "<priv_key>" --send-preimage-hash true --send-proposal-as democracy
```

## 2022-07-12 \[Moonriver-1606\] Open/Accept HRMP channel request to/from Litmus, Register LIT asset

Sends a batched proposal to Open/Accept HRMP channel to/from Litmus, it also register LIT as an XC-20

```
yarn generic-call-propose -w wss://wss.api.moonriver.moonbeam.network  --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee183c013a0800000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee383c003a080000e8030000009001000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x1e020c690000010200e920040a0c4c49541478634c49540c000100000000000000000000000000000001690100010200e920040a561f97532b1d000000000000000000001700000000050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181a7531184daa3618dec44ebb040b8ef3dbffffffff31103d490325bb0a8e40ef62e2f614c0181460006000fd" --account-priv-key "<priv_key>" --send-preimage-hash true --send-proposal-as democracy
```

# 2022-08-25 \[Moonriver-1701\] Update Units Per Second for all XC-20s

Sends a batched proposal to update the UnitsPerSecond for all XC-20s to target $0.02 as of 2022.08.24

```
yarn generic-call-propose -w wss://wss.api.moonriver.moonbeam.network/  --call "0x1e02406901000100fdce301577000000000000000000000019000000690100010200411f06080080f92faf2f142d0000000000000000000019000000690100010200411f0608008100901ec4bc160000000000000000000019000000690100010100511f92d1191d14d40000000000000000000019000000690100010200b1200608000c4e00fb71ee0a0000000000000000000019000000690100010200b1200608000b93c9010000000000000000000000000019000000690100010200451f0608000104b5bed076770000000000000000000019000000690100010100711fe7233270a71e0a00000000000000000019000000690100010300a10f043205011f40787d0100000000000000000000000019000000690100010300a10f043205208097b013120000000000000000000000190000006901000102009520060c484b4ffecc9828f5aa00000000000000000000190000006901000102007d1f06105445455219ec556e13210000000000000000000019000000690100010200e5200405ea84f51fef7d29b08e05000000000000190000006901000101009120978b3c56269b30000000000000000000190000006901000101005d1fc2c26aebeb157d6a040000000000000019000000690100010200e920040a023ace9a771d0000000000000000000019000000 " --account-priv-key  "<priv_key>" --send-preimage-hash true --send-proposal-as democracy
```

# 2022-11-?? \[Moonriver-1901\] Open/Accept HRMP channel request to/from BitCountry Pioneer, Register NEER asset, Register BIT asset

Sends a batched proposal to Open/Accept HRMP channel to/from BitCountry Pioneer, it also register NEER & BIT as XC-20s

```
yarn generic-call-propose -w wss://moonriver.public.blastapi.io  --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee183c01300800000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x670001010002100004000000000700e876481713000000000700e8764817010700f2052a01060002286bee383c0030080000e8030000009001000d0100040001010070617261e7070000000000000000000000000000000000000000000000000000" --call "0x1e020c690000010200c1200624000000000000000000104e4545521878634e45455212000100000000000000000000000000000001690100010200c1200624000000000000000000c7a8978b008d871601000000000000001b00000000050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181ad47cf8e85c6fd3253f06000547abbd10ffffffff2754f0bdf7eb215503c69204ccd61c5d181460006000fd" --call "0x1e0208690000010200c12006240200000000000000000c4249541478634249541200010000000000000000000000000000000100050411011da53b775b270400e7e61ed5cbc5a146ea70f53d5a3306ce02aaf97049cf181a015d45f2e02e131f22f5ff3938dc9f3effffffffe6b08aa1fbbaa02f004d3e5aa27f3bad181460006000fd" --account-priv-key <priv_key> --send-preimage-hash true --send-proposal-as democracy
```