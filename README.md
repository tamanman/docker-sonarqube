# docker-sonarqube
dockerでsonarqubeをたちあげる



## 1. サーバーの起動と終了 

* 開発環境

    mac 10.10.05
    
    docker Version 17.03.1-ce-mac12 (17661)

* 起動

    ```
    docker-compose up -d
    ```
    `http://localhost:9000` でアクセスできます。

    ```
    ID admin
    PASS admin
    ```
    
    でログイン

* セットアップ (phpの場合)

    ログイン後

    Administration > System > Update Center > Available

    にて移動してphpで検索して、 `SonarPHP` プラグインをinstall

    install完了後restart

* プロセス確認

    ```
    docker-compose ps
    ```

* 終了

    ```
    docker-compose down
    ```


### 2. 解析

* 解析ツール sonar-scannerのインストール

   ```
   brew install sonar-scanner
   ```

* プロジェクト用ファイルの作成

    解析したいプロジェクト配下に

    `sonar-project.properties`

    を作成 

* 解析

    実行コマンド

    >/usr/local/Cellar/sonar-scanner/3.0.0.702/bin/sonar-scanner

    ※ version(3.0.0.702) は適宜変更してください。

    実行には5分程度かかります。
    コマンドが完了しても sonar管理画面上 `in progress` がしばらく続きます

    `http://localhost:9000/projects`

    で解析結果を確認
