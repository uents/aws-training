# データベース
## AWSのデータベースとユースケース
https://qiita.com/leomaro7/items/e48d9941dab5b5f2a718

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F280929%2F55f5c666-9788-3337-d09e-44dd955d4a9c.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&w=1400&fit=max&s=adc449aef758ec67efd22706d327a87c)

---
## RDS
* AWSが提供するマネージドサービス
* MySQL、MariaDB、PostgreSQL、Oracle、Microsoft SQL Severなどのデータベースエンジンから選択可能
  - MySQLのストレージエンジンはInnoDB（MyISAMは選択できない）

### マルチAZ
* 別AZにセカンダリーDBを作成することで、BCP対策が可能に
* 別リージョンにセカンダリーDBを作成することはできない（リードレプリカなら別リージョンへも可能）

### レプリケーションラグ
* Amazon RDS for MySQLのレプリケーションで遅延が発生しているかどうかを確認する方法 | DevelopersIO (classmethod.jp)
  - https://dev.classmethod.jp/articles/how-to-know-how-late-a-replica-in-rds-for-mysql-ver-5-series/
* RDS for Oracle インスタンスのリードレプリカによるレプリケーションラグのトラブルシューティング (amazon.com)
  - https://aws.amazon.com/jp/premiumsupport/knowledge-center/rds-oracle-troubleshoot-replication-lags/

### RDS Proxy
* https://aws.amazon.com/jp/rds/proxy/
* アプリケーションとRDSデータベースの仲介役として機能
* 必要となるデータベースへのコネクションプールを確立・管理し、アプリケーションからのDB接続を少なく抑える機能

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
## Redshift
* マネージド型のDWH（データウェアハウジング）サービス
* 多くのソースからデータを収集し、データ全体の関係性や傾向を理解するのに役立つ機能を提供
* BI（ビジネスインテリジェンス）アプリケーションのの用途で活用

### Redshiftのアーキテクチャ
![](https://gihyo.jp/assets/images/dev/serial/01/redshift/0005/thumb/TH400_001.jpg)

* https://gihyo.jp/dev/serial/01/redshift/0005
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

### 拡張VPCルーティング
* VPC内にデータ移動を制御する機能

### クロスリージョンスナップショット
* クラスタのプライマリリージョンでスナップショットが作成されると、セカンダリリージョンにコピーされる
* プライマリリージョンのクラスタがダウンした場合、セカンダリリージョンでクラスタを即座に復元できる



---
## DynamoDB
サーバレスのキーバリューデータベースサービス
* プロビジョニング、パッチ適用、管理等が不要
* 自動的にスケーリング

### DynamoDB Streams
* DynamoDBの書き込み処理をトリガーにLambda関数を起動
* Lambda関数は最大512MBまでデータを扱うことが可能

### DynamoDB Accelerator（DAX）
* インメモリキャッシュを利用しクエリを高速化（ms→usオーダー）

### DynamoDB Auto Scaling
* Auto Scalingにより、負荷に応じてWCU/RCUのスループットを自動調整

### DynamoDBとRDSの違い

| 項目	| DynamoDB | RDS |
| --- | --- | --- |
| タイプ | 非リレショーナル | リレーショナル |
| データ構造 | Key-Value Store | SQL |
| サービス形態 | サーバレス | マネージド |
| スケーリング | 水平スケーリング | 垂直スケーリング[※1] |
| トランザクション | 結果整合性を保証 | ACID準拠 |
| アクセス性能 | 大量のアクセスでも性能維持 | 大量のアクセスには不向き[※2] |

* [※1] リードレプリカの増設によりある程度は対応可能
* [※2] RDS Proxyにコネクションプールを管理させることによりある程度は対応可能

---
## ElastiCache
* インメモリ・データストアサービス
* RedisとMemcachedのマネージドサービスとして使用可能
* 具体的な用途
  + アプリケーションのセッション情報
  + DBのクエリ結果のキャッシュ
