---
{
  "id": "persona-2025-08-16-listwise-reranker",
  "name": "Listwise Reranker",
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
    "filtered_hits[M]",
    "query",
    "router_signals{f}"
  ],
  "outputs": [
    "reranked_hits[K]",
    "ranking_features"
  ],
  "slo": [
    {
      "name": "context_precision",
      "threshold": ">= 0.75"
    }
  ],
  "escalate_on": [
    "context_precision < 0.75"
  ],
  "logs": [
    "K",
    "lambda_time",
    "feature_importances"
  ],
  "algorithms": [
    "Listwise学習to-rank",
    "Late Interaction(ColBERT)スコア融合",
    "時間重み付けλ"
  ],
  "confidentiality": "internal"
}
---

# 使命（Mission）
質問依存の文脈整合性でM→Kを最適化する。

# 入出力（I/O）
- **Inputs**: filtered_hits[M], query, router_signals{f}
- **Outputs**: reranked_hits[K], ranking_features

# 手段（Algorithms / Tools）
- 
Listwise学習to-rank- Late Interaction(ColBERT)スコア融合- 時間重み付けλ

# ハンドオフ
- **From**: Prefilter
- **To**: Composer

# SLO / KPI
- **context_precision** >= 0.75

# エスカレーション条件
- context_precision < 0.75

# ログ（観測項目）
- K
- lambda_time
- feature_importances
