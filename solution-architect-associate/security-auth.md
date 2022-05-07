# セキュリティ/権限管理/コンプライアンス

## IAM
### タグを条件としたIAMポリシー
* https://aws.amazon.com/jp/premiumsupport/knowledge-center/iam-ec2-resource-tags/
* IAMポリシーでEC2インスタンス等のリソースタグを条件に加えることで、例えば本番環境/開発環境ごとに運用ポリシーを変えることが可能に

### VPCを条件としたIAMポリシー
* https://qiita.com/ijin/items/8c53735ee5671cadbf2c
* IAMポリシーでEC2インスタンス等のリソースタグを条件に加えることで、例えば本番環境/開発環境ごとに運用ポリシーを変えることが可能に

---
## Directory Service
https://aws.amazon.com/jp/directoryservice/
![](https://d1.awsstatic.com/Products/product-name/diagrams/directory_service_howitworks.80bfccbf2f5d1d63558ec3c086aff247147258f1.png)

* Active Directory Connector
  * Micrsoft Active Diectoryへのリクエストを処理するゲートウェイサービス

---
## CloudHSM
* HSMはゼロ化してキーを失ってしまうと、コピーを有していない場合は新しいキーは取得不可能となる

---
## STS（Security Token Service）
限定的かつ一時的にセキュリティ認証情報を提供するサービス

* AWSサービスへのアクセスの提供
  * サービスロールを設定してアクセス権限を付与
* 別のAWSアカウントへのアクセス許可
  * クロスアカウントアクセス設定
* 外部で認証されたユーザー（IDフェデレーション）へのアクセス許可
  * ウェブIDフェデレーション
    * Amazon CognitoやOpenID Connectにより認証されたユーザー
  * SAML2.0フェデレーション
    * エンタープライズ系で利用？ IdPの認証情報を信頼する

> 参考リンク
> https://qiita.com/fjisdahgaiuerua/items/c8183dc19e95d9e13d4b

---
## WAF（Web Application Firewall）
https://aws.amazon.com/jp/waf/

![](https://d1.awsstatic.com/products/WAF/product-page-diagram_APIv2-AWS-WAF_How-it-Works-2x.1cafa052deabb5ca8500ce9565209f0f97725482.png)

