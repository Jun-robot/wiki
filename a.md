あ



```dataview
TABLE
  file.link AS ノート
FROM #toio 
```


```dataview
TABLE
  choice(thumbnail, "![](" + thumbnail + ")", "") AS サムネ,
  file.link AS ノート
FROM ""
```


