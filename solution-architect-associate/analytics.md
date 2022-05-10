# アナリティクス

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
* コンシューマ/プロシューマモデル
* パーティションキーを利用することで、割り当てられたシャードに一貫して処理される
* 主な出力先：Kinesis Firehose、Kinesis Analytics、Lambda、EMR、Apache Storm
* 関連するライブラリ/パッケージ
  * Kinesis Agent
  * Kinesis Producer Library（KPL）
  * Fluent Plugin for Amazon Kinesis
  * Kinesis Data Generator（KGL）
  * Kinesis Client Library（KCL）

### Kinesis Data Firehose
* 各種DBに配信・蓄積されるためのストリーム処理を実施
* Lambdaと連携するとETLとしても機能する
* 出力先はS3、Redshift、Elastic Search

### Kinesis Analytics
* ストリーミングデータを標準的なSQLクエリでリアルタイムに分析
* 分析したデータの出力先はFirehoseなど
* ただし、ログ解析には向いていない（その場合はEMRなどの別サービスを使用すべき）
