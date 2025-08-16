---
{
  "id": "persona-2025-08-16-compressor-question-dependent",
  "name": "Compressor (Question-Dependent)",
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
    "summary_tree",
    "query",
    "preset"
  ],
  "outputs": [
    "condensed_context",
    "compression_ratio",
    "retained_recall"
  ],
  "slo": [
    {
      "name": "retained_recall",
      "threshold": ">= 0.95"
    },
    {
      "name": "compression_stability",
      "threshold": ">= 0.90"
    }
  ],
  "escalate_on": [
    "retained_recall < 0.95",
    "preset == HighFid かつ compression_ratio > 2.0"
  ],
  "logs": [
    "compression_ratio",
    "tokens_in",
    "tokens_out"
  ],
  "algorithms": [
    "LongLLMLingua / 質問依存サマリ",
    "ルール: Balanced 2–4×, Fresh 2–3×, HighFid ≤2×, LongDoc ≈3×, LowLatency 4–8×"
  ],
  "confidentiality": "internal"
}
---

# 使命（Mission）
質問に必要な根拠を保ったままトークンを削減する。

# 入出力（I/O）
- **Inputs**: summary_tree, query, preset
- **Outputs**: condensed_context, compression_ratio, retained_recall

# 手段（Algorithms / Tools）
- 
LongLLMLingua / 質問依存サマリ- ルール: Balanced 2–4×, Fresh 2–3×, HighFid ≤2×, LongDoc ≈3×, LowLatency 4–8×

# ハンドオフ
- **From**: Composer (RAPTOR)
- **To**: Answerer

# SLO / KPI
- **retained_recall** >= 0.95
- **compression_stability** >= 0.90

# エスカレーション条件
- retained_recall < 0.95
- preset == HighFid かつ compression_ratio > 2.0

# ログ（観測項目）
- compression_ratio
- tokens_in
- tokens_out
