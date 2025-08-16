---
{
  "id": "sop-2025-08-16-long-doc-raptor-3",
  "title": "Long‑doc取り込み（RAPTOR 3層）",
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
  "route_hint": "LongDoc",
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
規格/長報告/RFPなど長文の中域喪失を回避。

## 手順
1) 章→節→段落のRAPTOR木生成
2) 重要根拠を冒頭/末尾に固定
3) 圧縮≈3×で要約を合成

## 監視
coverage_score ≥ 0.80 を維持

## 記録
ingestion/raptor/ にレシピ更新
