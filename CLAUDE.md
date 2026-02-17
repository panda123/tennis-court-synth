# CLAUDE.md — Project Instructions

## What This Is
A synthetic tennis court image generator for training keypoint detection models.
**Focus: behind-baseline camera angle only** (amateur phone filming from behind the court).

## Reference Implementation
The full working code is at: `/Users/haoqinggeng/.openclaw/workspace/tennis-analyzer-YOLOv8/synthetic_court_gen.py` (858 lines)
Refactor this into clean, modular scripts. Only keep the behind_baseline angle — remove side, broadcast, high, corner presets.

## Project Structure
```
scripts/generate.py      — main generator CLI
scripts/visualize.py     — keypoint overlay visualization
tests/test_generate.py   — pytest tests
```

## Python Environment
```bash
source ~/.openclaw/workspace/tennis-analyzer-YOLOv8/venv/bin/activate
```

## Key Technical Details
- ITF standard court dimensions (23.77m × 10.97m)
- 18 keypoints: 4 baseline corners × 2 (near/far) + 3 service line × 2 + 4 net points
- 3D→2D via rotation + perspective projection
- YOLO-Pose label format: class cx cy w h [x1 y1 v1 x2 y2 v2 ...]
- Keypoints outside frame → visibility=0

## Camera: Behind Baseline Only
- Camera position: behind the near baseline, ~1.5-2m height (phone held by standing person)
- Randomize: slight left/right offset, height variation, small angle jitter
- This matches amateur tennis filming angle (phone on tripod or hand-held behind court)
- Do NOT include broadcast, side, high, or corner angles
