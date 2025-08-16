---
{
  "id": "sop-2025-08-16-high-fidelity",
  "title": "High‑fidelityルートの公開審査（法務/医療/対外）",
  "version": "1.0.0",
  "status": "active",
  "owners": [
    "オペ/品質人格"
  ],
  "reviewers": [
    "統合応答人格",
    "メタ批判人格",
    "法務オブザーバ人格"
  ],
  "confidentiality": "internal",
  "route_hint": "HighFid",
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
高リスク領域における出力の安全性・正確性・引用整合性を保証する。

## 手順
1) Answererの草案をCoVe×2で検証
2) AISで未支持主張検出
3) リスク&コンプライアンスの承認
4) 未支持/疑義は保留出力

## 基準
圧縮≤2×、citation必須、AIS pass≥90%、未支持≤2%

## 記録
verifications/ に検証ログ、decisions/ に公開可否の記録
