# stamprecord_page
StampRecordのプロダクトページ

デプロイ先: https://kyome.io/stamprecord/index.html

## S3自動デプロイ

`main`へのpushまたはActionsの「Deploy to S3」を手動実行すると、Node.js 24.22.1 / npm 12.2.1でビルドします。リポジトリ変数 `AWS_DEPLOY_ENABLED` を `true` にすると、ビルド成功後に `s3://kyome.io/stamprecord/` へ配置し、CloudFrontの対象パスを更新します。AWS認証はOIDCを使用します。

AWS側の初回設定は [共通CloudFormationテンプレート](https://github.com/Kyome22/kyome_portfolio_react_ts/blob/main/.github/aws/deploy-stack.json) を使用します。東京リージョンのアカウント `723484802208` でスタックを作成し、名前付きIAMリソースの作成を許可してください。既存のGitHub OIDCプロバイダーがある場合は、そのARNを `ExistingOidcProviderArn` に指定します。スタック作成完了後に上記変数を有効にしてください。

アセットを先に、`index.html` を最後にアップロードします。共有バケット内の他ページや旧アセットを削除しない構成です。公開途中の更新は完全な一括切り替えではありません。
