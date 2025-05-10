---
title: ARMテンプレートについて
tags:
  - Azure
private: true
updated_at: '2025-05-11T00:22:16+09:00'
id: 07f1dcc239cadd325494
organization_url_name: null
slide: false
ignorePublish: false
---
## ARMテンプレートとは
- **ARMテンプレート**はAzureリソースマネージャーテンプレートの略称
- Azureのリソースを**Infrastructure as Code**として実装するためのJSON形式のテンプレート
- このテンプレートファイルを使用してリソースをデプロイすることが可能

## ARMテンプレートのメリット
1. **自動化による効率化**
   - 繰り返し行う作業をテンプレート化することで、エラーやミスを防止
   - 同じテンプレートから一貫性のあるリソースを作成可能

2. **オーケストレーションと並列化**
   - テンプレートファイルを使用して複数リソースを同時並行で作成可能
   - APIが依存関係や作成順序を自動で調整
   - **大量リソース作成時**に特に有効

3. **テストと検証の役割**
   - デプロイ時に依存関係や構成をチェック
   - テンプレートの構成ミスを修正可能
   - 段階的なインフラ構築を支援

## ARMテンプレートの構成要素
- **$schema**: JSONフォーマットを定義したファイルの置き場。基本的なのはAzureリソース。その他サブスクリプション、管理グループ、テナントも作成可能
- **contentVersion**: テンプレートファイルのバージョン管理
- **paraneters**: 仮想マシンのサイズ（SKUSKU）やOS種類などを指定
- **variables**: 変数（例: リソース名のプレフィックスやサフィックス）
- **resources**: 作成するAzureリソースの定義（仮想マシン名、リージョンなど）
- **outputs**: デプロイ結果を出力（例: 作成されたリソースの一覧やIPアドレス）

## クイックスタートテンプレート
- [Azure クイックスタート テンプレート](https://learn.microsoft.com/ja-jp/samples/browse/?expanded=azure&products=azure-resource-manager)
  - コミュニティ提供のテンプレート集
  
## Azure Bicepとは？
- **Azure Bicep**（バイセプ）はAzureリソースをデプロイするための**ドメイン固有言語（DSL）**
- Bicepファイルは最終的に**JSON形式のARMテンプレート**に変換され、Azureリソースをデプロイ可能
- 現在のARMテンプレートはそのまま利用可能で、互換性を担保

## Azure Bicepのメリット
1. **わかりやすい構文**
   - JSONフォーマットよりも簡潔でシンプルにリソースを定義可能
   - 記述量が大幅に削減されるため、読みやすく、管理しやすい

2. **依存関係の自動解決**
   - 仮想マシンやストレージ、ネットワークなどのリソース依存関係を自動解析
   - 作成順序や依存性を考慮する必要が減少

3. **開発の効率化**
   - Visual Studio Codeの拡張機能などが公式提供されており、開発が容易
   - JSONを1から記述する必要がなく、素早い開発が可能

## Azure Bicepの利用シナリオ
- **初めてのテンプレート導入環境**: 初心者でも扱いやすく、導入に適している
- **既存のARMテンプレート運用**: BicepはARMテンプレートに変換されるため、現在の運用との互換性を保持

## Azure Bicep の試験環境
- [Azure Bicep Playground](https://azure.github.io/bicep/)
  - Bicepと、それと同等のJSONを並べて見ることが可能


## 参考文献
https://www.udemy.com/course/az-104-microsoft-azure-administrator-jp/?couponCode=KEEPLEARNING

https://learn.microsoft.com/ja-jp/azure/azure-resource-manager/templates/overview

https://learn.microsoft.com/ja-jp/azure/azure-resource-manager/bicep/overview?tabs=bicep
