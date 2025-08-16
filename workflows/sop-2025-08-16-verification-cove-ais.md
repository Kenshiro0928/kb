---
{
  "id": "sop-2025-08-16-verification-cove-ais",
  "title": "Verification（CoVe＋AIS）標準手順",
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
回答の事実性・引用整合性の担保。

## 手順
1) CoVe計画→自己検証→修正
2) AISで対立証拠探索
3) 未達なら再取得or保留

## 基準
AIS pass≥90%、未支持≤2%

## ログ
verifications/ に cove_logs / ais_logs を保存
