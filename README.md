# AI 3D Character Workflow

AIで生成したキャラクターの部品を、編集やアニメーションに使える3Dモデルへ整えるためのスキル集です。参照画像の分析から素体、顔、衣装、リグ、布の揺れまでを6つの工程に分けています。

画像からの3D生成とBlender MCPによる組み立てを試したところ、一連の操作はできました。一方で、顔や手足の細部、関節の変形、衣装の動きには問題が残りました。このリポジトリでは、作業手順に加えて、各工程の完了条件と見直す条件を記録しています。

## スキル

| 工程 | スキル | 主な確認事項 |
|---|---|---|
| 参照画像・三面図 | [character-reference-analysis](skills/character-reference-analysis/SKILL.md) | 部位の輪郭、関節候補、左右、寸法と接合位置 |
| 素体 | [character-base-body](skills/character-base-body/SKILL.md) | 体型、厚み、Tポーズ、関節位置 |
| 顔・手足 | [character-face-hands](skills/character-face-hands/SKILL.md) | 細部の造形、テクスチャ、開閉や曲げ |
| 衣装・追加部品 | [character-clothing-fit](skills/character-clothing-fit/SKILL.md) | 素体を保った組み立て、接合と余裕 |
| リグ・動作 | [character-rig-motion](skills/character-rig-motion/SKILL.md) | ウェイト、足IK、接地、歩行 |
| 布・二次動作 | [character-cloth-secondary-motion](skills/character-cloth-secondary-motion/SKILL.md) | 揺れ、干渉、保存後の再生 |

## 使い方

必要な工程のスキルを選び、そのフォルダを利用するエージェントのスキル配置先へコピーします。既に同名のスキルがある場合は、差分を確認してから更新してください。スキルを登録せず、各`SKILL.md`を制作手順として読むこともできます。

名前で指定する場合の例です。

```text
$character-base-body を使って、この素体の体型とTポーズを確認してください。
衣装なしの正面・側面と、小さな関節曲げの比較を残してください。
```

全工程を一度に進める必要はありません。見た目や変形に問題があれば、その問題を直す工程へ戻ります。[制作フロー](docs/workflow.md)に工程間の関係を、[実験で分かったこと](docs/lessons.md)にスキルの元となった観察をまとめています。

## 対象と検証範囲

特定のキャラクターや3D生成モデルには限定していません。耳や尻尾は追加部位として扱います。SAMやOpenPoseは輪郭・関節位置の推定を補助しますが、それだけで3Dの骨格や自然な変形が完成するとは扱いません。

このリポジトリに含まれるのはスキルと文書です。3D生成モデルの実装、学習済みの重み、キャラクター画像、3Dモデル、実験用のキャッシュは含まれていません。生成や編集を実行するには、選んだ工程に対応するツールを別途用意してください。

スキルのファイル構成は検査済みです。新しいキャラクターで全工程を再実行した検証や、UnityでのGeneric・Humanoidの動作確認はまだ行っていません。

## ライセンス

[MIT License](LICENSE)。このライセンスは本リポジトリのスキルと文書に適用します。制作時に利用する外部モデル、ツール、参照画像、アセットには、それぞれのライセンスを確認してください。
