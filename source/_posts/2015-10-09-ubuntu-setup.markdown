---
layout: post
title: "ubuntu_setup"
date: 2015-10-09 18:46:34 +0900
comments: true
categories: 
---

#ubuntu setup 

最初にubuntuにインストールするシェルスクリプトです。
任意の場所にinstall.shの名前で保存します。
```
supo sh install.sh
```
でインストールを始めてください
```
#!/bin/bash

sudo apt-get -y update
sudo apt-get -y upgrade
sudo apt-get -y install emacs vim git gitk gcc g++ gfortran gnuplot terminator build-essential libgtk2.0-dev libjpeg-dev libjasper-dev libopenexr-dev cmake python-dev python-numpy python-tk libtbb-dev libeigen3-dev yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev libx264-dev libqt4-dev libqt4-opengl-dev sphinx-common texlive-latex-extra libv4l-dev libdc1394-22-dev libavcodec-dev libavformat-dev libswscale-dev default-jdk ant libvtk5-qt4-dev ibus-mozc arduino keepass2 nautilus-dropbox texlive libopencv-dev python-opencv cmake gparted inkscape mercurial  automake libtool freeglut3-dev xdotool unetbootin texlive-lang-cjk xdotool
```

