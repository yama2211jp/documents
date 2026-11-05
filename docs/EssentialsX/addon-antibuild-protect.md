# EssentialsX AntiBuild & Protect アドオン解説

[← コマンド総合一覧へ戻る](README.md) | [アドオン一覧](README.md#4-公式アドオン解説ページ一覧)

---

**EssentialsX AntiBuild** および **EssentialsX Protect** は、サーバーのワールドを荒らし被害（Griefing）や意図しない自然災害（TNT爆発、火災、クリーパーの地形破壊など）から守るための公式セキュリティ・保護アドオンです。

専用のコマンドを入力して使うタイプではなく、**権限（Permissions）の付与状態**および **設定ファイル（`config.yml`）のスイッチ**によって自動的・常時サーバー全体を監視・保護します。

---

## 目次

1. [EssentialsX AntiBuild の機能と権限制御](#1-essentialsx-antibuild-の機能と権限制御)
2. [EssentialsX Protect の災害防止機能](#2-essentialsx-protect-の災害防止機能)
3. [保護設定の構成例（config.yml）](#3-保護設定の構成例configyml)
4. [運用時のポイント・注意点](#4-運用時のポイント注意点)

---

## 1. EssentialsX AntiBuild の機能と権限制御

AntiBuild を導入すると、プレイヤーがワールド内で「ブロックを置く」「壊す」「アイテムを使う」「クラフトする」といったアクションを権限ごとに細かく制限できます。

例えば「サーバー規約に同意する前のゲスト（Guest）グループにはブロックの設置・破壊を一切させない」といった運用が可能です。

### 主要な権限ノード一覧

| 権限ノード | デフォルト | 効果・解説 |
| :--- | :--- | :--- |
| `essentials.build` | OPのみ | **ワールドでの建築・破壊・操作の包括権限**。通常のサバイバルプレイヤーグループには必ずこれを `true` で付与します。 |
| `essentials.build.place.<ブロック名>` | 設定依存 | 特定のブロックの設置のみを許可・禁止します。 |
| `essentials.build.break.<ブロック名>` | 設定依存 | 特定のブロックの破壊のみを許可・禁止します。 |
| `essentials.build.interact.<アイテム名>` | 設定依存 | 溶岩バケツやライターなど、特定アイテムの使用（右クリック）を制限します。 |
| `essentials.build.craft.<アイテム名>` | 設定依存 | 特定の危険アイテムのクラフト（作業台作成）を禁止します。 |
| `essentials.build.pickup.<アイテム名>` | 設定依存 | 特定アイテムの拾得（ドロップ回収）を禁止します。 |
| `essentials.build.drop.<アイテム名>` | 設定依存 | 特定アイテムを地面に捨てることを禁止します。 |

> **初心者が陥りやすい注意点**:  
> AntiBuild を導入した状態で `essentials.build` 権限を一般グループに与えていないと、一般プレイヤーがブロックを殴った際に「*You are not permitted to build*」と表示され、一切の作業ができなくなります。

---

## 2. EssentialsX Protect の災害防止機能

Protect は、爆発事故や自然発火によるサーバーの地形崩壊・建物の焼失を未然に防ぎます。

### 防ぐことができる災害一覧
- **TNTの爆発被害**: 地形破壊を無効化（プレイヤーへのダメージのみ維持可能）。
- **クリーパーの自爆**: ブロック破壊をブロックし、景観を守る。
- **火の延焼（Fire Spread）**: 木造建築に火が燃え移るのを防止。
- **溶岩の引火**: 溶岩の近くにある木材が自然発火するのを防止。
- **ウィザー・エンドクリスタル**: 召喚時や攻撃時のブロック破壊を防止。
- **雷（落雷）**: 雷による火災の発生を無効化。

---

## 3. 保護設定の構成例（config.yml）

`plugins/Essentials/config.yml` 内の `protect` セクションで保護項目を `true` / `false` で切り替えます。

```yaml
protect:
  # 物理現象・災害の防止設定
  prevent:
    # 溶岩による引火延焼を防ぐ
    lava-fire-spread: true

    # 通常の火の延焼を防ぐ（木造建築の火事防止）
    fire-spread: true

    # 火打石やチャッカマンによる着火を防ぐ
    flint-fire: false

    # 雷による火災発生を防ぐ
    lightning-fire-spread: true

    # チェスト等の爆発耐性
    chest-protection: true

    # クリーパーの爆発による地形破壊を防ぐ（ブロックが壊れない）
    creeper-explosion: true

    # クリーパーのプレイヤーへのダメージ自体を防ぐか
    creeper-playerdamage: false

    # TNTの爆発によるブロック破壊を防ぐ
    tnt-explosion: true

    # ウィザーのブロック破壊を防ぐ
    wither-block-damage: true

    # エンダードラゴンのブロック破壊を防ぐ
    dragon-block-damage: true
```

---

## 4. 運用時のポイント・注意点

1. **WorldGuard との併用**:
   EssentialsX Protect は「サーバーのワールド全体」に一律で適用されます。
   「ロビーや中央広場だけ爆発を無効化し、資源ワールドではTNT採掘を許可したい」といったエリアごとの細かい制御を行いたい場合は、エリア保護専用プラグイン（**WorldGuard**）との併用をおすすめします。
2. **危険アイテムの制限**:
   AntiBuild の `config.yml` にある `alert.on-placement` や `blacklist.placement` を設定することで、TNTやTNT付きトロッコ、ベッド（ネザーでの爆破用）の設置をピンポイントで禁止できます。

---

[← コマンド総合一覧へ戻る](README.md) | [アドオン一覧](README.md#4-公式アドオン解説ページ一覧)
