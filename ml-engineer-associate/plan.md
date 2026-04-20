# MLA-C01 学習計画

## 前提条件

- SAA-C02 合格済み（AWS基盤サービスの知識あり）
- 機械学習の初歩的な知識あり
- 試験まで 55日（仕上げ目標：35日）
- 推奨学習時間：80〜120時間（2.5〜3.5時間/日）

## 学習教材の選定

### Udemy コース比較

| 項目 | コース1（講義） | コース2（演習） |
|--|--|--|
| タイトル | [【最新】AWS認定 Machine Learning Engineer - Associate 試験対策講座](https://www.udemy.com/course/aws-machine-learning-engineer-associate-japan/) | [MLA-C01 対策テスト4回＋＠](https://www.udemy.com/course/mla-c01-aws-machine-learning-engineer-associate-4/) |
| 形式 | 動画講義（8時間） | 演習テスト専用（355問・6回分） |
| 評価 | 4.6（16件）※新しいコース | 4.2（174件）※合格体験記に多数登場 |
| 最終更新 | 2026/3 | 2026/4 |
| 強み | 4分野を体系的にカバー、MLOps実務視点の解説 | 反復演習で知識定着、合格実績多数 |
| 注意点 | レビュー件数がまだ少ない | 「本番より易しい」との声あり。これだけでは不十分 |

### 推奨の組み合わせ

**両方取り入れることを推奨します。**

コース1と2は「インプット」と「アウトプット」の役割が明確に異なるため、相互補完関係にあります。Skill Builder の公式問題集を加えた以下の3セットが最も効果的です。

| フェーズ | 教材 |
|--|--|
| インプット | Udemy コース1（講義）＋ AWS 公式ドキュメント |
| アウトプット | Udemy コース2（355問）＋ AWS Skill Builder 公式問題集 |
| 仕上げ | AWS Skill Builder Official Practice Exam |

> コース2のみに頼ると本番の難易度とギャップが生じる恐れがあります。  
> Skill Builder 公式問題集（無料）は本番に最も近い形式のため、必ず実施してください。

---

## 学習フェーズとスケジュール（35日間）

### Phase 1：SageMaker 集中理解（1〜12日目）

- [ ] コース1 視聴（全8時間）
- [ ] SageMaker 主要機能の整理（`sagemaker.md` に記録）
  - Training Job / Hyperparameter Tuning / Autopilot
  - Endpoints（リアルタイム / バッチ）
  - Pipelines / Feature Store / Clarify / Model Monitor

### Phase 2：分野別インプット（13〜25日目）

出題比率の高い順に進める。

- [ ] 分野1: データ準備 [28%]（`domain1-data-preparation.md` に記録）
- [ ] 分野4: モニタリング・セキュリティ [24%]（`domain4-monitoring-security.md` に記録）
- [ ] 分野2: モデル開発 [26%]（`domain2-model-development.md` に記録）
- [ ] 分野3: デプロイ・オーケストレーション [22%]（`domain3-deploy-orchestration.md` に記録）

### Phase 3：問題演習と弱点補強（26〜32日目）

- [ ] Udemy コース2 対策テスト①〜④（各1回）
- [ ] Udemy コース2 知識補足問題①②
- [ ] AWS Skill Builder 公式問題集（Official Practice Question Set）
- [ ] 間違えた問題をメモし `weak-points.md` に記録

### Phase 4：総仕上げ（33〜35日目）

- [ ] AWS Skill Builder Official Practice Exam（本番形式）
- [ ] `weak-points.md` を再確認
- [ ] `index.md` の出題範囲と自分のノートのカバレッジを確認

---

## ファイル構成

```
ml-engineer-associate/
├── plan.md                          # 本ファイル：学習計画・進捗管理
├── index.md                         # 試験概要・出題範囲・対象サービス
├── sagemaker.md                     # SageMaker 機能まとめ（Phase 1 の核）
├── domain1-data-preparation.md      # 分野1: MLのためのデータ準備 [28%]
├── domain2-model-development.md     # 分野2: MLモデルの開発 [26%]
├── domain3-deploy-orchestration.md  # 分野3: デプロイとオーケストレーション [22%]
├── domain4-monitoring-security.md   # 分野4: モニタリング・保守・セキュリティ [24%]
├── weak-points.md                   # 演習で間違えた問題・苦手分野のメモ
└── assets/
    ├── exam-coverage.puml
    └── exam-coverage.svg
```

### 各ファイルの記載内容方針

**`sagemaker.md`**

- SageMaker の各機能の概要と使い分け
- よく出る設定パラメータ・制約
- 他サービス（Step Functions・CodePipeline 等）との連携パターン

**`domain*.md`（各分野ノート）**

- タスクステートメントごとの要点
- 関連 AWS サービスとその役割
- よく出るシナリオと正解の選び方
- SAA 知識との差分・注意点

**`weak-points.md`**

- 演習で間違えた問題のキーワード
- 理解が浅かった概念とその補足メモ
- 試験直前の最終確認用チェックリスト
