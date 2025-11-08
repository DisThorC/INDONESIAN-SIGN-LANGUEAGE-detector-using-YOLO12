# Indonesian Sign Language Detector (YOLO12 FPS Boost)

Real‑time Indonesian Sign Language (ISL) gesture detection using Ultralytics YOLOv12 with performance knobs for higher FPS while maintaining accuracy.

### Core Features
- Fine‑tuned YOLO12s (50 epochs) final weights (`best.pt`, `last.pt`)
- Realtime webcam inference (threaded capture, frame stride skipping, dynamic `imgsz`)
- Optional tracking + temporal smoothing
- Semantic transition smoothing + Markov sequence decoding (opt‑in)
- Lightweight evaluation (mAP, confusion matrix) & class distribution script

### Goals
High FPS (>20) on modest GPUs by tuning resolution, stride, and disabling non‑essential steps when needed.

---
## Quick Start (Windows PowerShell)

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
# Install Torch for your environment (example CUDA 12.1):
# pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
```

Run realtime (10–15s demo):
```powershell
python .\realtime.py --weights runs\train\exp_y12s_50e_640\weights\best.pt --device cuda --duration 15
```

Alternate module run:
```powershell
python -m src.yolo12.realtime --weights runs\train\exp_y12s_50e_640\weights\best.pt --duration 15
```

Image / video inference:
```powershell
python -m src.yolo12.infer --weights runs/train/exp_y12s_50e_640/weights/best.pt --source 0
```

Check Torch GPU:
```powershell
python - <<'PY'
import torch; print('Torch', torch.__version__, 'CUDA', torch.cuda.is_available())
PY
```

---
## Performance Flags

```text
--vid-stride N        Skip frames (2–3 for speed)
--imgsz N             Inference resolution (320–640)
--no-track            Disable tracker
--smooth-window N     Temporal smoothing (e.g. 5)
--semantic-smooth     Enable semantic prior filtering
--semantic-threshold  Transition probability minimum (default 0.15)
--threaded            Enable threaded capture (default)
--max-det N           Limit detections per frame
--torch-compile       Use torch.compile if available
```

Example high‑speed run (stride + reduced imgsz + no tracking):
```powershell
python .\realtime.py --duration 15 --threaded --vid-stride 2 --imgsz 512 --no-track
```

Semantic smoothing + Markov:
```powershell
python .\realtime.py --duration 15 --threaded --vid-stride 2 --smooth-window 5 --semantic-smooth --semantic-threshold 0.15 --semantic-map configs\semantic_prior.json
```

---
## Classes
| ID | Name |
|----|------|
| 0  | Ayah |
| 1  | Halo |
| 2  | Kakak |
| 3  | Minum |
| 4  | Rumah |
| 5  | Sama-sama |
| 6  | Sehat |
| 7  | Teman |
| 8  | Terima kasih |
| 9  | Tidur |

---
## Troubleshooting
- If FPS low: reduce `--imgsz`, increase `--vid-stride`, disable smoothing/tracking.
- CUDA errors: reinstall Torch matching your driver.
- Webcam not found: list cameras `python .\scripts\list_cameras.py --max-index 10` (if script retained).

---
## License
MIT — see `LICENSE`.

Author: DISTHORC

