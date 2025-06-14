

## セットアップ

リポジトリを初期化する

```
mkdir docs
git init
cd docs
```

WSL Ubuntuでパッケージを入れる

```
sudo apt install mkdocs
```

mkdocs初期化

```
mkdocs new temp
```

中身を出す

```
mv temp/* ./
rmdir temp
```

コミットして、GithubにパブリックでPush

## ビルド/デプロイ

以下のコマンドで一括実施

```
mkdocs gh-deploy
```

- mdをビルドして./siteに保存
- ./siteをルートにgh-pagesブランチにコミット

.gitignore作成

```
/site/
```

## Actions

書き込み権限を与える

![alt text](image.png)

