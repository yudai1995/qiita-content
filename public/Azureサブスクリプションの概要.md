---
title: Azureサブスクリプションの概要
tags:
  - 'Azure'
private: false
updated_at: ''
id: null
organization_url_name: null
slide: false
ignorePublish: false
---
## はじめに
Azureにはサブスクリプションという効率的な運用に有効な考え方があります。
本記事では、サブスクリプション管理についてまとめます。

## サブスクリプションとは
Azureサブスクリプションは、**課金**と**セキュリティ**の単位として機能します。
- **課金の基盤**: サブスクリプションがすべてのAzureリソース（仮想マシンやストレージなどをまとめるための論理的なくくり）の課金単位となる
- **セキュリティのスコープ**: アクセス権や操作権限を管理する範囲を定義する

## サブスクリプションの種類
Azureには利用シナリオに応じたさまざまなサブスクリプションがあります。

- **[無料試用版](https://azure.microsoft.com/ja-jp/pricing/offers/ms-azr-0044p/)**: 初心者や学習者向けで、30日間$200のクレジットと1年間の無料リソースが利用可能
- **[従量課金](https://azure.microsoft.com/ja-jp/pricing/offers/ms-azr-0003p/)**: 個人開発者や中小規模での利用に適しており、使用した分だけ支払う形式
- **エンタープライズ契約（EA）**: 大企業向けで、ガバナンス機能や割引が充実
- **[Azureインオープン](https://azure.microsoft.com/ja-jp/pricing/offers/ms-azr-0111p/?msockid=34f793eab5be64c33bd4874ab4276500)**: 12カ月有効なクレジットを購入して利用する形式。従量課金の場合、毎月精算するが、インオープンの場合は事前精算となる。検証等など一時的な用途で使用し、決まったタイミングで経費計上したい場合などのシナリオで有効
- **[CSP（クラウドソリューションプロバイダー）](https://azure.microsoft.com/ja-jp/pricing/offers/ms-azr-0145p/)**: パートナーのプロバイダーと契約する形態。Azureと直接の契約ではなく請求やサポートはプロバイダーを通して行うため運用サービスが含まれる場合あり

## [クォーター](https://learn.microsoft.com/ja-jp/azure/quotas/quotas-overview)について
1つのサブスクリプション内で作成できるリソースに上限が設定されています。これをクォーターといいます。
Azure portalのサブスクリプションの使用料＋クォーターから現在の使用状況が確認できます。
![スクリーンショット 2025-03-18 055041.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1518953/0691e3e9-33a8-4d88-aed3-bfb0dd28ef60.png)

### なぜクォーターが必要なのか？
意図せずにリソースが作成されるとその分コストが発生してしまいます。多額な課金を生まないために制限としてクォーターという設けられています。例えば、スクリプトを使用してリソース管理を行いたい場合、スクリプトに誤りがあると繰り返しリソースが作成され続けてしまうケースが考えられます。この予防策として上限が存在します。

### 上限引き上げ依頼
クォーターは意図しないリソース作成の予防策として用意されています。このため必要な場合は上限を引き上げることが可能となっています
以下、Azure portalからのクォーター引き上げのリクエスト画面となります。
![スクリーンショット 2025-03-18 060445.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1518953/cfa73a14-b3e4-45ee-8fad-09ca7ce6366e.png)

## 参考
https://learn.microsoft.com/ja-jp/azure/azure-resource-manager/management/azure-subscription-service-limits

https://learn.microsoft.com/ja-jp/azure/cloud-adoption-framework/ready/landing-zone/design-area/resource-org-subscriptions
