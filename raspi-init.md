# Raspberry Pi Initialization Guide
## Raspberry Pi Imager
### OS
基本的には、Raspberry Pi OS Lite (64bit) 
- Raspberry Pi 3/4/5なら64bitCPU搭載

### ホスト名
`4b-01`, `4b-02`を参考につける
- cmの時は別にしたいな

### ユーザー名
- tomoshibi
- technetope

### パスワード
- ひみつ。

### タイムゾーン
- Asia/Tokyo

### キーボードレイアウト
- us

### SSH
- 有効化
- 公開鍵認証方式
  - 公開鍵の作り方は後述

### uartの有効化
uart経由でシリアルコンソールにアクセスできるようにする。
`config.txt`に以下を追記

```
[All]
enable_uart=1
```

## 公開鍵の作り方
### 鍵を入れるフォルダを作る(任意)
```zsh
mkdir -p ~/.ssh/tomoshibi
chmod 700 ~/.ssh/tomoshibi //権限を与える
```

### 鍵の作成
```zsh
ssh-keygen -t ed25519 -f ~/.ssh/tomoshibi/4b-01-jumpei -C "4b-01-jumpei"
```
- `-t ed25519` 鍵の種類
- `-f ~/.ssh/tomoshibi/4b-01-jumpei` 鍵の保存場所
- `-C "4b-01-jumpei"` 鍵のコメント
- パスフレーズはつけよう

### 転送
```zsh
ssh-copy-id -i ~/.ssh/tomoshibi/4b-01-jumpei.pub tomoshibi@4b-01.local
```

### sshの設定に追記(任意)
`~/.ssh/config`に以下を追記
```zsh
Host 4b-01
    HostName 4b-01.local
    User tomoshibi
    IdentityFile ~/.ssh/tomoshibi/4b-01-jumpei
    Port 22
```
`ssh 4b-01`でログインできるようになる。