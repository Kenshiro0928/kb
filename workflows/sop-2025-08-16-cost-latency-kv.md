---
{
  "id": "sop-2025-08-16-cost-latency-kv",
  "title": "Cost/Latency管理（KV圧縮・圧縮率・再ランク予算）",
  "version": "1.0.0",
  "status": "active",
  "owners": [
    "オペ/品質人格"
  ],
  "reviewers": [
    "統合応答人格",
    "メタ批判人格"
  ],
  "confidentiality": "internal",
  "route_hint": "Balanced",
  "quality_criteria": [
    {
      "name": "ragas_mean",
      "threshold": ">= 0.80"
    },
    {
      "name": "ais_pass_rate",
      "threshold": ">= 0.90"
    },
    {
      "name": "unsupported_claim_rate",
      "threshold": "<= 0.02"
    }
  ],
  "preconditions": {
    "data_freshness_hours": 24,
    "data_completeness_pct": 99.5
  },
  "links": [
    {
      "rel": "policy",
      "href": "../policies/rag_policy.yaml"
    },
    {
      "rel": "routes",
      "href": "../routes"
    }
  ]
}
---

## 目的
平均入力≤4k tokens、再ランク適用率≤40%を維持。

## 手順
1) KV圧縮（H2O/SnapKV）を適用
2) LongLLMLinguaの圧縮ダイヤル調整
3) 予算超過時は再ランクOFF（HighFid除外）
