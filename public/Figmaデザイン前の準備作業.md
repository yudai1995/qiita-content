---
title: Figmaデザイン前の準備作業
tags:
  - Figma
private: false
updated_at: '2025-04-05T00:09:14+09:00'
id: c633c9429547692bf4fb
organization_url_name: null
slide: false
ignorePublish: false
---
## はじめに
ワイヤーフレームの作成のためにFigmaを使いました。
この記事では、基本操作を簡単にまとめ、初心者の方でもわかりやすいように解説します。

### 実施すること
ワイヤーフレームを作成するにあたり、以下の準備作業を行います
- フレームで土台を作る
- グリッドを利用して補助線を引く
- グリッドに制約を設定する（土台フレームのサイズを変更した際にグリッドも追従させる）

## フレーム
Figmaのフレームは、デザイン作業の基盤となる枠組みとなります。  
この上にコンテンツやUIパーツを配置していきます。  
PhotoshopやIllustratorでいうアートボードですね。  

### 作成方法
- ショートカットキー`F`を押して、フレームテンプレートを表示します。
- 表示された中から対象デバイスを選んで追加します。
- キャンバス上にドラッグすることで任意のサイズで作成することもできます。

![スクリーンショット 2025-04-04 202959.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1518953/4c248014-c318-4214-b466-688fa5341171.png)

## グリッド
グリッドを利用すると、パーツを配置する際に整列が簡単になり、統一感のあるデザインが作れます。

### 作成方法
1. フレームを作る
2. フレームのサイズをデバイスサイズに揃える
   - フレームの端をドラッグし、対象フレームに近づけることで揃えることができる
3.  レイアウトグリッドの`+`を押下する
    ![スクリーンショット 2025-04-04 205718.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1518953/d976fe33-75c5-44cb-a6c2-5b8e4845c927.png)
4. サイズを`8`に変更する

### なぜグリッドのサイズを8にするのか？
一貫性のあるデザインを作成するために、4の倍数や8の倍数でUIデザインを行う手法があります。  
これは`4ポイントグリッドシステム`呼ばれる考え方だそうです。  

以下の理由で推奨されています。
- 一般的なデバイスサイズは4か8で割り切ることが可能(例: 1920px×1080px、 1280px×720px)
- 要素を均等に配置しやすく、一貫性が生まれる
- スケーリングの容易さ: 例えば1.5倍で拡大・縮小を行っても、割り切れるためレイアウトが崩れない

https://medium.com/@aratidube12lns/4-point-grid-system-for-more-consistent-interface-design-efea81dea3f3

## 制約（Constraints）
デバイスサイズを変更したいとき、先ほど作成したグリッドのサイズも変更しないといけません。
そこで制約を指定しておくと、親要素を変更すると子要素も追従しサイズを揃えることが可能となります。

### 設定手順
1. サイズを追従させたい子要素を選択する
2. 右側のパネルから制約アイコンをクリックする
    ![スクリーンショット 2025-04-04 235554.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1518953/957a61ab-7d3d-4d72-a7f6-d4e496bd3066.png)
3. 追従させたい方向を選択する
  ![スクリーンショット 2025-04-04 235940.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1518953/8f9e89a2-d090-4e77-8cec-36142e733921.png)

これにより、指定した方向に沿って親要素がサイズ変更された際、子要素も自動的に揃えられるようになります。

## 参考文献
https://note.com/fujisaki_neko/n/n81043403659f#ad605437-16ec-43e4-8456-74be9d5c19a8

https://medium.com/design-bootcamp/the-4-point-grid-system-in-ux-e21f5573e5e8

https://medium.com/@aratidube12lns/4-point-grid-system-for-more-consistent-interface-design-efea81dea3f3

https://www.figma.com/community/file/1228577958737472070
