# YOLO Manual-800 Model Card

## Purpose

Manual-800 is a YOLO11n checkpoint for the V2 single-bin industrial perception
task. It detects `shaft_upright`, `shaft_inverted`, `hex_nut`,
`open_end_wrench`, `bin_box`, `bin_slot`, and `bin_carry_handle`.

## Identity

| Field | Value |
|---|---|
| Artifact ID | `yolo_manual800_yolo11n_e10_cpu` |
| Checkpoint | `best.pt` |
| Checkpoint SHA-256 | `sha256:2a8beca3ff52f6cd7a2f81f087df71793889d7017f81156a8286f4ffb106080f` |
| Training seed | `7` |
| Training date | `2026-08-27` |
| Epochs / image size / batch | `10 / 640 / 8` |
| Device | CPU |
| Ultralytics | `8.4.104` |

The checkpoint is an external artifact. Never use a file with a different
digest in production.

## Held-out metrics

```text
mAP50:     0.925
mAP50-95:  0.771
Precision: 0.902
Recall:    0.880
```

These are same-domain held-out metrics and must be complemented by the real
three-camera inference probe before production use.

## Limitations

`open_end_wrench` remains the weakest class, and `bin_carry_handle` needs more
real-camera occlusion coverage.
