---
sidebar_position: 2
---

# timeAPI

現在時刻取得APIです。

## レート制限
10秒間に 100回以上 のリクエストされると、「429 Too many Requests」を返します。  
CloudFlareでも同様のレート制限を行っています。 
このレート制限は全てのAPIに適用されます。 

CloudFlareのレート制限の場合は以下が返されます。

``` json
{
  "status": 429,
  "error": "Rate limit exceeded",
  "message": "Too many requests. Please try again in about 5 minutes."
}
```

## API仕様

```
https://api.yama2211.jp/time
```

プレーンテキストで日本標準時(JST)を返します。

```
09:00.00
```

### tz
```
https://api.yama2211.jp/time?tz=[TimeZone]
```

[TimeZone]の時刻を返します。

```
[TimeZone]をutcにした場合：
00:00.00
```

```
[TimeZone]をAmerica/Los_Angelesにした場合：
17:00.00
```

:::warning

不正なタイムゾーンを指定した場合、UTCを返します。

:::

### f

```
https://api.yama2211.jp/time?f=[format]
```

時刻表表示のフォーマットを指定できます。

```
[format]をyyyy/MM/dd hh:mm.ssにした場合：
2026/05/14 09:00.00
```

### t

```
https://api.yama2211.jp/time/?t=[type]
```

表示方法を指定できます。  
指定できるものは「json」と「xml」です。  
指定されない場合はプレーンテキストで返します。

json結果例：

``` json
{"status":"success","time":"2026\/05\/14 09:00.00","timezone":"Asia\/Tokyo"}
```

xml結果例：

``` xml
<response>
<time>2026/05/14 09:59.18</time>
<timezone>Asia/Tokyo</timezone>
</response>
```