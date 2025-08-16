---
{
  "id": "persona-2025-08-16-retriever",
  "name": "Retriever",
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
    "query",
    "router_signals{c,f,h,r}",
    "budget{tokens,latency}"
  ],
  "outputs": [
    "hits[]",
    "scores[]",
    "pub_dates[]",
    "fresh_count_90d",
    "recall@100"
  ],
  "slo": [
    {
      "name": "recall@100",
      "threshold": ">= 0.90"
    },
    {
      "name": "fresh_count_90d (Fresh)",
      "threshold": ">= 2"
    }
  ],
  "escalate_on": [
    "recall@100 < 0.90",
    "Fresh判定でfresh_count_90d < 2"
  ],
  "logs": [
    "N",
    "index",
    "filters",
    "time_weight_lambda",
    "hyde_used"
  ],
  "algorithms": [
    "Hybrid(BM25 + Dense(E5系) + Late Interaction(ColBERTv2))",
    "HyDE（低再現率時のみ）",
    "重複・ノイズ除去フィルタ"
  ],
  "confidentiality": "internal"
}
---

# 使命（Mission）
高再現率で根拠候補を収集し、時事性要件を満たす集合を返す。

# 入出力（I/O）
- **Inputs**: query, router_signals{c,f,h,r}, budget{tokens,latency}
- **Outputs**: hits[], scores[], pub_dates[], fresh_count_90d, recall@100

# 手段（Algorithms / Tools）
- 
Hybrid(BM25 + Dense(E5系) + Late Interaction(ColBERTv2))- HyDE（低再現率時のみ）- 重複・ノイズ除去フィルタ

# ハンドオフ
- **From**: Router
- **To**: Prefilter

# SLO / KPI
- **recall@100** >= 0.90
- **fresh_count_90d (Fresh)** >= 2

# エスカレーション条件
- recall@100 < 0.90
- Fresh判定でfresh_count_90d < 2

# ログ（観測項目）
- N
- index
- filters
- time_weight_lambda
- hyde_used
