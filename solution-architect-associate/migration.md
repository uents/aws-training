# マイグレーション

## AWS間のマイグレーション
### Data Migration Service（DMS）
* データベースを短期間で安全にAWSに移行することを可能にするサービス

### Data Pipeline
※マイグレーション用途というより、定期的なデータ移行用途かも
* 様々なAWSデータベースやストレージ間のデータの移動と変換を自動化するサービス
* オンプレのデータ移動でも利用可能（Task RunnerというJavaプログラムをインストール）
* https://zenn.dev/mn87/articles/ec0f7dfde1dc43

## AWSへのマイグレーション
### Snowball/Snowball Edge/Snowmobile
* Snowball
  * ペタバイト規模のデータ移行。**現在は非推奨**
* Snowball Edge
  * ペタバイト規模のデータ移行＋コンピューティングとストレージ機能
  * 最大80TB/台の利用が可能（ディスク容量自体は100TB）
  * Compute OptmizedとStrage Optimizedの2種類が存在
* Snowmobile
  * エクサバイト規模のデータ移行

### Application Migration Service（MGN）
![](https://ent.iij.ad.jp/wp-content/uploads/2021/10/aws04_01.png)

* https://ent.iij.ad.jp/articles/2344/
* オンプレミスやその他のパブリッククラウドからのAWSへの移行をサポート
* シンプルな移行プロセスでサーバーをリフトアンドシフト（Lift & Shift）
  * リフトアンドシフト
    * https://aws.amazon.com/jp/application-migration-service/
    * 移行元のサーバの構成変更することなく移行すること。具体的には移行元のサーバにエージェントをインストールし、AWS側から接続してエクスポート/インポートする
* 他の移行サービスよりMGNの利用を推奨。MGNで難しい場合は、CloudEndureやSMSが選択肢に入る
  * https://aws.amazon.com/jp/application-migration-service/when-to-choose-aws-mgn/
  * https://aws.amazon.com/jp/server-migration-service/faqs/

### Server Migration Service（SMS）
![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F129517%2F3cd6ab33-a6f3-dd9a-1b2f-6f72bb612b7c.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&w=1400&fit=max&s=efb8192c56eab6446130b7fc220f270b)

* https://qiita.com/miyuki_samitani/items/5c6586151c02f7ef0cef
* VMware、Hyper-V、Azure上の仮想サーバをAMIとしてAWSに移行することができるサービス
* SMS自体の費用は無料

#### SMSとVM Importの違い
* SMSは、自動化されたサーバ増分レプリケーションに対応
* SMSは、マネコンから状況を確認することができる
* SMSの方がVM Importより推奨されている（ただし、マイグレーションサービスならMGNが最推奨）

### VM Import/Export
既存のオンプレにあるサーバを利用した仮想マシン群を、AWSにインポートおよびAWSからのエクスポートを可能にするサービス

* アプリケーションおよびワークロードをEC2への移行が容易に
* VMイメージカタログをEC2にコピーが可能に
* BCP対策のためにVMイメージのリポジトリを作成可能に

## オンプレミス側の支援
### Application Discovery Service
* オンプレミスのデータセンター内のサーバにエージェントをインストールすることで、
  データセンターの利用情報を収集することができるサービス
* これらの情報にもとづいて、ユーザーの移行プロジェクトの計画作成を支援する

### AWS Outposts
* オンプレミスの形式を取りながら、AWSをクラウド型インフラストラクチャーとして実行できるサービス
* AWSが契約企業内に巨艦サーバを設置する
