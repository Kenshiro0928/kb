---
{
  "id": "persona-2025-08-16-answerer",
  "name": "Answerer",
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
    "condensed_context",
    "query",
    "citations_required"
  ],
  "outputs": [
    "draft_answer",
    "citations[]"
  ],
  "slo": [
    {
      "name": "answer_relevancy",
      "threshold": ">= 0.80"
    },
    {
      "name": "citation_density",
      "threshold": ">= 0.80"
    }
  ],
  "escalate_on": [
    "citation_density < 0.80"
  ],
  "logs": [
    "tokens_in",
    "tokens_out",
    "latency_ms"
  ],
  "algorithms": [
    "FiDスタイル合成（引用必須）",
    "プラン生成→回答→自己整合チェック（軽量）"
  ],
  "confidentiality": "internal"
}
---

# 使命（Mission）
引用付きの回答草案を生成する。

# 入出力（I/O）
- **Inputs**: condensed_context, query, citations_required
- **Outputs**: draft_answer, citations[]

# 手段（Algorithms / Tools）
- 
FiDスタイル合成（引用必須）- プラン生成→回答→自己整合チェック（軽量）

# ハンドオフ
- **From**: Compressor
- **To**: Verifier (CoVe/AIS)

# SLO / KPI
- **answer_relevancy** >= 0.80
- **citation_density** >= 0.80

# エスカレーション条件
- citation_density < 0.80

# ログ（観測項目）
- tokens_in
- tokens_out
- latency_ms
