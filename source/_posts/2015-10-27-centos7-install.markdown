---
layout: post
title: "CentOS7のインストール"
date: 2015-10-27 05:49:08 +0900
comments: true
categories: CentOS7
---
![logo](http://mireiasangalo.com/wp-content/uploads/2013/09/centos-splash.png)
![centos](/images/centos7.png)

#基本の知識
CentOSは、Red Hat系linuxであり、RHELの完全互換を目指した無料のlinux distributionである。  
  
ROSでdistroという言葉が出てきていましたが、distro = distributionだそうです。もちろん、debianではないので**aptは使えません。**では、その代わりに何があるのかというと、yum(Yellowdog Updater Modified)というメタパッケージ管理システムが用意されています。  
  
しかし、デフォルトの状態であれば、入れることができるアプリケーションは非常に限定的であり、レポジトリを新たに追加するという人が多いようです。  
  
管理ファイルは、/etc/yum.repos.dのレポジトリ。  
ここに.repoファイルを作成すればいいようです。  

##yumのレポジトリを確認する

`
yum repolist
`
  
私の環境(入れたばかり)の状況では、以下のものが出ました。
```
読み込んだプラグイン:fastestmirror, langpacks
Determining fastest mirrors
 * base: ftp.iij.ad.jp
 * extras: ftp.iij.ad.jp
 * updates: ftp.iij.ad.jp
リポジトリー ID                  リポジトリー名                      状態
base/7/x86_64                    CentOS-7 - Base                     8,652
extras/7/x86_64                  CentOS-7 - Extras                     236
updates/7/x86_64                 CentOS-7 - Updates                  1,531
repolist: 10,419
```

##レポジトリの説明
私はなんの気無しにiijというミラーサイトのOSをダウンロードして入れてみましたが、iijとはおそらく(internet initiative japan)の会社のことです。日本の会社であるので、もうあらかたの日本語環境は導入済みなようです。ここでは、予めOSのイメージを作成した際に、これは絶対に必要だと判断されたもののパッケージがbase,extras,updatesというレポジトリとして存在しています。  

では、yumにレポジトリの追加をしていきます。とりあえず、以下の３種類のものをとりあえず入れたら?みたいな感じで様々なサイトに記載していましたので、どのようなレポジトリなのかを調べてみましょう。  

- rpmforge  
- epel  
- remi  





#参考文献
1. [UnixPower on Networking](http://www.unix-power.net/linux/yum.html)