---
{
  "id": "sop-2025-08-16-eco-dspy",
  "title": "ECO（自己最適化：DSPy）運用",
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
N/M/K・時間重みλ・HyDE有無・圧縮rを自動探索しSLO逸脱を是正。

## 手順
1) Monitorからの逸脱通知で起動
2) ナイトリーで署名別に探索
3) 差分パッチをPRとして提出→Policy審査

## 記録
experiments/dspy/ に検索空間と最良設定を保存
