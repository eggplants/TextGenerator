# Text Generator

マルコフ連鎖を使った文章自動生成プログラム(日本語のみ)

## インストール

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

## 使い方

```bash
# 吾輩は猫であるを青空文庫からダウンロード
$ curl 'http://pubserver2.herokuapp.com/api/v0.1/books/789/content?format=txt' -o wagahai.txt
# モデル作成
$ textgen p wagahai.txt
# 文章の長さ10で生成
$ textgen g 2
従って人間らしい行動を二週間継続するなら白髪だって伝染しているかとの諺《ことわざ》になるそうだ面白いじゃありませんか、今戸焼の狸《たぬき》からしていいでしょう」漆桶《み》がある。
```

## Fork 元

- オリジナル: [ohshige15/TextGenerator](https://github.com/ohshige15/TextGenerator)
  - +はてブロ投稿: [karaage0703/TextGenerator](https://github.com/karaage0703/TextGenerator)
    - +マイナーな変更: [nkutomi/TextGenerator](https://github.com/nkutomi/TextGenerator)
      - +CLI(いまここ): [eggplants/TextGenerator](https://github.com/eggplants/TextGenerator)
