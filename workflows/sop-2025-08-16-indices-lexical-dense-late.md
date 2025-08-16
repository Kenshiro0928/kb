---
{
  "id": "sop-2025-08-16-indices-lexical-dense-late",
  "title": "Indices構築・更新（lexical/dense/late）",
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
検索の土台を安定供給。

## 手順
1) corpus差分を検出
2) lexical/dense/late を順に再構築
3) Smoke-eval合格で切替

## 基準
再現率・遅延・コストのSLO内合格
