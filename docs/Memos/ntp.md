---
sidebar_position: 1
---

# NTPサーバー

ほぼ自分用にNTPサーバーを構築しました。  
一応誰でも接続が可能です。  
もし設定される場合は下記の内容をよくご確認の上、設定してください。  
NTP Pool Projectに参加する予定はありません。

## サーバスペック

| # | # |
|:----:|:----:|
| OS | Ubuntu 22.04.5 LTS |
| CPU | Intel Xeon Processor (Icelake), 3 コア |
| RAM | 2GB |
| Location | ConoHa/Tokyo |

## 上位ソースについて
当NTPでは、以下の上位ソースと同期しています。  

- [NICT(情報通信研究機構)](https://jjy.nict.go.jp/index.html)
- [国立天文台水沢](https://www.miz.nao.ac.jp/vlbi/ntp.html)
- [インターネットマルチフィード(MFEED)](https://www.mfeed.ad.jp/ntp/overview.html)

## 注意点

- 当NTPはあくまで個人が運営する実験的なNTPサーバです。
- たまに数時間～1日程度サーバが停止するときがあります。
- サーバへの負荷次第ではサーバを停止することがあります。
- 冗長構成はありません。

## 接続ドメイン
将来的にサーバのリプレイスを行う可能性があるため、ドメインを指定してください。  
ドメインは **`ntp.yama2211.jp`** です。  
IPv4とIPv6両方で接続できるはずです。  
