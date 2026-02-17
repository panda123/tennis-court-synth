# Tennis Court Synth 🎾

Synthetic tennis court image generator with auto-labeled keypoints for training pose/keypoint detection models.

## Features
- Full 3D court renderer with 18 auto-labeled keypoints
- 5 camera angle presets (behind_baseline, side, broadcast, high, corner)
- 7 court color palettes with random variation
- YOLO-Pose and COCO output formats
- No real data needed — pure synthetic generation

## Quick Start

```bash
# Generate 100 synthetic court images
python scripts/generate.py --count 100 --output-dir ./dataset

# Visualize a sample
python scripts/visualize.py --image dataset/images/train/00000.jpg --label dataset/labels/train/00000.txt

# Run tests
python -m pytest tests/ -v
```

## Dependencies
- numpy
- opencv-python (cv2)

## License
MIT
