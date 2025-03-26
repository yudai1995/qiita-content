---
title: CLIを使ったAzure Policy設定手順
tags:
  - Azure
private: false
updated_at: '2025-03-27T02:08:15+09:00'
id: e4ac32e4832c99dd4471
organization_url_name: null
slide: false
ignorePublish: false
---
## はじめに
Azure PolicyをCLIで設定する具体的な手順を解説します。
初めてCLIを使用する方でも操作イメージをつかめる内容です。

### そもそもAzureで使用できるCLIは？
Cloud Shlleもありますがローカル環境から使用する場合は以下2つのどちらかになるかと思います。
本記事ではAzure CLIを使用します。
- [Azure CLI](https://learn.microsoft.com/ja-jp/cli/azure/what-is-azure-cli)
- [Azure PowerShell](https://learn.microsoft.com/ja-jp/powershell/azure/what-is-azure-powershell?view=azps-12.5.0)

### 前提
[Azure CLIはインストール](https://learn.microsoft.com/ja-jp/cli/azure/install-azure-cli)済みとします。
Azure CLIのバージョンは2.70.0を使用しています。

## 手順
今回のシナリオケースとして、すべてのAzureリソースには「環境タグ（Environment）」を付けることを運用ルールとする組織があるとします。
このルールを実現するために、Azureポリシーを設定し、タグが付与されていないリソースの作成を防ぎます。

## ステップ1: 事前準備
### Azureにログインする
以下のコマンドでAzureにログインします
  ```bash
  az login
  ```

### リソースプロバイダーの登録
もし複数のサブスクリプションを管理している場合は以下のコマンドを実行します。作業するサブスクリプションを設定しています。
```bash
az account list --output table
az account set --subscription <subscriptionID>
```

[リソースプロバイダー](https://learn.microsoft.com/ja-jp/azure/azure-resource-manager/management/resource-providers-and-types)が未登録の場合、CLIを使って登録確認と操作を行います。この手順では、対象のリソースプロバイダーが利用可能であるかを確認し、必要に応じて登録を行います。
リソースプロバイダーとはAzureリソースを操作するための機能です。Azure PortalやCLIなどで各操作するとリソースプロバイダーのAPIを介して実行されます。
```bash
# リソースプロバイダーの登録状態確認。StateがRegisteredでない場合は登録が必要
az provider show --namespace Microsoft.PolicyInsights --query "{Provider:namespace,State:registrationState}" --output table

# 登録操作
az provider register --namespace Microsoft.PolicyInsights
```

### リソースグループの作成
適用対象のリソースグループを作成します。<resourceGroupName>には任意のリソースグループ名を入れてください。
```bash
az group create --name <resourceGroupName> --location japaneast
```

### リソースグループIDとポリシー定義名の取得
Azure CLIを使って、[リソースでタグを必須にする](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F871b6d14-10aa-478d-b590-94f262ecfa99)ポリシー定義を検索し、そのIDを取得します
ポリシーの表示名をキーとして以下のようにIDを取得します。
```bash
# リソースグループIDを取得
az group show --resource-group <resourceGroupName> --query id --output table

# ポリシー定義名を取得
az policy definition list --query "[?contains(displayName, 'Require a tag on resources')].name" -o table
```
出力結果から対象ポリシーのIDをメモします。

### リソースグループIDとポリシー定義名を変数に格納
powershellであれば以下のように変数に格納も可能です
```powershell
$rgid = az group show --resource-group testGroup --query id --output tsv

$definition = az policy definition list --query "[?displayName=='Require a tag on resources'].name" --output tsv
```

## ステップ2: ポリシーの割り当て
リソースグループにポリシーを割り当てます。
```bash
az policy assignment create --name "RequireEnvironmentTag" --scope "<リソースグループID>" --policy "<ポリシー定義名>" --params '{\"tagName\":{\"value\":\"Environment\"}}'
```
- `<リソースグループID>`には、前ステップで取得したリソースグループIDを指定します
- `<ポリシー定義名>`には、前ステップで取得したポリシー定義名を挿入。
- nameは任意のポリシー名を指定します。
- paramsは任意のタグ名を指定します

## ステップ3: 動作確認
ポリシーを割り当てたリソースグループにタグの設定を行わずにストレージアカウントを作成してみます。
すると検証に失敗し、タグを付与が必須化されます。
![スクリーンショット 2025-03-27 014018.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1518953/6a983f79-b45f-4c0e-8cb1-b72cd8e3e0bc.png)

## まとめ
Azure CLIを使用してポリシーを設定することで、運用ルールの適用が効率的になります。
例えば、開発環境にタグを付けることで不要なリソースを識別でき、無駄なコストの削減につなげることが可能です。
また、スクリプト化により再利用性することもでき、タグ付けの自動化でリソース管理が簡単になります。

## 参考
https://learn.microsoft.com/ja-jp/azure/governance/policy/assign-policy-azurecli
