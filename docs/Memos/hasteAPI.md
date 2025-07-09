---
sidebar_position: 3
---

# Haste API

[p.yama2211.jp](https://p.yama2211.jp/)のAPIについてです。

## 注意点

- Cloudflareが入っているため、ユーザーエージェント文字列が特殊な場合は、JSチャレンジやブロックが発生する可能性があります。
- AWSやAzure、GCPなどのクラウドからのアクセスする場合、ボットファイトと判定され、JSチャレンジやブロックが発生する可能性があります。
- Tor、China、Russian Federationからのアクセスは、JSチャレンジが発生する場合があります。
- その他、Cloudflareから意図しないJSチャレンジやブロックが発生する場合があります。
- サーバの停止や再起動により、レスポンスが帰ってこない、500エラー、502エラー(Bad gateway)が発生する場合があります。

要約すると、UAが特殊な場合や、変な環境、変なところからのアクセスはJSチャレンジやブロックが発生します。

## 使い方
`https://p.yama2211.jp/documents` メソッドはPOSTです。  

プレーンテキストにて文章をヘッダーにつけて送信することで、  
URLが発行されます。

```
$ curl.exe -d "Hello World!!" https://p.yama2211.jp/documents
{"key":"reforawubo"}
```

keyのreforawuboがURLになります。  
`https://p.yama2211.jp/reforawubo`  
テキストのみで表示する場合は、`https://p.yama2211.jp/raw/reforawubo`