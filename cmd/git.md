# gitの使い方

## 基本操作





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
