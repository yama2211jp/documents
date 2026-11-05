# EssentialsX コマンド総合一覧・日本語ガイド

Minecraft（Paper / Purpur / Spigot）サーバーで最も広く利用されている必須級ユーティリティプラグイン **「EssentialsX」** の全コマンドおよび公式アドオンの総合リファレンスドキュメントです。

本ドキュメントは、「誰向けのコマンドなのか」を明確に整理し、日常プレイからサーバー運営・モデレーション・アドオン連携まで、どのコマンドがどのように作用するかを日本語でわかりやすく解説しています。

---

## 📖 対象者別ガイド・ページ一覧

知りたいコマンドの用途や権限レベルに応じて、以下の各個別ページへ進んでください。

| 対象者・カテゴリ | ドキュメントリンク | 主な内容 |
| :--- | :--- | :--- |
| **一般プレイヤー向け** | [一般向けコマンド解説ページ](general-commands.md) | 拠点設定（`/home`）、友達へのテレポート要請（`/tpa`）、個別チャット（`/msg`）、所持金・送金（`/balance`, `/pay`）、キット（`/kit`）など、参加者全員が日常的に使うコマンド群 |
| **モデレーター・運営向け** | [モデレーター向けコマンド解説ページ](moderator-commands.md) | 迷惑プレイヤーへの処罰（`/kick`, `/ban`, `/mute`, `/jail`）、調査・監視（`/seen`, `/whois`, `/invsee`, `/vanish`, `/socialspy`）、誘導（`/tp`, `/tphere`）など、サーバーの治安維持コマンド群 |
| **サーバー管理者（OP）向け** | [管理者向けコマンド解説ページ](admin-commands.md) | 設定リロード（`/ess reload`）、負荷確認（`/gc`）、全体告知（`/broadcast`）、プレイヤー強化（`/god`, `/fly`, `/heal`）、アイテム生成・修理（`/give`, `/repair`）、ワールド環境操作（`/time`, `/weather`）、経済操作（`/eco`）など |

---

## 🧩 公式・関連アドオン個別ページ一覧

EssentialsX の機能をさらに拡張する公式・関連アドオンの解説および専用コマンド一覧です。

- [**EssentialsX Spawn 解説**](addon-spawn.md)
  - スポーン地点の設定・移動（`/spawn`, `/setspawn`）、権限グループ別スポーン、リスポーン優先度制御。
- [**EssentialsX Chat 解説**](addon-chat.md)
  - 役職Prefix/Suffixの反映、文字色・装飾、ローカル/グローバル近接チャット、シャウト発言（`!`）。
- [**EssentialsX Discord & Discord Link 解説**](addon-discord.md)
  - MinecraftとDiscordのチャット相互同期、アカウント連携（`/link`, `/unlink`）、Discord側スラッシュコマンド（`/execute`, `/list`）。
- [**EssentialsX WarpGUI 解説**](addon-warpgui.md)
  - チェストGUIをクリックして直感的にワープできるインターフェース（`/warp`, `/warpgui`, `/warpcfg`）。
- [**EssentialsX AntiBuild & Protect 解説**](addon-antibuild-protect.md)
  - ゲストの破壊・建築防止（AntiBuild）、TNT・クリーパー爆発・火災延焼防止（Protect）。
- [**EssentialsX GeoIP 解説**](addon-geoip.md)
  - IPアドレスから接続元の国名・地域を自動判定し、`/whois` やログイン通知に統合。

---

## 💡 コマンドの記法ルール

ドキュメント内で使用しているコマンド引数の記法は以下の通りです。

- `<必須引数>`: コマンドを実行する際に**必ず指定する必要がある項目**です。
- `[任意引数]`: 必要に応じて**省略可能な項目**です。省略時はデフォルト値が適用されます。
- `(選択肢A | 選択肢B)`: 指定された選択肢のいずれか1つを選んで入力します。
- `時間指定フォーマット`: `10s`（10秒）、`15m`（15分）、`2h`（2時間）、`7d`（7日）など。

