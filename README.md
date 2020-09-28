# zuk2y.com

## 本リポジトリ 及び [zuk2y.com](https://zuk2y.com)について

[zuk2y.com](https://zuk2y.com) のデプロイ資材を管理するリポジトリです。

[zuk2y.com](https//zuk2y.com)は[Amazon S3の静的ウェブサイトホスティング機能](https://docs.aws.amazon.com/ja_jp/AmazonS3/latest/dev/WebsiteHosting.html)を用いて構築されています。

Github Actionsを用いた自動デプロイに対応しており、masterブランチへのmergeが発生すると[deproy_targets](https://github.com/zuk2y/zuk2y.com/tree/master/deproy_targets)配下の資材が自動でS3バケットへ配置されます。

## 技術要素

HTML,CSS,AWS(S3,IAM),Github Actions
