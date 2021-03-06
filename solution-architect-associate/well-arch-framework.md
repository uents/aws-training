# Well-Architected Framework

## 6つの設計原則

SAA試験はWell-Architected Frameworkで提唱されている設計原則に沿った試験範囲になっている。

* Reliability：信頼性
* Peformance Efficiency：パフォーマンス効率
* Security：安全性
* Cost Optimization：コスト最適化
* Operational Excellence：運用上の優秀性
* Sustainability：持続可能性

> 持続可能性は2021年12月に追加された新しい項目

## 11のベストプラクティス
設計原則の具体例は **ベストプラクティス** として公開されており、AWSホワイトペーパー等により確認・学習が可能

![](../cloud-practitioner/assets/well-architected-framework.svg)

| | 項目 | 内容 | 関連サービス |
|--|--|--|--|
| 1 | スケーラビリティの確保 | 需要の変化に対応できるアーキテクチャを設計 | Auto Scaling、CloudWatch、RDS、DynamoDB |
| 2 | 環境の自動化 | システムの安定性・整合性及び組織の効率性を改善するため主要プロセスを自動化する | CloudFormation、Codeシリーズ、ElasticBeanstalk、OpsWorks、ECS |
| 3 | 使い捨てリソースの使用 | サーバーなどのコンポーネントを一時的なリソースとして利用・設計 | EC2、Auto Scaling |
| 4 | コンポーネントの疎結合 | コンポーネント間の相互依存を減らした構成とし、１つのコンポーネント変更や障害の影響を削減 | ELB、SNS、SQS |
| 5 | サーバレス | マネージド型サービスとサーバレスアーキテクチャにより、効率的な設計と運用を実現 | マネージド型サービス全般 |
| 6 | 最適なデータベース選択 | ワークロードに応じた最適なデータベース技術を利用 | RDS、Aurora、Redshift、DynamoDB、ElasticSearch |
| 7 | 増大するデータ量対応 | IoT/ビッグデータなどで絶えず増加するデータの保持を効率的に実施する | S3、Glacier、Kinesis |
| 8 | 単一障害点(SPOF)の排除 | AWSのサービスの多くは高可用が保証されているものが多いが、そうでないものはELBやマルチAZによる高可用設計が必要 | |
| 9 | コスト最適化 | リソースが適切なサイズから必要に応じたスケールアウト・スケールインの実施と最適な料金プランの選択する | EC2購入プラン、Auto Scaling、Trusted Advisor |
| 10 | キャッシュの利用 | 繰り返し取り出すデータやコンテンツについてはキャッシュを利用する構成とする | CloudFront、ElastiCache |
| 11 | セキュリティの確保 | 全てのレイヤー・境界・リソース内/間においてセキュリティを実装する | ほぼすべてのリソース |

### 設計原則の関係と試験範囲の関係

| 原則 | 分野 | 比率 |
| --- | --- | --- |
| Reliability：信頼性 | 1.弾力性（レジリエント）に優れたアーキテクチャ設計 | 30% |
| Peformance Efficiency：パフォーマンス効率 | 2.高パフォーマンスなアーキテクチャ設計 | 28% |
| Security：安全性 | 3.セキュアなアプリケーションとアーキテクチャ設計 | 24% |
| Cost Optimization：コスト最適化 | 4.コストを最適化したアーキテクチャ設計 | 18% |
| Operational Excellence：運用上の優秀性 | （C01での出題範囲） | - |
| Sustainability：持続可能性 | - | - |

## Reliability：信頼性

* 障害による中断・停止と障害復旧による影響を計銀するインフラを構成する
* 設計事項
  - 復旧手順のテスト検証
  - 障害復旧の自動化などの軽減設計
  - 需要変化に応じたスケーラビリティ・高可用性の確保
  - キャパシティの推測が不要であること
  - 変更管理・モニタリングと自動化の推進

> この「高可用性」「回復性の高い」アーキテクチャが試験でもいちばん配点が高い

信頼性の主要サービス

| 領域 | サービス |
| --- | --- |
| 基盤 | IAM, VPC, Auto Scaling, ELB, AMI |
| 変更管理 | CloudFormation, OpsWork, AWS Config |
| 障害管理 | CloudWatch |

### 高可用性
* 高可用性（High Availability）=アーキテクチャにより自動でシステムのダウンタイムを限りなく0にすること
* 方法
  1. 高可用なサービスの利用
      * AWSサービスの多くはAWS側で高可用に設計されている
      * 例えばS3のイレブンナインの耐久性は、高可用設計の代表例
  2. 高可用なアーキテクチャ設計
      * 一部のサービスはユーザー側で設計する必要がある（ex. EC2,RDS,IPフローティング,EMR,Direct Connect）
      * そのままだと単一障害点となるため、ユーザー側で排除する必要がある
* 高可用性の非機能要件
  * RTO：Recovery Time Objective（目標復旧時間）
    * いつまでにシステムが復旧するかという目標時間を表す指標
  * RPO：Recovery Point Objective（目標復旧時点）
    * システム障害などでデータが損壊した際に復旧するバックアップデータの古さの目標
  * 耐障害性
    * アプリケーションのコンポーネントに組み込まれた冗長性
  * 復元可能性
    * システム障害/災害発生時におけるサービス復旧に係る機能/プロセス/ポリシー
  * 拡張性
    *  既存設計・構成において、アプリケーションの拡張性を確保する能力
