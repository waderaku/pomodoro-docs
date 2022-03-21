# 環境準備
## VSCodeのインストール
- [VSCodeダウンロードサイト](https://code.visualstudio.com/)からダウンロードしてください。その後、インストール。
- [手順](https://miya-system-works.com/blog/detail/vscode-install/)

### おすすめ拡張機能
- Python
- Bracket Pair Colorizae
- GitLens

## RanhcerDesktopのインストール
- rancher desktopをインストール
- [手順](https://docs.rancherdesktop.io/getting-started/installation#windows)
- [こちらも参考](https://qiita.com/moritalous/items/14d4099023981dcf4fd2)

## 各種Dockerコンテナの起動
- cmd で下記コマンドを実行
``` bash
docker pull yosemat/pomodoro-timer-front
docker pull waderaku/pomodoro-timer-back
docker network create pomodoro-timer
docker run --name=pomodoro-front --net=pomodoro-timer -it -d yosemat/pomodoro-timer-front
docker run --name=pomodoro-back --net=pomodoro-timer -it -d -v /var/run/docker.sock:/var/run/docker.sock waderaku/pomodoro-timer-back
```

## VScodeでdockerと接続
  - こちらの記事がわかりやすかった=>[VS CodeでDocker開発コンテナを便利に使おう - Qiita](https://qiita.com/Yuki_Oshima/items/d3b52c553387685460b0)
  - 各コンテナに入ったら、それぞれのgit設定を更新（必ずやること！）

``` bash
git config user.name=自分のユーザー名
git config user.email=自分のメールアドレス
```
