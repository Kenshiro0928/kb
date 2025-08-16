---
{
  "id": "persona-2025-08-16-router",
  "name": "Router",
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
    "historical_signals",
    "router_signals{c,f,h,r}",
    "doc_stats{pages,tokens,pub_dates}"
  ],
  "outputs": [
    "preset",
    "justification",
    "signals{c,f,h,r}"
  ],
  "slo": [
    {
      "name": "route_miss_rate",
      "threshold": "<= 10%"
    },
    {
      "name": "escalation_latency_ms",
      "threshold": "<= 500"
    }
  ],
  "escalate_on": [
    "ragas_window_mean < 0.75",
    "ais_fail_rate > 0.10",
    "retrieval@100 < 0.90"
  ],
  "logs": [
    "preset",
    "c",
    "f",
    "h",
    "r",
    "time_sensitive",
    "risk",
    "doc_pages",
    "est_tokens"
  ],
  "algorithms": [
    "自己反省スコア（確信度c）推定器",
    "時事性検出（発行日分布・時間語）",
    "多段推論推定（複雑度h）",
    "リスク分類（法務/臨床/財務/対外）",
    "ルール: confidence_route=0.72, low_latency_demote=0.65, recency_days=90"
  ],
  "confidentiality": "internal"
}
---

# 使命（Mission）
クエリ特性（c,f,h,r）に基づき、Balanced/Fresh/HighFid/LongDoc/LowLatencyのプリセットへ振り分ける。

# 入出力（I/O）
- **Inputs**: query, historical_signals, router_signals{c,f,h,r}, doc_stats{pages,tokens,pub_dates}
- **Outputs**: preset, justification, signals{c,f,h,r}

# 手段（Algorithms / Tools）
- 
自己反省スコア（確信度c）推定器- 時事性検出（発行日分布・時間語）- 多段推論推定（複雑度h）- リスク分類（法務/臨床/財務/対外）- ルール: confidence_route=0.72, low_latency_demote=0.65, recency_days=90

# ハンドオフ
- **From**: ユーザ/システム入力
- **To**: Retriever

# SLO / KPI
- **route_miss_rate** <= 10%
- **escalation_latency_ms** <= 500

# エスカレーション条件
- ragas_window_mean < 0.75
- ais_fail_rate > 0.10
- retrieval@100 < 0.90

# ログ（観測項目）
- preset
- c
- f
- h
- r
- time_sensitive
- risk
- doc_pages
- est_tokens
