# MLA-C01 学習計画

## 前提条件

- SAA-C02 合格済み（AWS基盤サービスの知識あり）
- 機械学習の初歩的な知識あり
- 試験まで 55日（仕上げ目標：35日）
- 推奨学習時間：65〜90時間（1.9〜2.6時間/日）

## 学習教材の選定

### Udemy コース比較

| 項目 | コース1（講義） | コース2（演習） |
| --- | --- | --- |
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
| --- | --- |
| インプット | Udemy コース1（講義）＋ AWS 公式ドキュメント |
| アウトプット | Udemy コース2（355問）＋ AWS Skill Builder 公式問題集 |
| 仕上げ | AWS Skill Builder Official Practice Exam |

> コース2のみに頼ると本番の難易度とギャップが生じる恐れがあります。  
> Skill Builder 公式問題集（無料）は本番に最も近い形式のため、必ず実施してください。

---

## 学習フェーズとスケジュール（35日間）

### Phase 1：SageMaker 集中理解（1〜6日目）

**目安学習時間：12〜16時間**

| 内容 | 目安時間 |
| --- | --- |
| コース1「機械学習モデルのトレーニング」視聴＋ノート | 4〜5時間 |
| コース1「デプロイと自動化」視聴＋ノート | 4〜5時間 |
| Black Belt（SageMaker 全般・Pipelines・Model Monitor・Clarify）視聴＋整理 | 4〜6時間 |

**コース1 対応セクション**

| セクション | 内容 | 動画時間 | 目安学習時間 |
| --- | --- | --- | --- |
| 機械学習モデルのトレーニング | Training Job・HPT・Autopilot・Endpoints | 約2時間6分 | 約4〜5時間 |
| デプロイと自動化 | Endpoints・Pipelines・CodePipeline 連携 | 約1時間52分 | 約4〜5時間 |

> 「はじめに」「機械学習について」は ML 基礎知識ありのため視聴スキップ可。

- [ ] コース1 上記2セクション視聴
- [ ] SageMaker 主要機能の整理（`sagemaker.md` に記録）
  - Training Job / Hyperparameter Tuning / Autopilot
  - Endpoints（リアルタイム / バッチ）
  - Pipelines / Feature Store / Clarify / Model Monitor

### Phase 2：分野別インプット（7〜25日目）

**目安学習時間：29〜42時間**

**コース1 対応セクション**

| 分野 | コース1 セクション | 動画時間 | 目安学習時間 |
| --- | --- | --- | --- |
| 分野1: データ準備 [28%] | 機械学習のためのデータ準備 | 約2時間5分 | 約4〜5時間 |
| 分野2: モデル開発 [26%] | 機械学習モデルのトレーニング | 約2時間6分（Phase 1 視聴済み → ノート整理中心） | 約2〜3時間 |
| 分野4: モニタリング・セキュリティ [24%] | モデルの運用保守とセキュリティ | 約1時間26分 | 約3〜4時間 |
| 分野3: デプロイ・オーケストレーション [22%] | デプロイと自動化 | 約1時間52分（Phase 1 視聴済み → ノート整理中心） | 約2〜3時間 |

出題比率の高い順に進める。

- [ ] 分野1: データ準備 [28%]（`domain1-data-preparation.md` に記録）
- [ ] 分野4: モニタリング・セキュリティ [24%]（`domain4-monitoring-security.md` に記録）
- [ ] 分野2: モデル開発 [26%]（`domain2-model-development.md` に記録）
- [ ] 分野3: デプロイ・オーケストレーション [22%]（`domain3-deploy-orchestration.md` に記録）

### Phase 3：問題演習と弱点補強（26〜32日目）

**目安学習時間：18〜22時間**

| 内容 | 目安時間 |
| --- | --- |
| Udemy コース2 対策テスト①〜④（解答＋見直し） | 各2.5〜3時間 × 4回 ＝ 10〜12時間 |
| Udemy コース2 知識補足問題①②（解答＋見直し） | 各1.5〜2時間 × 2回 ＝ 3〜4時間 |
| AWS Skill Builder 公式問題集（解答＋見直し） | 4〜5時間 |
| `weak-points.md` への記録 | 上記見直しに含む |

