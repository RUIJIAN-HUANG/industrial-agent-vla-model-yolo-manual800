# Industrial Agent VLA YOLO Model Artifacts

Versioned model artifacts for the V2 single-bin industrial perception service.

This repository stores YOLO model delivery bundles used by the main
`industrial-agent-vla` repository. Each version includes checkpoint identity,
class map, checksums, model card, training/test results, and deployment config.

## Available Artifacts

| Version | Artifact ID | Checkpoint SHA-256 | Location |
|---|---|---|---|
| Manual-800 | `yolo_manual800_yolo11n_e10_cpu` | `sha256:2a8beca3ff52f6cd7a2f81f087df71793889d7017f81156a8286f4ffb106080f` | root legacy files |
| Manual-994 | `yolo_manual994_yolo11n_e10_cpu` | `sha256:67a70dd1f575919bde9184a993097771bbdbaa7516cdd251c1f91b2a490f1e5c` | [`manual994/`](manual994/) |
| Manual-1394 Wrench | `yolo_manual1394_wrench_yolo11n_e5_cpu` | `sha256:6bb9d5006e732426458322e7258d3043e367317dfd46ae54920f9605a90b9536` | [`manual1394_wrench/`](manual1394_wrench/) |

## Manual-994 Summary

Manual-994 was fine-tuned from Manual-800 with 200 newly corrected samples.
It contains 994 images split into 810 train, 105 val, and 79 test images.

Held-out test metrics:

```text
mAP50:     0.936
mAP50-95:  0.793
Precision: 0.905
Recall:    0.887
```

See [`manual994/MODEL_CARD.md`](manual994/MODEL_CARD.md) and
[`manual994/CHECKSUMS.json`](manual994/CHECKSUMS.json) for details.

The YOLO Agent only performs independent visual object detection. It does not
generate robot actions, control robot arms, read online GT, or grant control
tokens.
