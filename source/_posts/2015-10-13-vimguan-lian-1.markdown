---
layout: post
title: "vim1"
date: 2015-10-13 08:04:13 +0900
comments: true
published: true
categories: vim
--- 
![](https://upload.wikimedia.org/wikipedia/commons/4/4f/Icon-Vim.svg)
#vim設定ファイルの.vimrcをemacsで編集するという矛盾
今までemacsを使っていたのですが、後輩にvimを扱う者が現れまして、なかなかに使いやすそうだなと思ってちょっと挑戦してみました。もともと少し練習したことがありましたので、ちょっとした編集くらいはできていましたが、今回は**設定ファイル**を編集しました。

##.vimについて
.vimは自分で編集した*.vim等を置いておくディレクトリだそうですが、私はこれに関しては開発者側に回る気はさらさらないので、githubからひたすらcloneしてきたものを保存していくディレクトリになります。

##.vimrcについて
.vimrcは、事細かな設定をするときに使用します。例えば、色の設定をするときなどは、ここをいじります。実際にいじってみて、難易度はまあ、.emacs.dをいじった人であれば余裕であろうと思います。

##pasteってどうするんだ
はい、ここでemacsをついつい立ち上げてしまった、という話です。というのも、例えばfirefoxで見つけた文字列をコピーしようとした時に、ペースト[p]ではうまく行かないのです!!なんと言うことなのでしょうか。ああ、emacs使いやすいなぁ...

調べてみた結果、vim-gtkなりのclipboardが使えるようなパッケージ入りのものをインストールすれば、自然にクリップボードからのコピーにも対応できるようになるよ、という事らしいです。よって、

```
sudo apt-get install vim-gtk
```

* * *

##vimshellを入れてみた、という話
neobundleとかいう管理方法をインストールしてみた結果、結構使いやすかったと言いますか、vim側が勝手に全部やってくれます。素晴らしいです。vimshellだけは少しコンパイルして動作環境に適合させないといけないみたいですが、それ以外は全部自動です。

.vimrcの設定
```
git clone https://github.com/YusakuSakamoto/dotfiles ~/dotfiles
sh ~/dotfiles/link.sh
```


neobundleの設定
```
mkdir .vim
mkdir -p ~.vim/bundle
git clone https://github.com/Shougo/neobundle.vim ~/.vim/bundle/neobundle.vim
```

vimを立ち上げると、環境を自動的に入れてくれます。