---

## 🔍 全コマンドクイック早見一覧表

アルファベット順の総合インデックスです。コマンド名をクリックすると詳細解説へジャンプできます。

| コマンド | 主な短縮形 | 対象者 | 日本語による作用・概要 | 詳細リンク |
| :--- | :--- | :--- | :--- | :--- |
| `/afk` | なし | 一般 | 一時離席中（AFK）ステータスを切り替える | [詳細](general-commands.md#afk) |
| `/anvil` | なし | 管理者 | ブロックなしでどこでも金床画面を開く | [詳細](admin-commands.md#どこでもguiポータブルユーティリティ) |
| `/back` | `/return` | 一般 | 直前にテレポートした場所、または直前の死亡地点へ戻る | [詳細](general-commands.md#back) |
| `/backup` | なし | 管理者 | 設定された外部バックアップスクリプトを即時実行する | [詳細](admin-commands.md#backup) |
| `/balance` | `/bal`, `/money` | 一般 | 自分の所持金（通貨残高）を確認する | [詳細](general-commands.md#balance--bal--money) |
| `/balancetop` | `/baltop` | 一般 | サーバー内の所持金長者番付（ランキング）を表示する | [詳細](general-commands.md#balancetop--baltop) |
| `/ban` | なし | 運営 | 悪質プレイヤーのアカウントを無期限アクセス禁止にする | [詳細](moderator-commands.md#ban) |
| `/banip` | なし | 運営 | 悪質プレイヤーのIPアドレスをアクセス拒否リストに追加する | [詳細](moderator-commands.md#banip) |
| `/break` | なし | 管理者 | 視線を合わせているブロック（岩盤含む）を一撃破壊する | [詳細](admin-commands.md#break) |
| `/broadcast` | `/bc`, `/bcast` | 管理者 | サーバー全体に太字・強調アナウンスを一斉告知する | [詳細](admin-commands.md#broadcast--bc) |
| `/burn` | なし | 管理者 | 指定したプレイヤーを指定秒数間炎上させる | [詳細](admin-commands.md#2-プレイヤー能力改変チート代理実行系) |
| `/cartographytable`| なし | 管理者 | どこでも製図台画面を開く | [詳細](admin-commands.md#どこでもguiポータブルユーティリティ) |
| `/clearinventory` | `/ci` | 管理者 | 対象プレイヤーのインベントリ内のアイテムを全消去する | [詳細](admin-commands.md#clearinventory--ci) |
| `/compass` | なし | 一般 | 現在向いている方角（東西南北）を表示する | [詳細](general-commands.md#compass) |
| `/delhome` | `/rmhome` | 一般 | 登録済みのホーム地点を削除する | [詳細](general-commands.md#delhome) |
| `/deljail` | なし | 管理者 | 設定済みの監獄セルを削除する | [詳細](admin-commands.md#setjail--deljail) |
| `/delwarp` | なし | 管理者 | 登録済みの公共ワープ地点を削除する | [詳細](admin-commands.md#setwarp--delwarp) |
| `/depth` | なし | 一般 | 海抜（Y=63）からの高低差を表示する | [詳細](general-commands.md#depth) |
| `/discord` | なし | 一般 | サーバー公式Discordの招待リンクを表示する | [詳細](addon-discord.md#discord) |
| `/eco` | `/economy` | 管理者 | プレイヤーの所持金を直接付与・没収・設定・リセットする | [詳細](admin-commands.md#eco) |
| `/enchant` | なし | 管理者 | 手持ちアイテムに限界突破レベルを含むエンチャントを付与 | [詳細](admin-commands.md#enchant) |
| `/enderchest` | `/ec` | 運営 | 対象プレイヤーのエンダーチェスト内身を遠隔閲覧・没収 | [詳細](moderator-commands.md#enderchest--ec) |
| `/essentials` | `/ess` | 管理者 | 設定再読み込み（`reload`）、デバッグ情報出力（`dump`） | [詳細](admin-commands.md#essentials-reload) |
| `/exp` | `/xp` | 管理者 | 経験値ポイントまたはレベル（`L`）を直接付与・変更する | [詳細](admin-commands.md#exp) |
| `/extinguish` | `/ext` | 管理者 | 対象プレイヤーの身体の炎を瞬時に消火する | [詳細](admin-commands.md#extinguish--ext) |
| `/feed` | `/eat` | 管理者 | 対象プレイヤーの満腹度ゲージを満タンにする | [詳細](admin-commands.md#feed) |
| `/fly` | なし | 管理者 | サバイバルモードのプレイヤーにクリエイティブ飛行を付与 | [詳細](admin-commands.md#fly) |
| `/gc` | `/lag`, `/mem` | 管理者 | サーバーの健康状態（TPS、メモリ使用量、Mob数）を表示 | [詳細](admin-commands.md#gc--lag--mem) |
| `/getpos` | `/coords` | 一般 | 現在地のワールド名およびX, Y, Z座標を表示する | [詳細](general-commands.md#getpos) |
| `/give` | なし | 管理者 | 対象プレイヤーにアイテムを直接付与する | [詳細](admin-commands.md#give) |
| `/god` | `/tgm` | 管理者 | 奈落以外のあらゆるダメージを無効化する無敵モードを付与 | [詳細](admin-commands.md#god) |
| `/grindstone` | なし | 管理者 | どこでも砥石画面を開く | [詳細](admin-commands.md#どこでもguiポータブルユーティリティ) |
| `/hat` | `/headgear` | 管理者 | 手に持っているアイテムをヘルメット（頭）に装着する | [詳細](admin-commands.md#hat) |
| `/heal` | なし | 管理者 | 体力と満腹度を全回復し、有害な状態異常を解除する | [詳細](admin-commands.md#heal) |
| `/helpop` | `/ac` | 一般 | 運営スタッフ全員へ通報や質問メッセージを非公開送信 | [詳細](general-commands.md#helpop) |
| `/home` | なし | 一般 | 登録した拠点（ホーム）へテレポートする | [詳細](general-commands.md#home) |
| `/homes` | `/homelist` | 一般 | 自分が登録しているホームの一覧を表示する | [詳細](general-commands.md#homes) |
| `/ignore` | なし | 一般 | 特定プレイヤーのチャット・DM・テレポート申請を遮断 | [詳細](general-commands.md#ignore) |
| `/info` | `/news` | 一般 | サーバーの案内文やルール等の情報ドキュメントを表示 | [詳細](general-commands.md#info) |
| `/invsee` | なし | 運営 | 対象プレイヤーの手持ちインベントリをGUIで覗き見・編集 | [詳細](moderator-commands.md#invsee) |
| `/item` | `/i` | 管理者 | 自分のインベントリに指定アイテムを直接取り出す | [詳細](admin-commands.md#item--i) |
| `/itemdb` | `/dura` | 一般 | 手に持っているアイテムの内部IDや残り耐久値を表示する | [詳細](general-commands.md#itemdb) |
| `/jail` | なし | 運営 | 違反プレイヤーを監獄セルへ強制送致・隔離する | [詳細](moderator-commands.md#jail) |
| `/jails` | なし | 運営 | サーバー内に登録されている監獄の一覧を表示する | [詳細](moderator-commands.md#jails) |
| `/jump` | `/j` | 運営 | 照準（クロスヘア）を合わせている遠くのブロックへ移動 | [詳細](moderator-commands.md#jump--j) |
| `/kick` | なし | 運営 | 対象プレイヤーをサーバーから強制切断させる | [詳細](moderator-commands.md#kick) |
| `/kickall` | なし | 運営 | サーバー内の全プレイヤーを一斉に強制切断させる | [詳細](moderator-commands.md#kickall) |
| `/kill` | なし | 管理者 | 対象プレイヤーを即死させる | [詳細](admin-commands.md#kill) |
| `/killall` | `/butcher` | 管理者 | 周囲または全ワールドのMobやドロップ品を一括消去する | [詳細](admin-commands.md#killall) |
| `/kit` | なし | 一般 | 設定されたアイテム詰め合わせセット（キット）を受け取る | [詳細](general-commands.md#kit) |
| `/kits` | なし | 一般 | 自分が受け取り可能なキットの一覧を表示する | [詳細](general-commands.md#kits) |
| `/lightning` | `/smite` | 管理者 | 対象プレイヤーや指定地点に落雷を発生させる | [詳細](admin-commands.md#2-プレイヤー能力改変チート代理実行系) |
| `/link` | `/discordlink` | 一般 | MinecraftとDiscordを紐付けるワンタイムコードを発行 | [詳細](addon-discord.md#link) |
| `/list` | `/online` | 一般 | サーバーのオンラインプレイヤー一覧と人数を表示する | [詳細](general-commands.md#list) |
| `/loom` | なし | 管理者 | どこでも機織り機画面を開く | [詳細](admin-commands.md#どこでもguiポータブルユーティリティ) |
| `/mail` | なし | 一般 | オフラインでも送受信できるサーバー内メッセージシステム | [詳細](general-commands.md#mail) |
| `/me` | なし | 一般 | チャット欄にロールプレイ風の三人称アクション文を表示 | [詳細](general-commands.md#me) |
| `/more` | なし | 管理者 | 手持ちアイテムの数量をスタック上限（64個）まで補充する | [詳細](admin-commands.md#more) |
| `/motd` | なし | 一般 | ログイン時の「今日のメッセージ（告知）」を再表示する | [詳細](general-commands.md#motd) |
| `/msg` | `/tell`, `/w` | 一般 | 特定のプレイヤーにだけ見える個人メッセージ（DM）を送信 | [詳細](general-commands.md#msg--tell--whisper--w) |
| `/mute` | なし | 運営 | 対象プレイヤーのチャット発言およびDM送信を禁止する | [詳細](moderator-commands.md#mute) |
| `/near` | なし | 一般 | 周囲にいるプレイヤーと距離（ブロック数）を表示する | [詳細](general-commands.md#near) |
| `/pay` | なし | 一般 | 自分の所持金から他プレイヤーへ送金する | [詳細](general-commands.md#pay) |
| `/ping` | `/pong` | 一般 | サーバーとの通信応答速度（ping値、ms）を測定する | [詳細](general-commands.md#ping) |
| `/playtime` | なし | 一般 | そのサーバーでプレイした通算プレイ時間を表示する | [詳細](general-commands.md#playtime) |
| `/powertool` | `/pt` | 管理者 | 手に持ったアイテムにクリック発動のコマンドをバインド | [詳細](admin-commands.md#powertool--pt) |
| `/ptime` | なし | 管理者 | 自分または対象プレイヤーの画面上だけの時刻を変更・固定 | [詳細](admin-commands.md#ptime-player-time) |
| `/pweather` | なし | 管理者 | 自分または対象プレイヤーの画面上だけの天候を変更・偽装 | [詳細](admin-commands.md#pweather-player-weather) |
| `/recipe` | `/formula` | 一般 | 手持ちアイテムのクラフトレシピを作業台GUIで確認する | [詳細](general-commands.md#recipe) |
| `/repair` | `/fix` | 管理者 | ダメージを受けた装備やツールの耐久値を全回復する | [詳細](admin-commands.md#repair--fix) |
| `/reply` | `/r` | 一般 | 直前にDMを送ってきた相手へ素早く返信する | [詳細](general-commands.md#reply--r) |
| `/rules` | なし | 一般 | サーバーの公式規約・ルールを表示する | [詳細](general-commands.md#rules) |
| `/seen` | なし | 運営 | プレイヤーの最終ログイン日時、IP、BAN状況等を確認 | [詳細](moderator-commands.md#seen) |
| `/sell` | なし | 一般 | 手持ちのアイテムを公式ショップに売却してお金に換える | [詳細](general-commands.md#sell) |
| `/sethome` | `/createhome` | 一般 | 現在地をホーム（拠点）として保存・登録する | [詳細](general-commands.md#sethome) |
| `/setjail` | なし | 管理者 | 現在地を監獄セルとして登録・作成する | [詳細](admin-commands.md#setjail--deljail) |
| `/setspawn` | なし | 管理者 | 現在地を初期スポーン地点（グループ別指定可）に設定 | [詳細](addon-spawn.md#setspawn) |
| `/setwarp` | なし | 管理者 | 現在地を公共ワープ地点として登録する | [詳細](admin-commands.md#setwarp--delwarp) |
| `/skull` | `/head` | 管理者 | 指定したプレイヤーのスキンが反映された頭ブロックを入手 | [詳細](admin-commands.md#skull) |
| `/smithingtable` | なし | 管理者 | どこでも鍛冶台画面を開く | [詳細](admin-commands.md#どこでもguiポータブルユーティリティ) |
| `/socialspy` | `/spy` | 運営 | プレイヤー間の個人DMやコマンド履歴を画面に傍受表示 | [詳細](moderator-commands.md#socialspy) |
| `/spawn` | なし | 一般 | サーバーの初期スポーン地点へテレポートする | [詳細](addon-spawn.md#spawn) |
| `/spawner` | なし | 管理者 | 視線を合わせているスポナーの出現Mobの種類を変更する | [詳細](admin-commands.md#spawner) |
| `/speed` | なし | 管理者 | 歩行速度や飛行速度の倍率を1〜10に変更する | [詳細](admin-commands.md#speed) |
| `/stonecutter` | なし | 管理者 | どこでも石切台画面を開く | [詳細](admin-commands.md#どこでもguiポータブルユーティリティ) |
| `/sudo` | なし | 管理者 | 対象プレイヤーに成り代わりコマンドや発言を代理実行 | [詳細](admin-commands.md#sudo) |
| `/suicide` | なし | 一般 | スタック脱出等のためにその場で自決（死亡）する | [詳細](general-commands.md#suicide) |
| `/tempban` | なし | 運営 | 指定した期間（例: 7d）だけ一時的にアクセス禁止にする | [詳細](moderator-commands.md#tempban) |
| `/tempmute` | なし | 運営 | 指定した期間（例: 30m）だけチャット発言を一時禁止する | [詳細](moderator-commands.md#tempmute) |
| `/time` | なし | 管理者 | ワールド全体の時計（昼夜・時刻）を変更する | [詳細](admin-commands.md#time) |
| `/togglejail` | なし | 運営 | プレイヤーの投獄状態と釈放状態をトグル切り替えする | [詳細](moderator-commands.md#togglejail) |
| `/top` | なし | 運営 | 現在地の真上にある最上階の安全な地表へ瞬間ワープする | [詳細](moderator-commands.md#top) |
| `/tp` | なし | 運営 | 相手の許可なしに即座に対象プレイヤーの場所へテレポート | [詳細](moderator-commands.md#tp) |
| `/tpa` | なし | 一般 | 相手の場所へテレポートするための申請リクエストを送る | [詳細](general-commands.md#tpa) |
| `/tpaccept` | `/tpyes` | 一般 | 届いたテレポート申請（`/tpa`, `/tpahere`）を承諾する | [詳細](general-commands.md#tpaccept) |
| `/tpahere` | なし | 一般 | 相手を自分の現在地へ呼び寄せるための申請リクエストを送る | [詳細](general-commands.md#tpahere) |
| `/tpall` | なし | 運営 | サーバー全員を一斉に自分の足元へ強制テレポートさせる | [詳細](moderator-commands.md#tpall) |
| `/tpdeny` | `/tpno` | 一般 | 届いたテレポート申請を拒否する | [詳細](general-commands.md#tpdeny) |
| `/tphere` | `/s` | 運営 | 対象プレイヤーを自分の足元へ強制呼び出しテレポート | [詳細](moderator-commands.md#tphere) |
| `/tpo` | なし | 運営 | 受信拒否トグル設定を貫通して相手の元へ強制テレポート | [詳細](moderator-commands.md#tpo--tpohere) |
| `/tpohere` | なし | 運営 | 受信拒否トグル設定を貫通して相手を足元へ強制呼び出し | [詳細](moderator-commands.md#tpo--tpohere) |
| `/unban` | `/pardon` | 運営 | BAN処罰を解除し、再度ログインできるようにする | [詳細](moderator-commands.md#unban) |
| `/unbanip` | `/pardonip` | 運営 | IP-BANリストからIPアドレスを削除して制限解除する | [詳細](moderator-commands.md#unbanip) |
| `/unlink` | `/discordunlink`| 一般 | MinecraftとDiscordのアカウント連携を解除する | [詳細](addon-discord.md#unlink) |
| `/unmute` | なし | 運営 | ミュート状態を解除し、再度チャットを発言可能にする | [詳細](moderator-commands.md#unmute) |
| `/vanish` | `/v` | 運営 | Tabリストからも消える完全不可視状態でパトロールする | [詳細](moderator-commands.md#vanish--v) |
| `/warp` | なし | 一般 | 公共ワープ地点へ移動する（WarpGUI導入時はGUIが開く） | [詳細](general-commands.md#warp) / [GUI版](addon-warpgui.md#warp-guiフック) |
| `/warpcfg` | なし | 管理者 | WarpGUIのレイアウト、アイコン、設定を管理・リロード | [詳細](addon-warpgui.md#warpcfg) |
| `/warpgui` | なし | 一般 | ワープ選択用GUIメニューを明示的に開く | [詳細](addon-warpgui.md#warpgui) |
| `/warps` | なし | 一般 | 利用可能なワープ地点名の一覧を表示する | [詳細](general-commands.md#warp) |
| `/weather` | なし | 管理者 | ワールド全体の天候を晴れ・雨・雷雨に変更する | [詳細](admin-commands.md#weather) |
| `/whois` | なし | 運営 | プレイヤーのリアルタイム詳細情報（HP/IP/国籍等）を表示 | [詳細](moderator-commands.md#whois) |
| `/workbench` | `/wb`, `/craft` | 管理者 | どこでもクラフト作業台画面を開く | [詳細](admin-commands.md#どこでもguiポータブルユーティリティ) |
| `/worth` | なし | 一般 | アイテムの公式ショップ売却額相場を確認する | [詳細](general-commands.md#worth) |

---

## 🛠️ 運用・管理のTips

### 1. メッセージの日本語化
EssentialsX は標準で日本語化リソースを含んでいます。  
`plugins/Essentials/config.yml` を開き、以下の項目を設定して `/ess reload` を実行するだけで、システムメッセージを日本語表示に切り替えられます。
```yaml
locale: ja
```

### 2. 権限管理プラグイン（LuckPerms）との連携
EssentialsX の真価を発揮するには、権限管理プラグイン **LuckPerms** の導入が不可欠です。  
一般グループにコマンドを許可する際は、以下のコマンドを実行します。
```text
/lp group default permission set essentials.build true
/lp group default permission set essentials.home true
/lp group default permission set essentials.sethome true
/lp group default permission set essentials.tpa true
/lp group default permission set essentials.tpaccept true
/lp group default permission set essentials.spawn true
/lp group default permission set essentials.warp true
```

---

*このドキュメントは Minecraft サーバー運営者のための公式リファレンスとして管理・公開されています。*
