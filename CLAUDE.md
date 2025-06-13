# CLAUDE.md

必ず日本語で回答してください。

このファイルは、Claude Code (claude.ai/code) がこのリポジトリで作業を行う際のガイダンスを提供します。

## アーキテクチャ

これはAmazon S3でホストされているzuk2y.comの静的ウェブサイトです。ウェブサイトの構成：

- シンプルなHTML/CSSの個人プロフィールページ
- masterブランチへの変更マージ時にGitHub ActionsによるS3への自動デプロイ
- AWS S3静的ウェブサイトホスティング、CloudFront、Route 53、ACMを使用したコンテンツ配信

## ファイル構造

- `deproy_targets/` - デプロイ可能なウェブサイト資材（HTML、CSS、画像）を格納
  - `index.html` - プロフィール情報を含むメインウェブサイトページ
  - `css/stylesheet.css` - ウェブサイトのスタイリング
  - `img/` - プロフィール画像とその他のアセット
- `.github/workflows/deploy-s3.yml` - S3自動デプロイのためのGitHub Actionsワークフロー

## デプロイ

masterブランチにコードがプッシュされると、ウェブサイトは自動的にS3にデプロイされます。GitHub Actionsワークフローの流れ：
1. `deproy_targets/`ディレクトリの全ファイルをS3バケットに同期
2. `aws s3 sync . s3://zuk2y.com --delete`を使用してバケットの内容を更新
3. GitHubシークレットとして保存されたAWS認証情報が必要

## 開発時の注意事項

- ウェブサイトの変更は全て`deproy_targets/`ディレクトリ内で行う
- サイトはセマンティックHTMLと最小限のCSSスタイリングを使用
- プロフィールセクションは画像とテキストを横並びにするフレックスボックスレイアウトを使用
- ビルドプロセスは不要 - ファイルはそのままS3にデプロイされる