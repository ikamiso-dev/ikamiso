---
title: プライベートIPアドレス
description: 
slug: private-ip
date: 2026-04-15 00:00:00+0900
categories:
    - ネットワーク
tags:
    - プライベートIPアドレス
---

## プライベートIPアドレスとは

プライベートなネットワークで使用するIPアドレス

RFC1918に公式の定義が書いてあります。
https://datatracker.ietf.org/doc/html/rfc1918

    The Internet Assigned Numbers Authority (IANA) has reserved the following three blocks of the IP address space for private internets:
    (IANAは、プライベートインターネット用に下記の3つのIPアドレス空間のブロックを予約しています。)

    10.0.0.0        -   10.255.255.255  (10/8 prefix)
    172.16.0.0      -   172.31.255.255  (172.16/12 prefix)
    192.168.0.0     -   192.168.255.255 (192.168/16 prefix)

10/8 prefix とは

IPアドレスを2進数で考えたとき、先頭8bitが10（2進数で00001000）のものという意味です。プレフィックスとかサブネットマスクが出てきたときは、2進数で考えます。

    00001010.xxxxxxxx.xxxxxxxx.xxxxxxxx

※ 先頭8bitが固定

xxxxは自由にきめていいところです。

同様に 172.16/12 は

    10101100.0001xxxx.xxxxxxxx.xxxxxxxx

※ 先頭12bitが固定(10進数だと172.16〜172.31になる)

192.168.0.0/16 は

    11000000.10101000.xxxxxxxx.xxxxxxxx

※ 先頭16bitが固定

## これを覚えておけばいい

10\.  
172.16.  
172.17.  
172.18.  
172.19.  
172.20.  
172.21.  
172.22.  
172.23.  
172.24.  
172.25.  
172.26.  
172.27.  
172.28.  
172.29.  
172.30.  
172.31.  
192.168.  

から始まるのはプライベートIPアドレス