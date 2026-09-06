# Data

`mini_eval/` is the small development-only evaluation set used by notebooks 02-04.

## Mini-evaluation set

- Images: 12
- Person boxes: 60
- Hard-hat boxes: 53
- Safety-vest boxes: 37
- Total boxes: 150
- Annotation format: YOLO normalized `class_id x_center y_center width height`

Class IDs are defined in `mini_eval/dataset.yaml`.

This set has been used for model evaluation, prompt selection, and threshold selection. It must not be presented as an independent final test set. Before redistributing or reusing these images as a public benchmark, add source URLs, authorship, and license information for every image.

Future large datasets should not be committed directly to Git. Store them in Google Drive or an external dataset service and document a reproducible download/preparation procedure.
