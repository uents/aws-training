# マネジメント/ガバナンス

---
## Auto Scaling
* システムの利用状況（設定した閾値やヘルスチェックの結果）によって、インスタンスの台数を自動的に増減させるサービス
* ただし、閾値を超えたにも関わらずスケーリングが上手く実行されずに24h以上経過した場合、自動的にAuto Scalingが停止するようになっている

> 詳細は https://docs.aws.amazon.com/ja_jp/autoscaling/ec2/userguide/as-suspend-resume-processes.html を参考


