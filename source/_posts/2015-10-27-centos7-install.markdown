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

- [repoforge](https://wiki.centos.org/AdditionalResources/Repositories/RPMForge)  
- epel  
- remi  
- RPMFusion  
- IUS  
- Utter Ramblings  

**注意**  
今は、RPMForgeではなく、**Repoforge**という名前になっているようです  
しかし、rpmファイルの名前は依然としてrpmforgeになっていたりして。

調べた結果、個人的な感想を述べるとすれば、みなさんパッケージの種類が増えるだの、バージョンが増えるなど、様々言いたいことを申しているようですが、よくわからないので公式ページを見に行きました。  

RPMforge is a collaboration of Dag and other packagers. They provide over 5000 packages for CentOS, including wine, vlc, mplayer, xmms-mp3, and other popular media tools. It is not part of Red Hat or CentOS but is designed to work with those distributions. See also Using RPMforge and Repoforge.  
  
そんだけかい！  
  
その他のレポジトリもそんなものなんでしょう。とりあえずいっぱい追加しても悪いことはない、ということですね。

##keepassxのインストール
ubuntuを使っている間は、keepass2をインストールするのが当たり前でしたが、今回はcentosで、しかも不慣れなyumなので、少しの違和感がありました。次のコマンドを実行  
`
sudo yum install keepassx
`
初めて聞きますが、このコマンドで入りました。

#参考文献
1. [UnixPower on Networking](http://www.unix-power.net/linux/yum.html)
2. [repositoryの解説・入れ方](http://oki2a24.com/2012/03/13/what-is-rpmforge-remi-epel/)