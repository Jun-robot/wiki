# コミットメッセージガイドライン（簡易版）

## 基本ルール
- 1コミットにつき1トピック（複数あれば分ける）
- 英語または簡潔な日本語で命令形・現在形を書く（例: `Add git cheatsheet`)
- 50文字以内が理想。末尾に句読点はつけない
- 必要なら本文に1行追加し、背景やテスト結果を軽く書く

## 形式
```
<type>: <subject>
```

### よく使うtype
- `feat` 新規追加
- `fix` バグ/誤字修正
- `chore` メンテナンス・その他

## 例
```
docs: add commit message guideline

Note the format so contributors can follow the same style.
```
