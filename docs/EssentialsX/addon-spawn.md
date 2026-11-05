# EssentialsX Spawn アドオン解説

[← コマンド総合一覧へ戻る](README.md) | [アドオン一覧](README.md#4-公式アドオン解説ページ一覧)

---

**EssentialsX Spawn** は、Minecraftサーバーにおける「初期スポーン地点」や「死亡時のリスポーン地点」を高度に制御するための公式拡張アドオンです。

バニラのベッドや初期リスポーン地点だけでなく、権限グループ（LuckPerms等）ごとに異なるスポーン地点（例: 新規プレイヤー用スポーン、VIP用スポーン、管理者用スポーン）を設定したり、初参加時のウェルカムスポーンを指定することが可能です。

---

## 目次

1. [コマンド一覧と詳細解説](#1-コマンド一覧と詳細解説)
2. [グループ別スポーンの設定方法](#2-グループ別スポーンの設定方法)
3. [リスポーン優先度（config.yml）の解説](#3-リスポーン優先度configymlの解説)
4. [権限ノード一覧](#4-権限ノード一覧)
5. [よくあるトラブルと解決策](#5-よくあるトラブルと解決策)

---

## 1. コマンド一覧と詳細解説

### `/spawn`
- **対象**: 一般プレイヤー / 管理者
- **構文**: `/spawn [対象プレイヤー名]`
- **エイリアス**: なし
- **権限ノード**: 
  - `essentials.spawn`（自分自身のテレポート）
  - `essentials.spawn.others`（他プレイヤーを強制テレポート）
- **効果・解説**:
  サーバーのスポーン地点へ瞬間移動します。
  一般プレイヤーは引数なしで実行して自分のグループに割り当てられたスポーン地点へ移動します。
  管理者は他プレイヤー名を引数に指定することで、迷子になったプレイヤーや違反者を強制的にスポーン地点へ送り届けることができます。
- **使用例**:
  - `/spawn`（自分がスポーンへ戻る）
  - `/spawn Steve`（Steveさんをスポーンへ転送）

---

### `/setspawn`
- **対象**: 管理者（OP）
- **構文**: `/setspawn [グループ名]`
- **エイリアス**: なし
- **権限ノード**: `essentials.setspawn`
- **効果・解説**:
  現在立っている足元の座標と視線の向き（Pitch/Yaw）を、サーバーのスポーン地点として登録・保存します。
  - **引数なし**: サーバー全体の「デフォルトスポーン」として設定されます。
  - **`[グループ名]` を指定**: LuckPerms などの権限グループ名（例: `default`, `vip`, `admin`, `newbies`）を指定すると、そのグループに所属するプレイヤー専用のスポーン地点として個別に保存されます。
- **使用例**:
  - `/setspawn`（通常スポーンを設定）
  - `/setspawn default`（一般グループ用スポーンを設定）
  - `/setspawn newbie`（初参加初心者グループ用スポーンを設定）

---

## 2. グループ別スポーンの設定方法

EssentialsX Spawn では、プレイヤーの所属グループに応じて移動先やリスポーン先を自動分岐させることができます。

1. **スポーン地点の作成**:
   移動させたい場所に立ち、グループ名を指定して `/setspawn` を実行します。
   ```text
   /setspawn default
   /setspawn vip
   /setspawn admin
   ```
2. **グループの優先順位設定**:
   `plugins/Essentials/config.yml` の最下部にある `spawn-priority` セクションで、どのグループを優先して判定するか順序を調整します。

---

## 3. リスポーン優先度（config.yml）の解説

死亡したプレイヤーが復活する場所は、`config.yml` 内の `respawn-listener-priority` で決定されます。

```yaml
# リスポーンイベントの処理優先度
# lowest, low, normal, high, highest, none のいずれかを指定
respawn-listener-priority: high

# 死亡時にホーム地点（ベッド等）を優先するかどうか
# true: ベッドや/sethomeを最優先
# false: Essentialsの/setspawn地点を最優先
respawn-at-home: true

# 初めてサーバーに参加したプレイヤーのスポーン地点（グループ名）
newbies:
  announce-format: '&d{DISPLAYNAME}&e さんがサーバーに初めて参加しました！'
  spawnpoint: default
```

> **ポイント**: 他のワールド管理プラグイン（Multiverse-Core 等）とリスポーン地点が競合する場合は、`respawn-listener-priority: highest` に設定することで EssentialsX Spawn の設定が最優先されます。

---

## 4. 権限ノード一覧

| 権限ノード | デフォルト | 説明 |
| :--- | :--- | :--- |
| `essentials.spawn` | 全員 (true) | `/spawn` コマンドでスポーン地点へ移動する |
| `essentials.spawn.others` | OPのみ | 他人を `/spawn <プレイヤー>` で強制移動させる |
| `essentials.setspawn` | OPのみ | `/setspawn` コマンドでスポーン地点を設定する |

---

## 5. よくあるトラブルと解決策

- **Q. 死亡したときに `/setspawn` で設定した場所ではなく、バニラの初期リスポーン地点に飛ばされる**  
  **A.** `config.yml` の `respawn-listener-priority` を `high` または `highest` に変更し、`/ess reload` を実行してください。また、`respawn-at-home: false` にするとベッドの有無に関わらず必ずスポーン地点で復活させることができます。

- **Q. 初参加のプレイヤーだけをチュートリアル広場に飛ばしたい**  
  **A.** チュートリアル広場で `/setspawn newbie` を実行し、`config.yml` の `newbies.spawnpoint: newbie` に設定してください。

---

[← コマンド総合一覧へ戻る](README.md) | [アドオン一覧](README.md#4-公式アドオン解説ページ一覧)
