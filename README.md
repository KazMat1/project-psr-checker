# Instruction
## About this repository
- PSR-2のうち、「最低限これは守ってほしい！」というものを選んで、それにマッチしないものを検査するために使います。
- 正確にいうと、守られていないものとマッチする部分を検知します

## Usage
1. リポジトリをクローンする
1. クローンしたプロジェクトディレクトリをターミナルで開く
1. phpbadを適当な場所に置く
```
mkdir ~/lib
cp phpbad ~/lib/
```
4. PSRをチェックしたいディレクトリに移動する
```
cd {path/to/target/directory}
```
5. ディレクトリを移動したら下記のコマンドを実行する
```
find . -name '*.php' -exec grep -n -E -H -f ~/lib/phpbad {} \;
```

## 自分用メモ
- phpbadのアップデートをする
