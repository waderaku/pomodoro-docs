# mkdocs記載要領
## 初期環境構築
以下のdockerコマンドを実行してイメージのプル及びコンテナを作成する

``` bash
docker pull waderaku/pomodoro-timer-docs
docker run -it -d --name pomodoro-timer-docs waderaku/pomodoro-timer-docs
```

コンテナが立ち上がったら、VScodeを使ってコンテナ内に入る。  
gitの設定も各自更新する。

``` bash
git config user.name=自分のユーザー名
git config user.email=自分のメールアドレス
```

## フォルダ構成
docs/  
　├ 010.initial_settings/  
　├ 020.tutorial/  
　│　├ 010.frontend/  
　│　└ 020.backend/  
　├ 030.rule/  
　│　├ 010.meeting/  
　│　├ 020.git/  
　│　└ 030.frontend/  
　├ 040.document/  
　│　├ 010.common/  
　│　│   ├ 010.ubiquitous_language/  
　│　│   ├ 020.api/  
　│　│   └ 030.authentication/  
　│　├ 020.frontend/  
　│　│   ├ 010.screen_layout/  
　│　│   └ 020.deadline_task/  
　│　└ 030.backend/  
　│　    └ 010.db/    
　├ 050.meeting/  
　│　├ 010.20220327/  
　│　├ ...  
　├ 060.task/  
　└ 099.tips/  

## 各フォルダごとの記載内容
### 010.initial_settings
当開発の環境構築をする手順が記載されている.  
開発環境の変更があった場合に更新される可能性がある  

### 020.tutorial
当開発を行うにあたって必要となる知識のinput材料となるチュートリアルを用意した。  
バックエンド、フロントエンドそれぞれに用意している。  

### 030.rule
開発ルールについて記載  
現在は「会議体」、「git運用について」、「フロントエンド」について記載されているが、必要があれば追記する。  

### 040.document  
設計書にあたる内容が記載されている。  
「フロント・バックに共通する仕様」、「フロントエンドに閉じた仕様」、「バックエンドに閉じた仕様」に分離している

### 050.meeting
定例で共有した内容を日時ごとに記載している（最近は下火気味）

### 060.task
課題管理表。ソースコードに紐づタスク系はgithubのissuesで管理するため、それ以外の観点となる

## 新規ファイル執筆手順
1. 観点に沿って、各フォルダ構成に準じて新たなフォルダをツリーに追加する（例:バックエンドの開発ルールを記載する場合、030.rule配下に040.backendフォルダを追加する）
1. その配下にindex.mdファイルを作成し、そこに記載する。
1. mkdocs.ymlファイルの「nav:」配下にディレクトリ構成に対応するナビゲーションが記載されているため、そこに新規作成したファイルを追記する
1. 適宜コンソールから「mkdocs serve」を実行し、mkdocs上での見え方を確認する
1. 執筆完了したらgitでcommit、pushを行う
1. コンソールにて「mkdocs gh-deploy」を行いデプロイを行う。デプロイ環境に反映されていることを確認する