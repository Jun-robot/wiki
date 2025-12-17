---
feature: thumbnails/resized/bdc1a0d552dbaa00c0ac1933a93eb087_86cf658e.webp
thumbnail: thumbnails/resized/58e35810cf9bbc538ba012862a5db926_86cf658e.webp
---
あ

![](thumbnails/resized/bdc1a0d552dbaa00c0ac1933a93eb087_86cf658e.webp)

```dataviewjs
const pages = dv.pages("").where(p => p.thumbnail);

function toSrc(thumbnail) {
  if (!thumbnail) return "";

  // thumbnail が "文字列" か "リンク型" か両対応
  let p = (typeof thumbnail === "string") ? thumbnail : thumbnail.path;

  // Webやdata URLはそのまま
  if (p.startsWith("http://") || p.startsWith("https://") || p.startsWith("data:")) {
    return p;
  }

  // 先頭スラッシュが付いてたら落とす（環境差対策）
  if (p.startsWith("/")) p = p.slice(1);

  // Vault内ファイルとして解決して resource URL に変換
  const af = app.vault.getAbstractFileByPath(p);
  if (af && af.path) {
    return app.vault.getResourcePath(af);
  }

  // 見つからない場合は空（リンク切れ回避）
  return "";
}

dv.table(
  ["サムネ", "ノート"],
  pages.map(p => {
    const src = toSrc(p.thumbnail);
    const img = dv.el("img", "", { attr: { src }});
    img.style.maxHeight = "90px";
    img.style.objectFit = "cover";
    img.style.maxWidth = "160px";
    return [img, p.file.link];
  })
);

```
