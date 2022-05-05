# マネジメント/ガバナンス

---
## Elastic Beanstalk
* ウェブアプリケーションの構成管理サービス
* 構築できる構成は大きくは以下の2つ
  1. Webサーバ構成： ELB+Auto Scaling+EC2
  2. Batchワーカー構成： SQS+Auto Scaling+EC2

---
## OpsWorks
* Chefを利用したインフラ構成管理サービス
* スタック・レイヤーの概念が存在
  - スタック： OpsWorksのトップエンティティ。スタック単位こ構成情報をJSON形式で保持する。スタックの下に複数のレイヤーを定義できる
  - レイヤー： スタックのコンポーネントを定義。レイヤーに対してChefのレシピをマッピングすることで詳細な設定が可能

---
## CloudFormation
* AWSリソースを自動構築するためのサービス