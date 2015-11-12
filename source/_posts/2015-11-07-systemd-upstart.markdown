---
layout: post
title: "systemd_upstart"
date: 2015-11-07 11:13:52 +0900
comments: true
published: true
categories: 
---
NOOBSはOSのインストーラ
raspbianをインストール
Bittorrent

#upstartとsystemdの見分け方
各々、代表的なコマンドがあるかどうかで決めて良いと思います。以下、自分の環境で調べた結果をまとめます  

###How To Confirm

| system   | command          |
|--------  |--------          |
| sysVinit | cat /etc/inittab |
| upstart  | initctl          |
| systemd  | systemctl        |

###Confirmed List

|distribution|system  |
|------------|------  |
|ubuntu14,04 |upstart |
|ubuntu15.04 |systemd |
|raspbian    |sysVinit|
|CentOS6.2   |upstart |
|CentOS6.7   |upstart |
|CentOS7.1   |systemd |

##systemd

##upstart


rndcとは
nslookupとは
selinuxとは
