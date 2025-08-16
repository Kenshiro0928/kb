## Fresh不足チェック
```dataview
LIST FROM "kb/corpus"
WHERE qoc.freshness_days > 90 OR !exists(source.published_at)
```
