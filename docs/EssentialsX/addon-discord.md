# EssentialsX Discord & Discord Link アドオン解説

[← コマンド総合一覧へ戻る](README.md) | [アドオン一覧](README.md#4-公式アドオン解説ページ一覧)

---

**EssentialsX Discord** および **EssentialsX Discord Link** は、Minecraftサーバーと Discord サーバーを強力に相互連携させる公式拡張アドオンです。

ゲーム内のチャットと Discord のテキストチャンネルをリアルタイムで同期するだけでなく、ログイン・ログアウト通知、死亡通知、アカウント連携（Minecraft ID と Discord アカウントの紐付け）、Discord 上からのスラッシュコマンドによるサーバー管理を実現します。

---

## 目次

1. [機能概要とモジュール構成](#1-機能概要とモジュール構成)
2. [ゲーム内コマンド解説](#2-ゲーム内コマンド解説)
3. [Discord 側スラッシュコマンド解説](#3-discord-側スラッシュコマンド解説)
4. [権限ノード一覧](#4-権限ノード一覧)
5. [導入と初期設定の流れ](#5-導入と初期設定の流れ)

---

## 1. 機能概要とモジュール構成

EssentialsX の Discord 連携は主に2つの jar ファイルから構成されます。

- **EssentialsX Discord (`EssentialsXDiscord.jar`)**:
  Discord ボットを介して、チャットメッセージ、ログイン/ログアウト、死亡メッセージ、進捗（実績）達成通知を Discord チャンネルに中継します。また、Discord 上で動くスラッシュコマンドを提供します。
- **EssentialsX Discord Link (`EssentialsXDiscordLink.jar`)**:
  プレイヤーの Minecraft アカウント（UUID）と Discord アカウントを認証・紐付けし、Discord のロールと Minecraft の権限グループ（LuckPerms）を自動で同期します。

---

## 2. ゲーム内コマンド解説

### `/discord`
- **対象**: 全プレイヤー
- **構文**: `/discord`
- **エイリアス**: なし
- **権限ノード**: `essentials.discord`
- **効果・解説**:
  チャット欄にサーバー公式 Discord の招待リンク（Invite URL）を表示します。クリックするとブラウザまたは Discord アプリが開きます。

---

### `/link`
- **対象**: 全プレイヤー
- **構文**: `/link`
- **エイリアス**: `/elink`, `/discordlink`, `/ediscordlink`
- **権限ノード**: `essentials.discord.link`
- **効果・解説**:
  自分の Minecraft アカウントを Discord アカウントと連携するための**4桁〜6桁の認証コード（ワンタイムコード）を発行**します。
  発行されたコードを、指定された Discord チャンネルまたはボットのDMに入力することで連携が完了します。
  連携が完了すると、Discord 側の「認証済みメンバー」ロールが付与されたり、ゲーム内で特典キットが受け取れるなどの恩恵を設定できます。

---

### `/unlink`
- **対象**: 全プレイヤー
- **構文**: `/unlink`
- **エイリアス**: `/eunlink`, `/discordunlink`, `/ediscordunlink`
- **権限ノード**: `essentials.discord.link`
- **効果・解説**:
  現在紐付けられている自分の Minecraft アカウントと Discord アカウントの連携を解除します。

---

## 3. Discord 側スラッシュコマンド解説

Discord のチャット入力欄で `/` を打つことで呼び出せるボットコマンドです。  
※これらのコマンドの実行権限は、Discord 側の「サーバー設定」>「連携」>「EssentialsX ボット」からロールごとにアクセス制限できます。

### `/list`
- **実行場所**: Discord
- **効果・解説**:
  現在 Minecraft サーバーにログインしているプレイヤーの一覧と人数、サーバーの稼働状態（TPSや稼働時間）を Discord 上にリッチ埋め込み（Embed）で表示します。

### `/msg <player> <message>`
- **実行場所**: Discord
- **効果・解説**:
  Discord からゲーム内にいる特定のプレイヤーへプライベートメッセージ（個チャ）を送信します。

### `/execute <command>`
- **実行場所**: Discord（管理者・スタッフ専用）
- **効果・解説**:
  Discord から Minecraft サーバーの**コンソールコマンドを遠隔実行**します。
  外出先やPCから離れている場合でも、スマホの Discord から即座に `/kick`, `/ban`, `/whitelist on`, `/broadcast` などの管理コマンドを実行できます。

---

## 4. 権限ノード一覧

### Minecraft 側権限（LuckPerms等で設定）
| 権限ノード | デフォルト | 説明 |
| :--- | :--- | :--- |
| `essentials.discord` | 全員 (true) | ゲーム内で `/discord`（招待リンク表示）を実行する |
| `essentials.discord.link` | 全員 (true) | `/link`, `/unlink` を実行してアカウント連携を行う |
| `essentials.discord.receive.<channel>` | 全員 (true) | 指定した Discord チャンネルからのチャットをゲーム内で受信する |
| `essentials.discord.ping` | OPのみ | ゲーム内チャットから `@everyone` や `@here` メンションを Discord に飛ばすことを許可する |
| `essentials.discord.markdown` | OPのみ | ゲーム内チャットから Discord の太字・斜体等のマークダウン記法を使用可能にする |

---

## 5. 導入と初期設定の流れ

1. **Discord Developer Portal でボットを作成**:
   - 新しいアプリケーションを作成し、「Bot」タブでボットトークン（Token）を生成・コピーします。
   - **Privileged Gateway Intents**（`PRESENCE INTENT`, `SERVER MEMBERS INTENT`, `MESSAGE CONTENT INTENT`）をすべて ON にします。
2. **サーバーへ導入**:
   - `EssentialsXDiscord.jar` を `plugins/` に配置してサーバーを起動します。
3. **config.yml の編集**:
   - `plugins/Essentials/discord.yml` を開き、`token: "ここにボットトークン"` を貼り付けます。
   - 同期したい Discord チャンネルの ID を `channels` セクションに指定します。
4. **設定のリロード**:
   - `/ess reload` を実行するとボットがオンラインになり、連携が開始されます。

---

[← コマンド総合一覧へ戻る](README.md) | [アドオン一覧](README.md#4-公式アドオン解説ページ一覧)
