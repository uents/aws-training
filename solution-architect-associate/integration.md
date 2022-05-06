# インテグレーション

## SNS（Simple Notification Service）
フルマネージド型のpub/subメッセージングサービス

* コンポーネント間のメッセージ通知やアラート通知に利用
* AWS上でイベント通知やメッセージング処理/プッシュ通知をするユースケースで利用

## SQS（Simple Queue Service）
フルマネージド型のメッセージキュイーングサービス

* キューによってシステム処理の水平分散が可能
  - https://aws.amazon.com/jp/blogs/developer/using-python-and-amazon-sqs-fifo-queues-to-preserve-message-sequencing/
* キューに対して優先度を設定することが可能
* 受信側はポーリング通信で受信する

### キューの種類
* 標準キュー（Standardキュー）
  - メッセージの配信順序の保証なし
  - 同一のメッセージが2回配信されることがある
  - TPS（1秒あたりのトランザクション数）の件数は無制限
* FIFOキュー
  - メッセージの配信順序が保証されている
  - 標準キューとは異なり、同一メッセージに2重取得はない
  - TPSの件数は300

## SES
Eメールの送受信機能を提供するサービス

## MQ
Apache ActiveMQ向けのマネージド型メッセージブローカーサービス

## Step Functions
* ワークフローを制御するフルマネージドサービス
* Lambda関数や複数のAWSサービスをプロセスとして配置し、サーバレースのワークフロー作成・管理を実現
* ワークフローの最大実行時間は1年
* ワークフローをマネジメントコンソールのGUIで変更できないSWF（Simple Workflow）というサービスもある
