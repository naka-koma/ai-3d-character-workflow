# AI 3D Character Workflow

[English](README.md) | 日本語

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

## インストール

Node.jsとGitを用意し、[skills CLI](https://github.com/vercel-labs/skills)で導入します。スキル本文とUIメタデータは英語です。

```sh
npx skills add naka-koma/ai-3d-character-workflow
```

画面の案内で、使うエージェント、スキル、インストール範囲を選びます。Codex向けに6つ全てをユーザー共通の配置先へ導入する場合は、次のコマンドを使います。

```sh
npx skills add naka-koma/ai-3d-character-workflow --global --agent codex --skill '*' --yes
```

特定の工程だけなら、`--skill '*'`を`--skill character-base-body`などに替えます。プロジェクト内だけで使う場合は、そのプロジェクトのディレクトリで`--global`を外して実行します。

インストールせず一覧を見るには、次を実行します。

```sh
npx skills add naka-koma/ai-3d-character-workflow --list
```

### 更新

同じ導入コマンドを再実行して、対象のスキルを更新できます。既に同名のスキルがある場合や、導入後に自分で編集した場合は、差分を確認してバックアップを残してから更新してください。

### Claude Codeのプラグインとして導入

yomiyasuと同じく、マーケットプレイスから6つのスキルをまとめて導入できます。Claude Code内で実行します。

```text
/plugin marketplace add naka-koma/ai-3d-character-workflow
/plugin install ai-3d-character-workflow@ai-3d-character-workflow
```

導入後は、`/ai-3d-character-workflow:character-base-body`のように指定します。更新方法は[Claude Codeのプラグイン管理](https://code.claude.com/docs/en/discover-plugins)を参照してください。

### 手動配置

必要な`skills/<skill-name>/`フォルダを、利用するエージェントのスキル配置先へコピーする方法も使えます。スキルを登録せず、各`SKILL.md`を制作手順として読むこともできます。

## 使い方

名前で指定する場合の例です。

```text
$character-base-body を使って、この素体の体型とTポーズを確認してください。
衣装なしの正面・側面と、小さな関節曲げの比較を残してください。
```

全工程を一度に進める必要はありません。見た目や変形に問題があれば、その問題を直す工程へ戻ります。[制作フロー（英語）](docs/workflow.md)に各工程の作業、完了条件、見直す条件をまとめています。

## 対象と検証範囲

特定のキャラクターや3D生成モデルには限定していません。耳や尻尾は追加部位として扱います。SAMやOpenPoseは輪郭・関節位置の推定を補助しますが、それだけで3Dの骨格や自然な変形が完成するとは扱いません。

このリポジトリに含まれるのはスキルと文書です。3D生成モデルの実装、学習済みの重み、キャラクター画像、3Dモデル、実験用のキャッシュは含まれていません。生成や編集を実行するには、選んだ工程に対応するツールを別途用意してください。

スキルのファイル構成と、隔離した環境でのCLIによる一覧取得・導入・再導入を検査済みです。Claude Codeのプラグイン定義は検証を通っていますが、プラグインとしての呼び出しは未検証です。新しいキャラクターで全工程を再実行した検証や、UnityでのGeneric・Humanoidの動作確認はまだ行っていません。

## ライセンス

[MIT License](LICENSE)。このライセンスは本リポジトリのスキルと文書に適用します。制作時に利用する外部モデル、ツール、参照画像、アセットには、それぞれのライセンスを確認してください。
