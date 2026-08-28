# Industrial Agent VLA — YOLO Manual-800

Versioned model artifacts for the V2 single-bin industrial perception service.

This repository contains the model identity, class map, and model card. The
`best.pt` checkpoint is intentionally distributed through the team's artifact
store rather than committed to Git. Retrieve the immutable artifact identified
in `CHECKSUMS.json`, verify its SHA-256, and mount it as `best.pt` for real-mode
deployment.

## Artifact

- Artifact ID: `yolo_manual800_yolo11n_e10_cpu`
- Architecture: YOLO11n
- Checkpoint: `best.pt`
- Checkpoint SHA-256: `sha256:2a8beca3ff52f6cd7a2f81f087df71793889d7017f81156a8286f4ffb106080f`
- Class map: [`configs/class_map.single_bin_v2.json`](configs/class_map.single_bin_v2.json)
- Class-map SHA-256: `sha256:839fdb76e458f9148959e727d289a29495130ce9c868b10b57adcaab4323ba06`

See [`MODEL_CARD.md`](MODEL_CARD.md) for training details, metrics, and
limitations. The consuming code and deployment contract remain in the main
`industrial-agent-vla` repository.
