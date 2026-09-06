# Experiment log

## Phase 1 — YOLO-World smoke test

The initial three-image run detected people but missed hard hats and safety vests. This established the inference pipeline and motivated a labeled mini-evaluation set.

## Phase 2 — Mini-evaluation baseline

Dataset: 12 development images with 150 annotated boxes.

- Overall mAP50: 70.32%
- Overall mAP50-95: 40.92%
- Person AP50-95: 65.35%
- Hard-hat AP50-95: 46.53%
- Safety-vest AP50-95: 10.87%

Decision: keep YOLO-World as the open-vocabulary baseline, but do not use the vest output for automatic compliance decisions.

## Phase 3 — Prompt ablation

Five controlled prompt configurations were evaluated with fixed images, annotations, model weights, and validation settings.

- Best isolated hard-hat prompt: `safety helmet` (48.40% AP50-95).
- Best isolated vest prompt: `reflective safety vest` (13.22% AP50-95).
- `high visibility vest` reduced vest performance and was rejected.

The C1 combination `[person, safety helmet, reflective safety vest]` produced the best overall result:

- Overall mAP50: 73.00%
- Overall mAP50-95: 41.87%
- Person AP50-95: 64.92%
- Hard-hat AP50-95: 48.32%
- Safety-vest AP50-95: 12.38%

Decision: freeze C1 as the current development configuration.

## Phase 4 — Threshold calibration

Maximum-F1 candidates on the development set:

- Person: threshold 0.121, precision 95.15%, recall 98.33%, F1 96.72%.
- Hard hat: threshold 0.014, precision 86.98%, recall 88.25%, F1 87.61%.
- Safety vest: no acceptable threshold. At the curve floor, precision is 31.34%, recall is 56.76%, and F1 is 40.38%.

Decision: person and hard-hat thresholds remain provisional. Vest absence must produce an uncertain result. The next phase is dataset expansion and a supervised/second-detector comparison, followed by evaluation on a frozen test set.
