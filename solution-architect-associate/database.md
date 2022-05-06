# データベース
## AWSのデータベースとユースケース
https://qiita.com/leomaro7/items/e48d9941dab5b5f2a718

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F280929%2F55f5c666-9788-3337-d09e-44dd955d4a9c.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&w=1400&fit=max&s=adc449aef758ec67efd22706d327a87c)

---
## RDS
* AWSが提供するマネージドサービス
* MySQL、MariaDB、PostgreSQL、Oracle、Microsoft SQL Severなどのデータベースエンジンから選択可能
  - MySQLのストレージエンジンはInnoDB（MyISAMは選択できない）

### レプリケーションラグ
* Amazon RDS for MySQLのレプリケーションで遅延が発生しているかどうかを確認する方法 | DevelopersIO (classmethod.jp)
  - https://dev.classmethod.jp/articles/how-to-know-how-late-a-replica-in-rds-for-mysql-ver-5-series/
* RDS for Oracle インスタンスのリードレプリカによるレプリケーションラグのトラブルシューティング (amazon.com)
  - https://aws.amazon.com/jp/premiumsupport/knowledge-center/rds-oracle-troubleshoot-replication-lags/

---
## Aurora
* MySQLやPostgreSQL等と互換性がある分散型RDB
* マルチAZで分散されたクラスタ構成により、高速・高性能なRDBを実現
* クエリ処理量が多くOLTPで利用する業務用データベースに最適

### Auroraレプリカ
* 他のリージョンに対してリードレプリカを構築可能
  + AuroraグローバルDB： https://aws.amazon.com/jp/rds/aurora/global-database/
* 概ね1秒以下・最大でも5秒という低レイテンシーでレプリケーションを実現
* マスターに障害が発生した場合、リーダーがマスターに昇格することでフェイルオーバーを実現。（他のRDSにはない機能）

---
## ElastiCache

---
## DynamoDB

### DynamoDB Streams
* DynamoDBの書き込み処理をトリガーにLambda関数を起動
* Lambda関数は最大512MBまでデータを扱うことが可能

---
## Redshift
### Redshiftのアーキテクチャ
出展： https://gihyo.jp/dev/serial/01/redshift/0005

![](https://gihyo.jp/assets/images/dev/serial/01/redshift/0005/thumb/TH400_001.jpg)

* リーダーノード、複数のコンピュートノードからクラスタを構成
* 複数のコンピュートノードをまたがずに処理が完結できる分散構成をいかに作れるかがポイント

### ノードの役割
* リーダーノード
  - クライアントから実行クエリを受け付けて、クエリの解析・実行プランの作成を行い、コンピュートノードに分散して処理を実行させる
  - コンピュートノードの処理結果を受けて、クライアントにレスポンスを返す
* コンピュートノード
  - 計算処理を行うインスタンスおよびストレージから構成
     + インスタンスタイプを設定可能
     + オンデマンドインスタンスとリザーブドインスタンスが設定可能
     + リザーブドインスタンスの場合、1年or3年間の契約。最大75%のコスト削減
     + 自動および手動スナップショットを作成可能。自動スナップショットの空き容量上限に達すると課金が発生。手動スナップショットはストレージ料金が発生。ただし、保持期間の設定変更は可能
  - コンピュートノードを強化することでRedshiftクラスタの性能向上
* ノードスライス
  - コンピュートノード内での分散並列処理の最小単位
  - ノード内のスライス数はコンピューのノードのインスタンスタイプによって異なる
