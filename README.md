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
usage: textgen [-h] [-V] {prepare,p,generate,g,help,h} ...

マルコフ連鎖を使った文章自動生成プログラム

positional arguments:
  {prepare,p,generate,g,help,h}
    prepare (p)         モデルをテキストから作成(chain.db)
    generate (g)        文章を生成する
    help (h)            ヘルプを表示する

optional arguments:
  -h, --help            show this help message and exit
  -V, --version         show program's version number and exit
```

```bash
$ textgen p -h
usage: textgen prepare [-h] [FILE [FILE ...]]

positional arguments:
  FILE        テキストファイル(指定がなければstdin)

optional arguments:
  -h, --help  show this help message and exit
```

```bash
$ textgen g -h
usage: textgen generate [-h] [-n NL] [-l BYTE] [-t LIMIT]

optional arguments:
  -h, --help            show this help message and exit
  -n NL, --num_line NL  生成する文数(>=0)
  -l BYTE, --length BYTE
                        指定したbyte数以下のものが生成されるまで試行(>=0)
  -t LIMIT, --try_limit LIMIT
                        試行回数の上限(>=0)
```

## 使い方

```bash
# 吾輩は猫であるを青空文庫からダウンロード
$ curl 'http://pubserver2.herokuapp.com/api/v0.1/books/789/content?format=txt' -o wagahai.txt
# モデル作成
$ textgen p wagahai.txt
# 文数2で生成
$ textgen g -n 2
従って人間らしい行動を二週間継続するなら白髪だって伝染しているかとの諺《ことわざ》になるそうだ面白いじゃありませんか、今戸焼の狸《たぬき》からしていいでしょう」漆桶《み》がある。
```

## Fork 元

- オリジナル: [ohshige15/TextGenerator](https://github.com/ohshige15/TextGenerator)
  - +はてブロ投稿: [karaage0703/TextGenerator](https://github.com/karaage0703/TextGenerator)
    - +マイナーな変更: [nkutomi/TextGenerator](https://github.com/nkutomi/TextGenerator)
      - +CLI(いまここ): [eggplants/TextGenerator](https://github.com/eggplants/TextGenerator)
