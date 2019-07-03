## Python

### 文法など

- 変数
  - 変数に型指定なし
- 文字の結合
  - +で結合 `temp = 'fizz' + 'buzz'` # 'fizzbuzz'
- 関数
  - defで宣言 `def hoge():`  
    ⇒ 後述のとおりインデントでブロック判断
  - 引数にデフォ値設定可能 `def fuga(a, b=2, c='piyo'):`  
    ⇒ デフォ値あり引数は呼び出し時省略可能
- インデント
  - インデントでブロック判断なので、スペース1つでもずれたらNG
  - インデントは半角スペース4つと決まっている
- 辞書型（key value pair）
  - キーと値のペアを保持する型
  - 基本： `obj = (key: value)`
  - 複数： `obj = (key1: value1, key2: value2)`
  - 追加： `obj = {hoge: 'hoge', fuga: 1}`  
    　　　 `obj['foo'] = 2` # 新しい データ を 追加
  - 削除： `del obj[hoge]` # hoge を 削除
- リスト
  - いわゆる配列の認識
  - 基本： `list = ['hoge', 10, True]`  
          ⇒ 添字は0から自動採番
  - 追加： `list.append(20)` # ['hoge', 10, True, 20]
  - 削除： `list.pop(2)` # ['hoge', 10, 20]  
          ⇒ ☆要素削除時の添字は？
- 集合
  - 重複しない複数の値を保持（型というよりオブジェクト？）
  - 宣言： `s = set()`
  - 追加： `s.add('hoge')`  
          ⇒ 重複した値は add しても追加されない（エラーにもならない）
- ループ
  - for ： `for i in range(0, 5):` # 5回繰り返し
  - for ： `for i in list:` # リストを使うとforeach` 集合（set）も利用可能
  - for ： `for i in obj:` # 辞書型を使ったforeach。この場合iにはKeyのみ入るのでValueは元の辞書型データから取り出す
  - while： `while True:`
  - リスト内包
    - 0～99: `l = [i for i in range(100)]` 1個指定の場合はその数-1までの模様。 range(5,10) だと5～9までだった。
    - 100以下の3の倍数の自然数:  
      `l = [i for i in range (100) if i % 3 == 0]`
- 条件分岐
  ``` python 
  if str == "hoge":
      print("hoge")
  elif str == "fuga":
      print("fuga")
  else:
      print("piyo")
  ```
  elif に注意
- クラス 
  - 宣言
    ``` python
    class Hoge:
        def __init__(self, hoge, fuga):
            self.hoge = hoge
            self.fuga = fuga

        def getHoge(self):
            print(self.hoge)

        def getFuga(self):
            print(self.fuga)
    ```
  - インスタンス化
    ``` python
    h = Hoge("hoge", "fuga")
    ```
- モジュール
  - ライブラリ呼び出しのようなもの？
  - サンプル(argv.py)
    ``` python
    import sys

    for i in sys.argv:
        print(i)
    ```
  - サードパーティ製のものはpipなどでローカルに持ってくる必要がある
    - 導入例  
      ```
      $ pip3 install requests
      ```
    - 利用例
      ``` python
      import requests

      r = requests.get('https://www.google.co.jp')
      print(r.content)
      ```
    - 欠点  
      pipで導入すると、マシン全体でこのパッケージを利用することになる。  
      （複数パッケージバージョンの使い分けなどができない）  
      ⇒ 解決策は次の venv 参照
    - 参考  
      pipで導入したもの（及びバージョン）を確認するコマンド
      ```
      $ pip freeze
      ```
- venv
  - 仮想環境の作成コマンド。（virtual env）
  - 以下の例では project プロジェクトの仮想環境を構築し、requests パッケージを利用している
    ```
    $ mkdir project
    $ python3 -m venv project
    $ cd project
    $ source bin/activate
    (project) hoge:project hoge$
    (project) hoge:project hoge$ pip3 install requests
    ```
  - 仮想化しているとHerokuなどPaaS利用時などに便利
  - python自体を含め各種フレームワークなどは仮想化環境内では外と別のバージョンを個別にインストール可能
