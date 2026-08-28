# YOLO V2 Manual-994 Training Summary

Dataset:

- Images: 994 unique images
- Split: 810 train / 105 val / 79 test
- Sources: 794 manual800 + 200 newly corrected samples
- Classes: 7
- Base model: previous manual800 `best.pt`
- Training: YOLO11n, 10 epochs, image size 640, batch 8, CPU

Final validation metrics from epoch 10:

| Metric | Value |
|---|---:|
| Precision | 0.889 |
| Recall | 0.904 |
| mAP50 | 0.930 |
| mAP50-95 | 0.807 |

Final test metrics:

| Class | Precision | Recall | mAP50 | mAP50-95 |
|---|---:|---:|---:|---:|
| all | 0.905 | 0.887 | 0.936 | 0.793 |
| shaft_upright | 0.952 | 0.951 | 0.982 | 0.868 |
| shaft_inverted | 0.877 | 0.850 | 0.915 | 0.739 |
| hex_nut | 0.806 | 0.833 | 0.899 | 0.793 |
| open_end_wrench | 0.868 | 0.737 | 0.833 | 0.584 |
| bin_box | 0.967 | 0.987 | 0.990 | 0.889 |
| bin_slot | 0.935 | 0.971 | 0.980 | 0.939 |
| bin_carry_handle | 0.932 | 0.878 | 0.956 | 0.738 |

Model:

```text
C:\Users\TJW\Documents\Codex\2026-08-28\new-chat-2\outputs\yolo_runs\manual994_yolo11n_finetune_e10_cpu\weights\best.pt
```

SHA256:

```text
67a70dd1f575919bde9184a993097771bbdbaa7516cdd251c1f91b2a490f1e5c
```

Notes:

- Compared with the manual800 summary, test mAP50-95 improved from 0.771 to 0.793.
- The combined test split is larger than manual800's original test split because it includes newly corrected samples, so treat the comparison as practical evidence rather than a perfectly fixed benchmark.
- `open_end_wrench` remains the weakest class and is still the best next cleanup target.
