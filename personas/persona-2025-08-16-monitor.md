---
{
  "id": "persona-2025-08-16-monitor",
  "name": "Monitor",
  "version": "1.0.0",
  "status": "active",
  "owners": [
    "統合応答人格"
  ],
  "reviewers": [
    "メタ批判人格"
  ],
  "scope": [
    "assurance"
  ],
  "route_compatibility": [
    "Balanced",
    "Fresh",
    "HighFid",
    "LongDoc",
    "LowLatency"
  ],
  "inputs": [
    "query_id",
    "preset",
    "metrics{ragas,ais,recall,latency,tokens_in,out}"
  ],
  "outputs": [
    "dashboard_view",
    "escalation_ticket?",
    "recommendations"
  ],
  "slo": [
    {
      "name": "observability_completeness",
      "threshold": ">= 0.99"
    }
  ],
  "escalate_on": [
    "ragas_window_mean < 0.75",
    "ais_fail_rate > 0.10",
    "retrieval@100 < 0.90"
  ],
  "logs": [
    "query_id",
    "preset",
    "N/M/K",
    "compress_ratio",
    "sources[]",
    "publish_dates[]",
    "ragas",
    "ais_pass",
    "latency_ms",
    "tokens_in/out"
  ],
  "algorithms": [
    "スライディングウィンドウでRAGAS/AIS/Recallを監視",
    "逸脱時の自動エスカレーション（ECOへ）"
  ],
  "confidentiality": "internal"
}
---

# 使命（Mission）
運転健全性を可視化し、逸脱をECO/Policyへ伝達する。

# 入出力（I/O）
- **Inputs**: query_id, preset, metrics{ragas,ais,recall,latency,tokens_in,out}
- **Outputs**: dashboard_view, escalation_ticket?, recommendations

# 手段（Algorithms / Tools）
- 
スライディングウィンドウでRAGAS/AIS/Recallを監視- 逸脱時の自動エスカレーション（ECOへ）

# ハンドオフ
- **From**: Verifier
- **To**: ECO / Policy Steward

# SLO / KPI
- **observability_completeness** >= 0.99

# エスカレーション条件
- ragas_window_mean < 0.75
- ais_fail_rate > 0.10
- retrieval@100 < 0.90

# ログ（観測項目）
- query_id
- preset
- N/M/K
- compress_ratio
- sources[]
- publish_dates[]
- ragas
- ais_pass
- latency_ms
- tokens_in/out
