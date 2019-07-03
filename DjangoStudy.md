## Django

- MTV?
  - MVC
    - Model : アプリケーションを構成するデータの構造や操作を宣言する
    - View  : データをどのように整形してビジュアルを表現するか
    - Controller : モデルとビューの関係性を定義する
  - MTV
    - Model
    - Template : MVCのViewに似た役割
    - View     : MVCのControllerに相当。特定のURLに対するPythonコールバック関数
- Flask?
  - Flask : 軽量＆高速。シンプルなアプリケーション向き
  - Django : 安定、フルスタック
- サポート
  - 最新のLTSは 2.2 なので、今から開発する場合基本は 2.2 を利用する

## [Django(2.2)チュートリアル](https://docs.djangoproject.com/ja/2.2/intro/)

- 一旦仮想環境作成 & アクティブ化
  ```
  > virturlenv env
  > .\env\Scripts\activate
  ```

- 仮想環境にdjangoをインストール
  ```
  > pip install django
  ```

- プロジェクト作成
  ```
  > django-admin startproject mysite
  ```

- ローカルサーバ起動  
  作成したディレクトリ内（manage.pyのあるところ）で
  ```
  > py manage.py runserver
  ```

- アプリケーション作成  
  作成したディレクトリ内（manage.pyのあるところ）で
  ```
  > py manage.py startapp polls
  ```

  ※ プロジェクトという枠内に複数のアプリケーション、設定が入るイメージ

## その他
- 日本で利用するための設定
  - settings.py
    - LANGUAGE_CODE = 'ja'
    - TIME_ZONE = 'Asia/Tokyo'
- migration
  - models.pyのモデルを変更する（作成したいテーブル定義を表す）
  - 変更のためのマイグレーションを作成するために以下を実行する
    ```
    > python manage.py makemigrations
    ```

  - データベースに変更を反映するために以下を実行する
    ```
    > python manage.py migrate
    ```

  - Adminの作成
    ```
    > python manage.py createsuperuser
    ```

  - 対象プロジェクトでの対話型実行
    ```
    > python manage.py shell
    ```