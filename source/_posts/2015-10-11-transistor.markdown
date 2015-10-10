---
layout: post
title: "transistor"
date: 2015-10-10 00:00:26 +0900
comments: true
published: true
categories: 電気回路
---
#トランジスタの役割
トランジスタは、電圧・電流を増幅させる働きを持ちます。携帯電話は、空気中を伝わってくる電波(微弱な電気信号)を増幅して、通信が可能な信号にしているようです。  
[Nch MOSFET EKI04047](http://akizukidenshi.com/img/goods/C/I-08423.jpg)

トランジスタの種類には、以下のものがある  
1. バイポーラ・トランジスタ  
2. Field Effect Transistor  

##バイポーラ・トランジスタ
バイポーラトランジスタには、以下のものがある  
1. NPN型トランジスタ  
2. PNP型トランジスタ  
バイポーラトランジスタの場合、端子はコレクタ・ベース・エミッタの3種類が存在する。
##バイポーラトランジスタは電流制御に用いられる。
バイポーラトランジスタの場合、コレクタ・ベース・エミッタ間は電気的につながっている。

##Field Effect Transistor
Field Effect Transistor(電界効果トランジスタ)には、次の種類がある。  
1. Nチャネル  
2. Pチャネル  
FETの場合、ソース、ドレイン、ゲートの3種類が存在する。  
##MOSFETは電圧の制御で用いられる。
MOSとは、金属酸化膜型のこと。
MOSFETの場合、ゲート端子が浮いていることになる。
##記号の意味
1. Vdss(ドレイン・ソース間電圧[Drain-source voltage])-最大何ボルトまで接続できるか
2. ld(ドレイン電流[Gate threshold voltage])-最大何アンペアの電流を流せるか
3. Vth(ゲートしきい値電圧[Gate threshold voltage])-負荷をON/OFFさせるときのゲート電圧の境
4. Rds(ドレイン・ソース間オン抵抗値[Drain.source ON resistance])オン抵抗値

##参考文献  
1. [ＦＥＴをマイコン出力のスイッチとして使う方法](http://www.geocities.jp/zattouka/GarageHouse/micon/circuit/FET.htm)
2. [マイコン徹底入門](http://miqn.net/periph/63.html)


