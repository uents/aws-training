# インテグレーション

## SNS（Simple Notification Service）

## SQS（Simple Queue Service）
* キューによってシステム処理の水平分散が可能
  - https://aws.amazon.com/jp/blogs/developer/using-python-and-amazon-sqs-fifo-queues-to-preserve-message-sequencing/
* キューに対して優先度を設定することが可能

### キューの種類
* 標準キュー（Standardキュー）
  - メッセージの配信順序の保証なし
  - 同一のメッセージが2回配信されることがある
  - TPS（1秒あたりのトランザクション数）の件数は無制限
* FIFOキュー
  - メッセージの配信順序が保証されている
  - 標準キューとは異なり、同一メッセージに2重取得はない
  - TPSの件数は300
