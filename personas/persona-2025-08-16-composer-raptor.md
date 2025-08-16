---
{
  "id": "persona-2025-08-16-composer-raptor",
  "name": "Composer (RAPTOR)",
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
    "reranked_hits[K]",
    "query"
  ],
  "outputs": [
    "summary_tree",
    "coverage_score",
    "salient_spans[]"
  ],
  "slo": [
    {
      "name": "coverage_score",
      "threshold": ">= 0.80"
    }
  ],
  "escalate_on": [
    "coverage_score < 0.80"
  ],
  "logs": [
    "raptor_depth",
    "nodes",
    "edges",
    "salient_span_count"
  ],
  "algorithms": [
    "RAPTOR: 2層（LongDoc時は3層）",
    "章→節→段落の階層要約",
    "重要根拠の冒頭/末尾固定"
  ],
  "confidentiality": "internal"
}
---

# 使命（Mission）
長文集合を階層要約木に落とし込み、見落としと中域喪失を抑える。

# 入出力（I/O）
- **Inputs**: reranked_hits[K], query
- **Outputs**: summary_tree, coverage_score, salient_spans[]

# 手段（Algorithms / Tools）
- 
RAPTOR: 2層（LongDoc時は3層）- 章→節→段落の階層要約- 重要根拠の冒頭/末尾固定

# ハンドオフ
- **From**: Listwise Reranker
- **To**: Compressor

# SLO / KPI
- **coverage_score** >= 0.80

# エスカレーション条件
- coverage_score < 0.80

# ログ（観測項目）
- raptor_depth
- nodes
- edges
- salient_span_count
