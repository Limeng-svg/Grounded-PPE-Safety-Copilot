# Results

This directory contains curated, directly previewable artifacts from the Colab experiments. Full generated `outputs/` directories and ZIP archives are excluded from Git.

- `smoke_test/`: initial three-image predictions and manual review.
- `mini_eval_baseline/`: A0 metrics, curves, confusion matrices, and validation previews.
- `prompt_ablation/`: five-run prompt comparison plus representative H1 and V2 predictions.
- `C1_combined/`: combined-prompt metrics, curves, predictions, and comparison JSON.
- `threshold_calibration/`: class-specific threshold candidates and confidence curves.

All reported values come from the same 12-image development set unless explicitly stated otherwise. Use the JSON and CSV files as the numerical source of truth; prediction montages are qualitative evidence only.