- [ ] Udemy コース2 対策テスト①〜④（各1回）
- [ ] Udemy コース2 知識補足問題①②
- [ ] AWS Skill Builder 公式問題集（Official Practice Question Set）
- [ ] 間違えた問題をメモし `weak-points.md` に記録

### Phase 4：総仕上げ（33〜35日目）

**目安学習時間：6〜8時間**

| 内容 | 目安時間 |
| --- | --- |
| AWS Skill Builder Official Practice Exam（本番形式） | 2〜3時間 |
| `weak-points.md` 再確認・弱点補強 | 3〜4時間 |
| カバレッジ確認・最終整理 | 1時間 |

- [ ] AWS Skill Builder Official Practice Exam（本番形式）
- [ ] `weak-points.md` を再確認
- [ ] `index.md` の出題範囲と自分のノートのカバレッジを確認

### 所要時間合計

| フェーズ | 日数 | 目安学習時間 | 日平均 |
| --- | --- | --- | --- |
| Phase 1: SageMaker 集中理解 | 6日 | 12〜16時間 | 2.0〜2.7時間 |
| Phase 2: 分野別インプット | 19日 | 29〜42時間 | 1.5〜2.2時間 |
| Phase 3: 問題演習と弱点補強 | 7日 | 18〜22時間 | 2.6〜3.1時間 |
| Phase 4: 総仕上げ | 3日 | 6〜8時間 | 2.0〜2.7時間 |
| **合計** | **35日** | **65〜88時間** | **1.9〜2.5時間** |

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

---

## 参考資料

サービスの概略をつかむことを優先し、API ドキュメントや料金表などは優先度低めで取り組む。

### 導入リソース（全フェーズ共通）

初めて触れるサービスはまずこちらで概略をつかむ。

| 資料 | 概要 |
| --- | --- |
| [AWS Skill Builder](https://skillbuilder.aws/) | 各サービスの 1〜2 時間の無料入門コース。日本語対応あり。`Amazon SageMaker Getting Started` が特に有用 |
| [AWS デジタルコース - Learn About AI](https://aws.amazon.com/jp/training/learn-about/ai/) | 動画＋ハンズオン形式。AI/ML の基礎概念を学べる |

### SageMaker（Phase 1 全般）

| 資料 | 概要 |
| --- | --- |
| [AWS Black Belt - Amazon SageMaker 基礎編](https://aws.amazon.com/jp/blogs/news/2026-03-aws-blackbelt/) | SageMaker 全体像・各機能の使い分け |
| [AWS Black Belt - SageMaker Model Monitor](https://youtu.be/Q-vTO1_QjMs?si=IQ0gsHVBfhzEZ2S4) | モデルドリフト・データドリフト検出 |

### 分野1: データ準備

| 資料 | 概要 |
| --- | --- |
| [AWS Black Belt - AWS Glue](https://www.youtube.com/watch?v=5fbdx849AYw) | ETL・Data Catalog・DataBrew の全体像 |

### 分野2: モデル開発

| 資料 | 概要 |
| --- | --- |
| [雲勉@オンライン【勉強会】Amazon SageMaker 入門 〜組み込みアルゴリズムで機械学習を試してみよう〜【開発エンジニア向け】](https://www.youtube.com/watch?v=aC_FG4mnasw) | アルゴリズム選択の判断基準 |

### 分野3: デプロイ・オーケストレーション

| 資料 | 概要 |
| --- | --- |
| [AWS Black Belt - AWS Step Functions](https://www.youtube.com/watch?v=PGyasNJ1QTQ) | ML ワークフローのオーケストレーション |
| [AWS Black Belt - AWS CodePipeline 基礎編](https://www.youtube.com/watch?v=L7rKC81dYrU) | CI/CD パイプラインの概念 |

### 分野4: モニタリング・セキュリティ

| 資料 | 概要 |
| --- | --- |
| [AWS Black Belt - Amazon CloudWatch 概要と基本](https://www.youtube.com/watch?v=fzVkJne3OMI) | メトリクス・ログ・アラームの設計 |
| [AWS Black Belt - AWS IAM](https://www.youtube.com/watch?v=K7F5yTThynw) | 最小権限設計・ロールの使い分け（SAA 復習） |
| [AWS Black Belt - Amazon Macie](https://www.youtube.com/watch?v=I7slUbShAqM) | PII 検出・ML データの機密性管理 |
