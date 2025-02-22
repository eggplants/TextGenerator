# Text Generator CLI

[![Release Package](https://github.com/eggplants/TextGenerator-cli/actions/workflows/release.yml/badge.svg)](https://github.com/eggplants/TextGenerator-cli/actions/workflows/release.yml) [![PyPI version](https://badge.fury.io/py/TextGenerator-cli.svg)](https://badge.fury.io/py/TextGenerator-cli)

- マルコフ連鎖を使った文章自動生成プログラム(日本語のみ) + コマンドラインインターフェース
- [ohshige15/TextGenerator](https://github.com/ohshige15/TextGenerator)の[Fork](https://github.com/karaage0703/TextGenerator)の[Fork](https://github.com/nkutomi/TextGenerator)の Fork

## インストール

### 1. 事前に mecab をセットアップしておく

- Mac:

```bash
brew install mecab
brew install mecab-ipadic
```

- Linux(Ubuntu):

```bash
sudo apt install mecab libmecab-dev mecab-ipadic-utf8 -y
```

- Windows:
  - [3rd Party のインストーラ](https://github.com/ikegami-yukino/mecab/releases/tag/v0.996.2)でインストール
  - 環境変数`Path`に`C:\Program Files\MeCab\bin`を追加

### 2. `TextGenerator-cli`を PyPI からダウンロード

```bash
pip install TextGenerator-cli
```

## ヘルプ

```bash
$ textgen
usage: textgen [-V] [-h] {prepare,p,generate,g,help,h} ...

マルコフ連鎖を使った文章自動生成プログラム

positional arguments:
  {prepare,p,generate,g,help,h}
    prepare (p)         モデルをテキストから作成する
    generate (g)        文章を生成する
    help (h)            ヘルプを表示する

optional arguments:
  -V, --version         バージョン情報を表示する
  -h, --help            ヘルプを表示する


```

```bash
$ textgen help p
usage: textgen prepare [-o DB] [-h] [FILE [FILE ...]]

positional arguments:
  FILE             テキストファイル (default: stdin)

optional arguments:
  -o DB, --out DB  出力DBファイル名 (default: chain.db)
  -h, --help       ヘルプを表示する

```

```bash
$ textgen help g
usage: textgen generate [-s NL] [-b BYTE] [-n TIME] [-t LIM] [-d DB] [-h]

optional arguments:
  -s NL, --sentence NL  生成する文数(>=0) (default: 5)
  -b BYTE, --byte BYTE  指定byte数以下の文生成を試行(>=0) (default: None)
  -n TIME, --time TIME  生成する回数(>=0) (default: 1)
  -t LIM, --try LIM     試行回数の上限(>=0) (default: 100)
  -d DB, --db DB        チェインDBファイル (default: chain.db)
  -h, --help            ヘルプを表示する

```

```bash
$ textgen help h
usage: textgen help [-h] command

positional arguments:
  command     ヘルプが表示されるコマンド名

optional arguments:
  -h, --help  ヘルプを表示する

```

## 使い方

```bash
# 吾輩は猫であるを青空文庫からダウンロード
$ curl 'http://pubserver2.herokuapp.com/api/v0.1/books/789/content?format=txt' -o wagahai.txt
# モデル作成(chain.dbに出力する, -oで変更可能)
$ textgen p wagahai.txt
# 文章生成(chain.dbを入力とする, -dで変更可能)
# -nで回数, -sで1回につなげる文の数を指定
$ textgen g -n 2 -s 3
忘れまいと思って、小供だの、いろいろ用事があっては近頃材料払底の為め、黒石を取っては黒を見て、図書館へは寄りつかない男だ」失敬な、下駄屋はいつ御催しがありました。「そうでございましょう」と考えて見たら分るでしょうから吹き付ける、非常に体育を重んじたものは自分の容貌《ようば》へ置く。
この鏡を見ねえ。しかるにこのパラドックスを道破《どうは》えに眼窩《がんなべ》の声だけにしろと、烈しい光線で瞳孔《どうこう》の根本へ吹き寄せつつある。「質朴剛健でたのもしい気風だ」
```

## Fork 元

- オリジナル: [ohshige15/TextGenerator](https://github.com/ohshige15/TextGenerator)
  - +はてブロ投稿: [karaage0703/TextGenerator](https://github.com/karaage0703/TextGenerator)
    - +マイナーな変更: [nkutomi/TextGenerator](https://github.com/nkutomi/TextGenerator)
      - +CLI(いまここ): [eggplants/TextGenerator](https://github.com/eggplants/TextGenerator)
