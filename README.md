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
6. マッチしたファイルのパスと行数が出力される
```
./{path}/{to}/{file}.php:{Line}: AAAAAA
./{path}/{to}/{file}.php:{Line}: CCCCCC
./{path}/{to}/{file}.php:{Line}: EEEEEE
./{path}/{to}/{file}.php:{Line}: GGGGGG
・・・
（省略）
・・・
```

## Extra
1. マッチしたファイルのパスと行数をひとつのファイルにして出力したいとき
```
mkdir ./tmp && find . -name '*.php' -exec grep -n -E -H -f ~/lib/phpbad {} \; > ./tmp/file
```
2. ファイルの行数もカウントできるよ
```
wc -l ./tmp/file
```
3. プロジェクトディレクトリから移動させて削除しちゃおう
```
mv ./tmp/file ~/{somewhere} && rm -r ./tmp
```

## Todo
- 違反している項目をひとつのファイルにして出力したい
- phpbadのルールを自分用にアップデートする
- 特定のディレクトリは、検査の対象外にする or 特定のディレクトリのみを検査対象とする
