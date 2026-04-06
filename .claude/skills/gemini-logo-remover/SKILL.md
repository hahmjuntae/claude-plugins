---
name: gemini-logo-remover
description: Remove Gemini logos, watermarks, or AI-generated image markers using OpenCV inpainting.
---

# Gemini Logo Remover

OpenCV inpainting으로 AI 생성 이미지의 로고/워터마크 제거.

## Setup

```bash
pip install opencv-python numpy pillow --break-system-packages
```

## 좌표 지정 제거

```python
import cv2, numpy as np

def remove_region(input_path, output_path, x1, y1, x2, y2, radius=5):
    img = cv2.imread(input_path)
    h, w = img.shape[:2]
    mask = np.zeros((h, w), dtype=np.uint8)
    cv2.rectangle(mask, (x1, y1), (x2, y2), 255, -1)
    result = cv2.inpaint(img, mask, radius, cv2.INPAINT_TELEA)
    cv2.imwrite(output_path, result)
```

## 코너 로고 제거

```python
def remove_corner_logo(input_path, output_path, corner='bottom_right',
                       w_ratio=0.1, h_ratio=0.1, padding=10):
    img = cv2.imread(input_path)
    h, w = img.shape[:2]
    lw, lh = int(w * w_ratio), int(h * h_ratio)
    coords = {
        'bottom_right': (w-lw-padding, h-lh-padding, w-padding, h-padding),
        'bottom_left': (padding, h-lh-padding, lw+padding, h-padding),
        'top_right': (w-lw-padding, padding, w-padding, lh+padding),
        'top_left': (padding, padding, lw+padding, lh+padding)
    }
    x1, y1, x2, y2 = coords[corner]
    mask = np.zeros((h, w), dtype=np.uint8)
    cv2.rectangle(mask, (x1, y1), (x2, y2), 255, -1)
    result = cv2.inpaint(img, mask, 5, cv2.INPAINT_TELEA)
    cv2.imwrite(output_path, result)
```

## 좌표 확인

```python
img = cv2.imread(input_path)
h, w = img.shape[:2]
print(f"Size: {w}x{h}")
# Gemini 별 로고: 보통 우하단. 일반적 좌표: x1=w-150, y1=h-100, x2=w-130, y2=h-55
```

## 참고

- `/mnt/user-data/outputs/`에 저장 후 `present_files` 도구 사용
- 균일한 배경의 작은 영역에서 가장 효과적
- Gemini 로고는 보통 우하단 위치
- 실제 로고 위치/크기에 따라 좌표/비율 조정 필요
