# アナリティクス

---
## EMR
* Apache Spark、Apache Hive、Presto などのオープンソース分析フレームワークを使用し、
  大規模な分散データ処理ジョブ、インタラクティブSQLクエリ、
  機械学習 (ML) アプリケーションを実行するフレームワーク
* コンピュートノードはEC2インスタンスを利用して構成される

![](https://d1.awsstatic.com/products/EMR/Product-Page-Diagram_Amazon-EMR.803d6adad956ba21ceb96311d15e5022c2b6722b.png)

---
## Kinesis
主に3つのサービスで構成される。
* Kinesis Data Streams
  - ストリームデータを処理するアプリケーションの構築
* Kinesis Data Firehose
  - ストリームデータをS3・Redshift等へかんたんに配信
* Kinesis Data Analytics
  - ストリームデータを標準的なSQLクエリでリアルタイムに可視化・分析

### Kinesis Data Streams
* ストリーミング処理をシャードに分散することで高速処理が可能
* プロシューマ/コンシューマモデル
  * コンシューマ側でデータの取得（ポーリング）が必要
* パーティションキーを利用することで、割り当てられたシャードに一貫して処理される
* 主な出力先は、Kinesis Firehose、Kinesis Analytics、Lambda、EMR、Apache Storm
* 関連するライブラリ/パッケージ
  * Kinesis Agent
  * Kinesis Producer Library（KPL）
  * Fluent Plugin for Amazon Kinesis
  * Kinesis Data Generator（KGL）
  * Kinesis Client Library（KCL）

### Kinesis Data Firehose
* 各種DBに配信・蓄積されるためのストリーム処理を実施
* Kinesis Data Streamsとの大きな違いは「Zero Admission」
  * EC2でポーリングしたり、Lambdaでコードを書く必要は一切なく、直接出力可能
  * GzipやSnappyといった圧縮アルゴリズムや、KMSを使った暗号化も対応
* 出力先はS3、Redshift、Elastic Search
* データ変換フロー
  * Lambdaと連携することでデータの加工・変換が可能に

![](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2016/12/firehose_transform14.jpg?_ga=2.115691008.724312861.1652593360-1335981390.1652231649)

### Kinesis Analytics
* ストリーミングデータを標準的なSQLクエリでリアルタイムに分析
* 分析したデータの出力先はFirehoseなど
* ただし、ログ解析には向いていない（その場合はEMRなどの別サービスを使用すべき）
