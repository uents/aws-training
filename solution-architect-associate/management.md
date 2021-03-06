# マネジメント/ガバナンス

## AWS Organization
AWS Organizationsを使用すると、保有している複数アカウント群をー元的に管理することができる。

### マルチアカウント運用
* https://medium.com/japan-d2/%E3%83%9E%E3%83%AB%E3%83%81aws%E3%82%A2%E3%82%AB%E3%82%A6%E3%83%B3%E3%83%88%E9%81%8B%E7%94%A8%E3%81%AE%E5%A7%8B%E3%82%81%E6%96%B9-2020-18cd636007e2
* ルートAWSアカウント
  * Organizationのメンバーアカウントを取りまとめるアカウント
  * 費用請求などはルートAWSアカウントに集約される
  * アカウント毎の請求も可能
  * 権限が強いアカウントのため通常は利用しない
* AWSアカウント（メンバーアカウント）
  * Origanizationのメンバーアカウント
  * OUで複数の子アカウントを階層的に整理することができる
  * 「IAMアカウント」とも呼ぶ？

### OU（Organization Unit：組織単位）
![](../cloud-practitioner/assets/organization-unit.png)

複数のメンバーアカウントを組織単位（OU：Organization Unit）にグループ化できる。

### SCP（Service Control Policy）
* OUまたは個別のAWSアカウントに指定するポリシーで、OU／アカウントで実行できるサービスやアクションを制限できる
* SCPとIAMを組み合わせることで柔軟なアクセス権限の管理が可能に
  - ルートAWSアカウントからSCPで大まかに権限を振り
  - OU（メンバーアカウント）のIAMで細かく権限を振る、など

### アカウント移動
* Organizationのメンバーアカウントなら、異なる組織に移動させることが可能

### リソースのシェア
* Resource Access Manager（RAM）との連携
  * 組織またはOUでリソースを共有する
* リザーブドインスタンス（RI）の共有
  * アカウントでRIの共有がオンになっていれば、
    Organiizationsを利用した一括請求で、RIが共有される
* ボリュームディスカウント
  * 各メンバーアカウントの総利用料をまとめて、ボリュームディスカウントに反映することができる

## Systems Manager
* 構築済みのインフラストラクチャを可視化し、制御するためのサービス
* 統一されたUIを介して複数のAWSサービスからの運用データを表示し、運用タスクを自動化することが可能

## Trusted Advisor
* AWS環境を検査し、AWSのベストプラクティスに基づいてリアルタイムの推奨事項を提供するサービス
* 評価する5つのカテゴリ
  - コスト最適化
  - パフォーマンス
  - セキュリティ
  - 耐障害性
  - サービスの制限

![](https://d1.awsstatic.com/support/jp/Trusted%20Advisor%20best%20practice%20checks%20categories.76a13b0b2bf982c874d0d03e6138b7b73e45680c.png)

## AWS Config
![](https://d1.awsstatic.com/Products/product-name/diagrams/product-page-diagram-Config_how-it-works.bd28728a9066c55d7ee69c0a655109001462e25b.png)

* AWSリソースの設定から、AWSリソースの構成情報のスナップショットを取得・管理
* この構成情報を元に、現状のAWSリソースの設定が、利用者によって定義された正しい状態になっているかを評価

## AWS Backup
![](https://d1.awsstatic.com/product-marketing/AWS%20Backup/AWS-Backup-Resources-diagram-2x.d8263a085153f2825ce52a3f814393b6c5559747.png)

* AWS Storage Gatewayを使用して、オンプレミスおよびAWS サービス全体のデータのバックアップの一元化と自動化を簡単に実行できる、完全マネージド型のバックアップサービス
* バックアップポリシーを一元的に設定し、Amazon EBSボリューム、Amazon RDSデータベース、Amazon DynamoDBテーブル、Amazon EFSファイルシステム、AWS Storage GatewayボリュームなどのAWSリソースのバックアップアクティビティを監視
