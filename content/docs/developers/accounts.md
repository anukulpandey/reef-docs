---
title: "Accounts"
description: "Reef chain accounts"
lead: "Reef chain accounts"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "developers"
weight: 230
toc: true
---

## Generate a keypair
You can create a new random mnemonic and corresponding SR25519 keypair with `reef-node key generate`:

```
./reef-node key generate --words 12
Secret phrase `any member stadium combine company grass jar wood brown second blame rocket` is account:
  Secret seed:      0xf087a7ebb71070624fede0758ed46facf24eddef78e2c4a96e3d0e6ee934472a
  Public key (hex): 0xf47813a285f917a3c2a3eae00d94f1158761ad5105261e98bceb050ad8871638
  Account ID:       0xf47813a285f917a3c2a3eae00d94f1158761ad5105261e98bceb050ad8871638
  SS58 Address:     5HbFDCvjGmG2VRae2KN6kkYbYaspfdGb5n7LtZf1FfqvNrDt
```

The mnemonic can be used to also obtain ED25519 or ECDSA keypairs:
```
./reef-node key inspect-key --scheme Ed25519 \
  "any member stadium combine company grass jar wood brown second blame rocket"
Secret phrase `any member stadium combine company grass jar wood brown second blame rocket` is account:
  Secret seed:      0xf087a7ebb71070624fede0758ed46facf24eddef78e2c4a96e3d0e6ee934472a
  Public key (hex): 0x4457741669d11953becab1e7ec348eef0885db824dfc92cd3bc06b3efb167071
  Account ID:       0x4457741669d11953becab1e7ec348eef0885db824dfc92cd3bc06b3efb167071
  SS58 Address:     5DcK6KBAdwXeGuz5zKRPfkz1gT5bK4LRCWtFxhWqNwNVgKvL
```


Output ECDSA keypair as JSON:
```
./reef-node key inspect-key --scheme Ecdsa --output-type json \
  "any member stadium combine company grass jar wood brown second blame rocket"
{
  "accountId": "0xdb086ba0c8d331a52049f1ae5f47552a15cb11554b4c5f1950bdb6ad9b538fed",
  "publicKey": "0x02fda19338fc1bb08a2bd1437c7b5364b429d09f57968344f39bf5574f79c9d0a5",
  "secretPhrase": "any member stadium combine company grass jar wood brown second blame rocket",
  "secretSeed": "0xf087a7ebb71070624fede0758ed46facf24eddef78e2c4a96e3d0e6ee934472a",
  "ss58Address": "5H1tqyqYgBhYky3rMwjwmR9uNrBMrm45EaF8c9UQoxuVAmRA"
}
```

## EVM Account
Each Reef chain account (SR25519) also has