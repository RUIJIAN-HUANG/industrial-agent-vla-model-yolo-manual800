# YOLO Manual-994

Complete model delivery bundle for the V2 single-bin industrial perception
service.

## Artifact

- Artifact ID: `yolo_manual994_yolo11n_e10_cpu`
- Architecture: YOLO11n
- Checkpoint: [`best.pt`](best.pt)
- Checkpoint SHA-256: `sha256:67a70dd1f575919bde9184a993097771bbdbaa7516cdd251c1f91b2a490f1e5c`
- Class map: [`configs/class_map.single_bin_v2.json`](configs/class_map.single_bin_v2.json)
- Class-map SHA-256: `sha256:839fdb76e458f9148959e727d289a29495130ce9c868b10b57adcaab4323ba06`

## Contents

| Path | Purpose |
|---|---|
| `best.pt` | YOLO11n checkpoint for runtime deployment |
| `configs/class_map.single_bin_v2.json` | Frozen seven-class V2 class map |
| `configs/yolo_service_config.manual994.json` | YOLO service deployment settings |
| `configs/perception.yolo-local.manual994.json` | Supervisor perception integration block |
| `reports/training_summary.md` | Training and held-out test summary |
| `reports/dataset_merge_summary.json` | Dataset merge and label validation summary |
| `metrics/train_results.csv` | Ultralytics epoch metrics |
| `metrics/*.png`, `metrics/*.jpg` | PR curve, confusion matrices, and prediction previews |
| `CHECKSUMS.json` | Machine-readable artifact identity |
| `CHECKSUMS.sha256.txt` | Flat SHA-256 manifest for delivered files |

## Deployment

Use the checkpoint with the pinned identity below:

```powershell
$env:YOLO_USE_MOCK = "0"
$env:YOLO_CHECKPOINT_PATH = "<repo-or-artifact-path>\manual994\best.pt"
$env:YOLO_CHECKPOINT_SHA = "sha256:67a70dd1f575919bde9184a993097771bbdbaa7516cdd251c1f91b2a490f1e5c"
$env:YOLO_CLASS_MAP_SHA = "sha256:839fdb76e458f9148959e727d289a29495130ce9c868b10b57adcaab4323ba06"
$env:YOLO_DEVICE = "cpu"
```

The YOLO Agent only performs independent visual object detection. It does not
generate robot actions, control robot arms, read online ground truth, or grant
control tokens.
