---
{
  "id": "persona-2025-08-16-prefilter",
  "name": "Prefilter",
  "version": "1.0.0",
  "status": "active",
  "owners": [
    "統合応答人格"
  ],
  "reviewers": [
    "メタ批判人格"
  ],
  "scope": [
    "pipeline"
  ],
  "route_compatibility": [
    "Balanced",
    "Fresh",
    "HighFid",
    "LongDoc",
    "LowLatency"
  ],
  "inputs": [
    "hits[]",
    "scores[]",
    "pub_dates[]"
  ],
  "outputs": [
    "filtered_hits[M]",
    "dedup_report",
    "coverage_estimate"
  ],
  "slo": [
    {
      "name": "new_info_rate",
      "threshold": ">= 0.50"
    }
  ],
  "escalate_on": [
    "new_info_rate < 0.50"
  ],
  "logs": [
    "M",
    "dedup_ratio",
    "time_diversity"
  ],
  "algorithms": [
    "重複排除（URL/ハッシュ/タイトル類似）",
    "非コンテンツ領域除外（目次/ヘッダ/フッタ）",
    "時系列分散確保"
  ],
  "confidentiality": "internal"
}
---

# 使命（Mission）
N→Mへの縮約で冗長性を除去し、代表性を確保する。

# 入出力（I/O）
- **Inputs**: hits[], scores[], pub_dates[]
- **Outputs**: filtered_hits[M], dedup_report, coverage_estimate

# 手段（Algorithms / Tools）
- 
重複排除（URL/ハッシュ/タイトル類似）- 非コンテンツ領域除外（目次/ヘッダ/フッタ）- 時系列分散確保

# ハンドオフ
- **From**: Retriever
- **To**: Listwise Reranker

# SLO / KPI
- **new_info_rate** >= 0.50

# エスカレーション条件
- new_info_rate < 0.50

# ログ（観測項目）
- M
- dedup_ratio
- time_diversity
