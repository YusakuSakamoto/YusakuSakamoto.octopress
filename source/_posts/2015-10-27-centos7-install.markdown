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

##repo追加(rpmforge,epel,elrepo,remi,IUS)
```
cd ~/Downloads
rpm --import http://apt.sw.be/RPM-GPG-KEY.dag.txt
rpm -ivh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el7.rf.x86_64.rpm
rpm --import http://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-7
rpm -ivh http://ftp-srv2.kddilabs.jp/Linux/packages/fedora/epel/7/x86_64/e/epel-release-7-5.noarch.rpm
rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org
rpm -ivh http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm
rpm --import http://rpms.famillecollet.com/RPM-GPG-KEY-remi
rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
wget https://dl.iuscommunity.org/pub/ius/stable/CentOS/7/x86_64/ius-release-1.0-14.ius.centos7.noarch.rpm
rpm -Uvh ius-release-1.0-14.ius.centos7.noarch.rpm
```

#各種インストール
##keepassxのインストール
ubuntuを使っている間は、keepass2をインストールするのが当たり前でしたが、今回はcentosで、しかも不慣れなyumなので、少しの違和感がありました。次のコマンドを実行  
`
sudo yum install keepassx
`
  
初めて聞きますが、このコマンドで入りました。  
  
##dropboxのインストール  
解説ページにしたがってコマンドを入力するだけで入ります。ありがとうございます。  

##gitのインストール
```
sudo yum install git
sudo yum install gitk
```

##git-flowのインストール
これに関してはビビりまくっていましたが、yumで行けるんかい！となってしまいました。コマンドはこちら
```
sudo yum install -y gitflow
```


##keepass2のインストール
keepassxですが、これでは.kdbxのファイルは扱えない、ということらしいので、入れなおしました。  
gitでkeepass2のインストーラーを起動します。  
この時にちょっとしたエラー  
monoについてのエラーのようですが、以下のコマンドで解決しました。  
install方法を示します。  
```
sudo yum install mono-core
sudo yum install mono-devel
sudo yum install mono-devel
cd ~/Downloads
git clone https://github.com/akmc/fedora_keepass_installer
cd fedora_keepass_installer
chmod u+x keepass.sh
./keepass.sh
```
##build-essentialsをinstall
ubuntuでは簡単ですが、ccentosの場合は？
```
sudo su
yum groupinstall "Development Tools"
yum install kernel-devel kernel-headers
```
yumのgroup-installを使えばいいようですね。存在は知っていましたが、初めて使いました。これによって、gccだのg++だのもすべてインストールしてくれるので、素晴らしく楽ですね。

##emacs 24.4のインストール
なんか気持ち悪い....  
しかし入りました。
```
yum install gcc make ncurses-devel gtk+ gtk3-devel.x86_64
yum install giflib-devel libjpeg-devel libtiff-devel
cd /usr/local/src
wget http://mirror.bjtu.edu.cn/gnu/emacs/emacs-24.4.tar.gz
tar xzvf emacs-24.4.tar.gz
cd emacs-24.4
./configure --without-all --with-x-toolkit=no --without-x
sudo make
sudo make install
```

##gitのバージョンアップ
```
sudo yum remove git
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel perl-ExtUtils-MakeMaker
cd ~/Downloads
wget https://www.kernel.org/pub/software/scm/git/git-2.5.1.tar.gz
tar -zxf git-2.5.1.tar.gz
cd git-2.5.1
sudo make
sudo make install
git --version
```
していない？

##vimのインストール
これに関しては、ほぼ教科書通りのことをしました。
vimは今までの過程で既に入っているようでしたので、neobundleの設定をして終了でした。



##その他
###tmuxのインストール
```
sudo yum install tmux
```
##haroopadのインストール
```
wget https://bitbucket.org/rhiokim/haroopad-download/downloads/haroopad-v0.13.1-x64.tar.gz
tar -zxv haroopad-v0.13.1-x64.tar.gz
cd haroopad-v0.13.1-x64
tar -zxvf data.tar.gz
sudo cp ./usr/ / -rf
tar zxf control.tar.gz
chmod 755 postinst
sudo ./postinst
```

##VirtualBoxのインストール

[CentOS 7 における VirtualBox のインストール手順](http://yoshiiz.blog129.fc2.com/blog-entry-825.html)

###日本語環境のインストール
```
sudo yum -y groupinstall "Japanese Support"
sudo yum -y install ibus-anthy
sudo yum -y remove ibus-kkc
sudo yum -y install ibus-kkc
```


#参考文献
1. [UnixPower on Networking](http://www.unix-power.net/linux/yum.html)
2. [repositoryの解説・入れ方](http://oki2a24.com/2012/03/13/what-is-rpmforge-remi-epel/)
3. [dropboxのinstall](http://weblabo.oscasierra.net/installing-dropbox-on-redhat/)
4. [CentOS7の日本語入力にAnthyを使うには](http://www.sssg.org/blogs/hiro345/archives/17553.html)
