# qiita-content
こちらはQiita記事管理用リポジトリです

# [qiita-cli](https://github.com/increments/qiita-cli)コマンドチート
## Qiita Preview の起動（プレビュー画面の表示）
```sh
npx qiita preview
```
## 記事の作成/更新
リモートにpushすることでQiitaへの反映を行う

または以下コマンドで作成/更新も可能
### 新規記事作成
```sh
npx qiita new 記事のファイルのベース名
```
### 記事の投稿・更新
```sh
npx qiita publish 記事のファイルのベース名
```

# 参考
CLI使い方と管理方法についての詳細は以下にある
- [自分のエディタで記事投稿ができる、Qiita CLIの使い方](https://qiita.com/Qiita/items/666e190490d0af90a92b)
- [Qiitaの記事をGitHubリポジトリで管理する方法](https://qiita.com/Qiita/items/32c79014509987541130)