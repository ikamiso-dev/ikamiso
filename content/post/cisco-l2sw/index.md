---
title: cisco L2SW　研修用コマンド
description: ciscoのL2SWの研修で登場したコマンド
slug: cisco-l2sw
date: 2026-04-09 20:00:00+0900
categories:
    - ネットワーク
tags:
    - cisco
---

## 特権パスワード設定（暗号化）

```
(config)#enable secret <パスワード>
```

## ホスト名設定

```
(config)#hostname <ホスト名>
```

## 管理IP付与

```
(config)#interface vlan 20
(config-if)#no shutdown
(config-if)#ip address <ipアドレス> <サブネットマスク>
(config-if)#exit
```

## VTY設定（SSH有効/TELNET無効）

```
(config)#line vty 0 15
(config-line)#transport input ssh
(config-line)#login local
(config-line)#exit
```

## HTTP(S)無効化

```
(config)#no ip http server
(config)#no ip http secure-server
```

## LAG設定（EtherChannel）

```
(config)#interface range gigabitEthernet 0/1-2
(config-if-range)#channel-group <番号> mode active
(config-if-range)#exit
```

## STP設定

```
(config)#spanning-tree mode rapid-pvst
(config)#spanning-tree vlan <番号> priority <priority値4096単位>
```

## VLAN作成

```
(config)#vlan <番号>
(config-vlan)#name <VLAN名>
(config-vlan)#exit
```

## アクセスポート

```
(config)#interface range <IF名>-<IF名>
(config-if-range)#switchport mode access
(config-if-range)#switchport access vlan <番号>
(config-if-range)#exit
```

## トランクポート

```
(config)#interface <IF名>
(config-if)#switchport mode trunk
(config-if)#switchport trunk allowed vlan <番号>,<番号>,<番号>
(config-if-range)#exit
```

## ポートチャンネル

```
(config)# interface port-channel 1
(config-if)#switchport mode trunk
(config-if)#switchport trunk allowed vlan <番号>,<番号>,<番号>
(config-if-range)#exit
```

## NTP設定

```
(config)#ntp server <ntpサーバのipアドレス>
```

## Timezone設定

```
(config)#clock timezone JST 9 0
```
## ログバッファ設定

```
(config)#logging buffered <バッファサイズ>
```

## ドメイン　DNSサーバ設定

```
(config)#ip domain name <ドメイン名>
(config)#ip name-server <dnsサーバのipアドレス>
```

## SSH
rsa鍵を生成する前に、ホスト名とドメイン名を設定しておく必要があるよ。
鍵のラベルにFQDN(ホスト名+ドメイン名)を使用するかららしい。

```
(config)#hostname <ホスト名>
(config)#ip domain name <ドメイン名>
(config)#username <ユーザ名> secret <パスワード>
(config)#crypto key generate rsa modulus 1024
(config)#ip ssh version 2
```

## スタティックルート
本当のL2SWにこのコマンドはないよ。L3SWをL2SWとしてつかうときは、デフォルトゲートウェイの設定をこのコマンドでしてもいいらしい。

```
(config)#ip route <宛先> <サブネットマスク> <ネクストホップ>
```