* AWSにおける高可用性の実現
  * サービス配置
    * リージョン、AZ、VPC設計
  * サービス機能の活用
    * Route53によるフェールオーバー
    * ELBによるロードバランシング
    * Auto Scalingによるスケーラビリティ
    * Lambdaによるスケーリング
    * ElastiCacheを活用したキャッシュアクセス
    * CloudWatchによるモニタリング
  
### DR（Disaster Recovery）構成
障害復旧対応に向けた方式は様々あり、用途に応じて準備する。

| 方式 | 内容 |
| --- | --- |
| ホットスタンバイ | 本番サーバ/予備サーバが常時稼働しており、本番に問題が発生した場合に即座に予備に切り替える |
| コールドスタンバイ | 予備サーバには必要なデータ・機材がひと通り準備されているが、稼働されていない状態でスタンバイしておく |
| ウォームスタンバイ | 本番サーバ/予備サーバが同じ形で用意されているが、切り替え（復旧）には何らかの作業が必要（例えばDNS切り替えなど） |
| バックアップ＆リストア | バックアップを定期的に実施し、本番に異常が発生した場合はリストアする |
| パイロットライト | 停止した状態のサーバを別のリージョンに用意しておき、障害発生時に立ち上げる（例えばDBのレプリケーション） |
| マルチサイト | 別のリージョンに本番サーバと同じ構成のシステムを常時稼働しておく |

## Peformance Efficiency：パフォーマンス効率

* システム要件に対するリソースの最適化によるインフラの効率化
* 設計事項
  - システム要件を満たすためのコンピューティングリソースの効率化
  - システム要件やAWSサービスの進化の応じて、AWSインフラの効率化を推進
    + 先端技術のコモディティ化
    + グローバル化を迅速に達成
    + サーバレスアーキテクチャの利用
    + より頻繁な実験（素振り）

パフォーマンス効率の主要なサービス

| 領域 | サービス |
| --- | --- |
| コンピューティング | Auto Scaling, Lambda |
| ストレージ | EBS, S3, Glacier, EFS |
| データベース | RDS, DynamoDB, Aurora Redshift |
| 容量と時間のトレードオフ | CloudFront, ElastiCache |

## Security：安全性

* AWS内のデータ/システム/アセットの保護・モニタリングによりセキュリティを高める
* 設計事項
  - すべてのレイヤーにおいてセキュリティを適用
  - アクセス追跡・モニタリングの確実な実施
  - 条件ドリブンのアラートなどのセキュリティイベントの応答自動化
  - AWS責任共有モデルに基づく対象範囲の保護に集中
  - セキュリティのベストプラクティスの自動化

セキュリテイの主要サービス

| 領域 | サービス |
| --- | --- |
| データ保護 | ELB, EBS, S3, RDS, KMS |
| 権限管理 | IAM, MFA |
| インフラ保護 | VPC |
| 検出制御 | CloudTrail, CloudWatch, AWS GuardDuty, AWS Inspector |

## Cost Optimization：コスト最適化

* 不要なリソースの削減、最適料金選択によるコスト削減
* 設計事項
  - 不必要なリソース削減
  - 透明性のある費用賦課
  - マネージド型サービスの利用によるコスト削減
  - 固定の償却コストを変動コストに転換
  - スケールによるコストメリット
  - データセンターへの投資不要化

コスト最適化の主要サービス

| 領域 | サービス |
| --- | --- |
| 需給一致 | Auto Scaling |
| コスト効率の高いリソース | EC2購入方式、Trusted Advisor |
| 支出の認識 | CloudWatch、見積もりツール |
| 継続した最適化 | AWS最新情報、Trusted Advisor |

## Operational Excellence：運用上の優秀性

* 計画変更が起こった場合、予期せぬイベントの発生時において、自動化された運用実務および文書化・テスト化およびレビューされた手順があること
* 設計事項
  - コードに基づく運用実施
  - ビジネス目的に沿った運用手順
  - 定期的かつ小規模で増加的な変更実施
  - 予期せぬイベントと障害からの学習
  - 運用手順を最新のものに保持すること

運用上の優秀性の主要サービス

| 領域 | サービス |
| --- | --- |
| 準備 | CloudFormation, Codeシリーズ |
| 運用 | Systems Manager, CloudTrail, AWS GuardDuty, CloudWatch, AWS Config, API Gateway |
| 進化 | 継続的かつ段階的な改善のために、時間とリソースを割り当て、運用の有効性と効率性を向上させる |

## Sustainability：持続可能性

* 2021年12月に6本目の柱として追加
* サステイナビリティの目標
  * インフラに関するエネルギー使用率を80%削減
  * ユーザー側はクラウドを利用した効率的なアプリケーション設計やサービス選択を実施
* サステイナビリティのベストプラクティス
  * ワークロードの地理的配置の最適化
  * 時間/リソースを最も多く消費するコード領域の最適化
  * ユーザーのデバイスや機器への影響を最適化
  * データ分類ポリシーを実装
    * 重要度と機密性に基づいてデータをカテゴリ別に分類し、各カテゴリに適した保護と保持方法によりデータを管理すること
  * ネットワーク間でのデータ移動を最小化
  * GPU使用を最適化
  * 潜在的なサステイナビリティの改善を迅速に導入できる開発手法・テスト方法の採用
  * ビルド環境の使用率を向上

