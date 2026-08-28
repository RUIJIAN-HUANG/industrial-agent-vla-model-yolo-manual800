# YOLO Manual-994 Model Card

## Purpose

Manual-994 is a YOLO11n checkpoint for the V2 single-bin industrial perception
task. It detects `shaft_upright`, `shaft_inverted`, `hex_nut`,
`open_end_wrench`, `bin_box`, `bin_slot`, and `bin_carry_handle`.

The YOLO Agent outputs object class, bounding box, confidence, and inference
latency for the latest RGB images. It preserves raw prediction results for
offline mAP evaluation and provides visual perception information to the
Supervisor/VLA stack. It does not generate actions, control robot arms, read
online GT, or grant control tokens.

## Identity

| Field | Value |
|---|---|
| Artifact ID | `yolo_manual994_yolo11n_e10_cpu` |
| Checkpoint | `best.pt` |
| Checkpoint SHA-256 | `sha256:67a70dd1f575919bde9184a993097771bbdbaa7516cdd251c1f91b2a490f1e5c` |
| Class map SHA-256 | `sha256:839fdb76e458f9148959e727d289a29495130ce9c868b10b57adcaab4323ba06` |
| Service config SHA-256 | `sha256:40c815abdd3766db3277e022f0ba259b1ba12c7d90e829c39fe981a2858e3d8f` |
| Training seed | `7` |
| Training date | `2026-08-28` |
| Epochs / image size / batch | `10 / 640 / 8` |
| Device | CPU |
| Ultralytics | `8.4.104` |

Never use a checkpoint file with a different digest in production.

## Dataset

Manual-994 contains 994 unique images with manually cleaned YOLO labels:

| Split | Images |
|---|---:|
| train | 810 |
| val | 105 |
| test | 79 |

Sources:

| Source | Images |
|---|---:|
| Manual-800 | 794 |
| Newly corrected samples | 200 |

## Held-Out Metrics

```text
mAP50:     0.936
mAP50-95:  0.793
Precision: 0.905
Recall:    0.887
```

Compared with Manual-800, same-domain held-out mAP50-95 improved from `0.771`
to `0.793`. The Manual-994 test split includes newly corrected samples, so this
is practical candidate evidence rather than a perfectly fixed-benchmark
comparison.

## Per-Class Test Metrics

| Class | Precision | Recall | mAP50 | mAP50-95 |
|---|---:|---:|---:|---:|
| all | 0.905 | 0.887 | 0.936 | 0.793 |
| `shaft_upright` | 0.952 | 0.951 | 0.982 | 0.868 |
| `shaft_inverted` | 0.877 | 0.850 | 0.915 | 0.739 |
| `hex_nut` | 0.806 | 0.833 | 0.899 | 0.793 |
| `open_end_wrench` | 0.868 | 0.737 | 0.833 | 0.584 |
| `bin_box` | 0.967 | 0.987 | 0.990 | 0.889 |
| `bin_slot` | 0.935 | 0.971 | 0.980 | 0.939 |
| `bin_carry_handle` | 0.932 | 0.878 | 0.956 | 0.738 |

## Limitations

- `open_end_wrench` remains the weakest class, especially for tight box quality.
- `bin_carry_handle` still needs more real-camera occlusion coverage.
- Same-domain held-out metrics must be complemented by the real three-camera
  inference probe before production gating.
