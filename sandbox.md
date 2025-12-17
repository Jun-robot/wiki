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


```dataviewjs
const pages = dv.pages("")
  .where(p => p.thumbnail)
  .sort(p => p.file.mtime, "desc");

function toSrc(thumbnail) {
  let path = (typeof thumbnail === "string") ? thumbnail : thumbnail?.path;
  if (!path) return "";

  if (path.startsWith("http://") || path.startsWith("https://") || path.startsWith("data:")) return path;
  if (path.startsWith("/")) path = path.slice(1);

  const af = app.vault.getAbstractFileByPath(path);
  return af ? app.vault.getResourcePath(af) : "";
}

const root = dv.el("div", "", { cls: "dv-cards" });

for (const p of pages) {
  const card = root.createDiv({ cls: "dv-card" });

  // 👇 ここが重要：クリックでノートを開く
  card.onclick = () => {
    app.workspace.openLinkText(p.file.path, "", false);
  };

  const imgWrap = card.createDiv({ cls: "dv-card-imgwrap" });
  imgWrap.createEl("img", {
    cls: "dv-card-img",
    attr: { src: toSrc(p.thumbnail) }
  });

  const body = card.createDiv({ cls: "dv-card-body" });
  body.createDiv({ cls: "dv-card-title", text: p.file.name });
}


```
