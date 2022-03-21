# git
## gitって？
- 古いバージョンに簡単に戻せる
- 新旧のファイルを一元管理できる
- 編集した履歴を複数人で共有できる
- 複数人で修正した部分を一つに統合できる
![gitイメージ.png](./image/git%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8.png)
- リモートリポジトリ
    - 特定のサーバー上に設置して複数人で共有するためのリポジトリ
- ローカルリポジトリ
    - ユーザーごとに配置される手元のマシンで編集できるリポジトリ
## 各種コマンド
### fetch
- ローカルリポジトリをリモートリポジトリに同期する
```git
git fetch origin
git fetch origin (リモートブランチ名)
```
### merge
- リモートブランチと同期したデータ、ローカルリポジトリ(のカレントブランチ)に取り込む
```git
git merge origin/(リモートブランチ名)
```
### pull
- fetchとmergeをまとめて行う
- ローカルブランチに対象ブランチが存在しない場合は新たに作る
- 基本的にこれを使う
```git
git pull origin (リモートブランチ名)
```
### push
- ローカルブランチのデータをリモートブランチに送る（最新のもの）
```git
git push origin (ローカル・リモートのブランチ名)
git push origin <PUSHしたいローカルブランチ名>:<PUSH先リモートブランチ名>
```
### branch
- ブランチの一覧表示
```git
git branch
```
- ブランチ新規作成
```git
git branch (新規ローカルブランチ名)
```
- ブランチの削除
```git
git branch -d (ローカルブランチ名)
git branch -D (ブランチ名)
```
### checkout
- カレントブランチの変更
```git
git checkout (ローカルブランチ名)
```
- 新規ブランチを作りそれをカレントブランチにする
```git
git checkout -b (ブランチ名)
```
### state
- 変更のあったファイルを確認
```git
git state
```
### add
- 変更を取り込むファイルの選択
```git
git add (ファイル名)
```
### commit
- 変更を確定
```git
git commit -m 'コメント'
```

### 規約
- ローカルブランチからリモートブランチのmasterには直にpushしない
  - 別名でリモートブランチを切って、そこからpull requestを出す
  - pull requestの名前にはissue番号を入れる(例:#86 XXXコンポーネント修正)
- 作業の前にはissueボードの該当タスクを動かす
### Tips
- 基本的に作業は下記の流れ
```git
git checkout -b XXX
git pull origin master
git add ./XXX/XXX.tsx
git commit -m '#86 isuue対応'
git push origin XXX
```
- その他
  - 過去のバージョンに戻る
    ```git
    // コミットログを参照
    git log
    // 対象コミットに戻る
    git reset --hard XXX
    // 戻しすぎちゃった場合
    git reflog
    // reflogで出てきたログに
    git reset --hard XXX
    ```
  - リモートブランチでローカルを上書きする
    ```git
    git fetch origin (対象リモートブランチ)
    git reset --hard origin/<branch_name>
    ```