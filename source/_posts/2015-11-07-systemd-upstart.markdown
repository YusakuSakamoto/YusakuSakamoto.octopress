---
layout: post
title: "initシステム"
date: 2015-11-07 11:13:52 +0900
comments: true
published: true
categories: 
---
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
ubuntu14.10からsystemdの導入が決定し、CentOS7もsystemdに移行しているので、時代のトレンド的にSystemdが流行り出しているのかな、とか勝手に思っていますが、要するにsysVinitは依存関係上の処理が止まると全てのサービスの起動が停滞してしまう、という欠点があり、それが起動の遅延を引き起こしていましたが、systemdはサービスの起動を並列的に処理してくれるので結果的に起動が速くなります。

注意ですが、`sysctl`コマンドはカーネルのパラメータを操作するときのコマンドであり、systemdのコマンドではありません。
[Systemd関連記事](http://equj65.net/tech/systemd-boot/)  
[systemdを本番運用してわかったこと](http://alpha.mixi.co.jp/entry/2013/12063/)
##upstart
Upstartもsystemdと同じような働きをしており、過去多くのLinux distributionで利用されてきましたが、今はUpstartよりも多機能で膨大な働きができるSystemdの方が主流となっているようです。しかしながらUbuntu14.04LTSではUpstartが採用されていますので、現在のところどちらも使えるようになっておく必要があります(私の場合ですが)。

#起動スクリプトの考え方は変わらない
起動スクリプトの考え方、つまりは、CentOS6における、`/etc/init.d/* start`みたいな使い方には変化しないようです。systemdではsystemctlを使用するか`service サービス名`という使い方をします。
