# マネジメント/ガバナンス

## CloudTrail
ユーザー単位でログ証跡を取得・集約

## AWS Organization
AWS Organizationsを使用すると、保有している複数アカウント群をー元的に管理することができる。

### OU（Organization Unit：組織単位）
![](../cloud-practitioner/assets/organization-unit.png)

管理しているアカウントのうちの複数を組織単位（OU：Organization Unit）にグループ化できる。

### SCP（Service Control Policy）
* OUまたは個別アカウントに指定するポリシーで、OU／アカウントで実行できるサービスやアクションを制限できる
* SCPとIAMを組み合わせることで柔軟なアクセス権限の管理が可能に
  - 親アカウントからSCPで大まかに権限を振り、OU（子アカウント）のIAMで細かく権限を振るなど
