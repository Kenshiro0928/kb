---
{
  "id": "sop-2025-08-16-rag-router-retriever-prefilter-reranker-composer-compressor-answerer-verifier-mo",
  "title": "RAG運用ランブック（Router→Retriever→Prefilter→Reranker→Composer→Compressor→Answerer→Verifier→Monitor）",
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
適応型RAGパイプラインを安定運用する標準手順を定義する。

## 前提
routes/* と policies/rag_policy.yaml に従う。ログは verifications/ と evals/runs/ に保存。

## 手順
1) Routerで c,f,h,r 推定→Preset決定
2) Hybrid取得N→前置M→再ランクK
3) RAPTORで階層要約→質問依存圧縮
4) 生成（引用必須）→CoVe/AIS検証
5) MonitorでSLO監視→逸脱はECOへ

## 出力
verified_answer, citations, logs

## 失敗モードと対策
低再現率→HyDE/拡張、時事ズレ→時間重みλ↑、中域喪失→RAPTOR3層、コスト超過→圧縮↑/再ランクOFF（HighFid除く）
