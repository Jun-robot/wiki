# gitの使い方



## 基本操作

## 初期設定
### インストール
```bash
sudo apt install git gh
```
### 公開鍵の作成
```bash
ssh-keygen -t ed25519 -f ~/.ssh/ed25519_github -C "your_email@example.com"
```
- `-t ed25519` 鍵の種類
- `-C "email"` 鍵のコメント
- `-f ~/.ssh/ed25519_github` 鍵の保存場所
- パスフレーズはつけよう
 
## ghで登録
```bash 
gh auth login
```



## 既存のフォルダをgit管理下に置く

### gitの初期化と最初のコミット
```bash
git init
git add .
git commit -m "first commit"
```

### ghの用意
```bash
gh auth login
```

### 空のリポジトリの作成
```bash
gh repo create <repo-name> --public --source=. --remote=origin
```
### プッシュ
```bash
git push -u origin main
```

## コミットメッセージ
- このリポジトリでの書き方は[`commit-message-guideline.md`](../commit-message-guideline.md)を参照
