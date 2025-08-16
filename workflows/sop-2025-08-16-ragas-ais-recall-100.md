---
{
  "id": "sop-2025-08-16-ragas-ais-recall-100",
  "title": "評価パイプライン（RAGAS/AIS/Recall@100）",
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
RAGの品質を定量監視しSLOを維持する。

## 手順
1) evals/sets/* を用いて RAGAS/AIS/Recall を測定
2) 逸脱をMonitorが検知→ECOが探索
3) 有効パッチをPolicyが承認・配備

## 基準
RAGAS≥0.80、AIS≥90%、Recall@100≥0.90
