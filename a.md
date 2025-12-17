
📌 これだけで  
- 左：サムネ画像  
- 右：ノートリンク  
の一覧が出ます。

---

## 表示イメージ（概念）


::contentReference[oaicite:0]{index=0}


---

# ④ Notion風「カードギャラリー」にする（おすすめ）

Dataview **TABLEは地味**なので、CSSでカード化します。

## Dataview（HTMLを使う）

```markdown
```dataview
TABLE WITHOUT ID
  "![](" + featured + ")" AS "",
  file.link AS タイトル
FROM #project
