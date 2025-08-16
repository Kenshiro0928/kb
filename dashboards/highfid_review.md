## High‑fidelity レビュー待ち
```dataview
TABLE file.link, version, reviewers, qoc.accuracy
FROM "kb"
WHERE route_hint = "HighFid" AND status = "draft"
SORT file.mtime DESC
```
