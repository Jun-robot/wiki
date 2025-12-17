あ



```dataview
TABLE
  file.link AS ノート
FROM #toio 
```


```dataview
TABLE
  featured AS サムネ,
  file.link AS ノート
FROM #
SORT file.mtime DESC
```


