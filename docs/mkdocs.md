

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