# Code Memory Cheat Sheet

## The Golden Rule: ALL transformations follow the SAME pattern!

```python
for r in range(rows):
    for c in range(cols):
        tp = MATRIX @ array([[r],[c],[1]])
        rd, cd = int(tp[0,0]), int(tp[1,0])   # Add /tp[2,0] for projective
        im2[rd,cd] = im1[r,c]
```

---

# 1. IMPORTS (Same for ALL)

```python
from PIL import Image
from numpy import array, zeros
from matplotlib.pyplot import imshow, show, subplot
```

**Memory trick:** "PIL-NUM-MAT" (Pillow, Numpy, Matplotlib)

---

# 2. LOAD IMAGE (Same for ALL)

```python
img = Image.open('image.jpg').convert('L')  # 'L' = grayscale
im1 = array(img)
rows, cols = im1.shape[0], im1.shape[1]
```

**Memory trick:** "Open-Convert-Array-Shape"

---

# 3. THE THREE TRANSFORMATION MATRICES

## Only memorize these 3 matrices!

| Transform | Matrix | Key Values |
|-----------|--------|------------|
| **Scale 2x** | `[[2,0],[0,2]]` | Just the scale factor |
| **Rotate 30°** | `[[.866,-.5,0],[.5,.866,0],[0,0,1]]` | cos=.866, sin=.5 |
| **Projective** | `[[.8,.3,10],[-.7,.9,30],[.0028,.0036,1]]` | Last row NOT [0,0,1] |

### Memory Trick for Rotation:
```
"8-6-6 and 5" = cos(30°)=0.866, sin(30°)=0.5

Rotation = | cos  -sin  0 |
           | sin   cos  0 |
           | 0     0    1 |
```

---

# 4. THE KEY DIFFERENCE

## Scale & Rotation (Affine):
```python
rd = int(tp[0,0])
cd = int(tp[1,0])
```

## Projective (DIVIDE BY W!):
```python
rd = int(tp[0,0] / tp[2,0])  # <-- DIVIDE!
cd = int(tp[1,0] / tp[2,0])  # <-- DIVIDE!
```

**Memory trick:** "Projective = Perspective = divide by w"

---

# 5. COMPLETE MINIMAL CODE (15 lines each)

## Scale:
```python
S = [[2,0],[0,2]]
im2 = zeros([rows*2+1, cols*2+1])
for r in range(rows):
    for c in range(cols):
        tp = S @ array([[r],[c]])
        im2[int(tp[0,0]), int(tp[1,0])] = im1[r,c]
```

## Rotation:
```python
R = [[.866,-.5,0],[.5,.866,0],[0,0,1]]
im2 = zeros([rows+200, cols+200])
for r in range(rows):
    for c in range(cols):
        tp = R @ array([[r],[c],[1]])
        rd, cd = int(tp[0,0]), int(tp[1,0])
        if rd>=0 and cd>=0: im2[rd,cd] = im1[r,c]
```

## Projective:
```python
P = [[.8,.3,10],[-.7,.9,30],[.0028,.0036,1]]
im2 = zeros([rows+200, cols+200])
for r in range(rows):
    for c in range(cols):
        tp = P @ array([[r],[c],[1]])
        rd = int(tp[0,0]/tp[2,0])  # DIVIDE!
        cd = int(tp[1,0]/tp[2,0])  # DIVIDE!
        if rd>=0 and cd>=0: im2[rd,cd] = im1[r,c]
```

---

# 6. INTERPOLATION (Just 2 formulas)

## Linear (1D):
```python
f(x) = f1 + (x-x1)*(f2-f1)/(x2-x1)
```

## Bilinear (2D):
```python
f(x,y) = f11*(1-dx)*(1-dy) + f21*dx*(1-dy) + f12*(1-dx)*dy + f22*dx*dy
```

**Memory trick:** "Weighted average of 4 corners"

---

# 7. MATRIX OPERATIONS

## Array vs Matrix:
```python
a * b   # Element-wise (array)
a @ b   # Matrix multiplication (ALWAYS use @)
```

## Inverse:
```python
from numpy import linalg as la
ai = la.inv(a)
```

---

# 8. RGB CHANNELS

```python
im[:,:,0]  # Red
im[:,:,1]  # Green
im[:,:,2]  # Blue
```

**Memory trick:** "0-1-2 = R-G-B"

---

# 9. DISPLAY

```python
subplot(1,2,1); imshow(im1, cmap='gray')
subplot(1,2,2); imshow(im2, cmap='gray')
show()
```

---

# FINAL SUMMARY CARD (Print this!)

```
┌─────────────────────────────────────────────────────────┐
│                    CODE MEMORY CARD                      │
├─────────────────────────────────────────────────────────┤
│  IMPORTS: PIL, numpy(array,zeros), matplotlib           │
├─────────────────────────────────────────────────────────┤
│  LOAD: open→convert('L')→array→shape                    │
├─────────────────────────────────────────────────────────┤
│  MATRICES:                                              │
│    Scale:    [[2,0],[0,2]]                              │
│    Rotate:   [[.866,-.5,0],[.5,.866,0],[0,0,1]]         │
│    Project:  [[.8,.3,10],[-.7,.9,30],[.0028,.0036,1]]   │
├─────────────────────────────────────────────────────────┤
│  LOOP:                                                  │
│    for r in range(rows):                                │
│      for c in range(cols):                              │
│        tp = MATRIX @ array([[r],[c],[1]])               │
│        rd, cd = int(tp[0,0]), int(tp[1,0])              │
│        im2[rd,cd] = im1[r,c]                            │
├─────────────────────────────────────────────────────────┤
│  PROJECTIVE ONLY: rd = rd/tp[2,0], cd = cd/tp[2,0]      │
├─────────────────────────────────────────────────────────┤
│  SHOW: subplot(1,2,1); imshow(im1); show()              │
└─────────────────────────────────────────────────────────┘
```

---

# PRACTICE WRITING (Do this 3 times!)

Write from memory:

1. **Imports** (3 lines)
2. **Load image** (3 lines)
3. **Rotation matrix** (1 line)
4. **Loop** (5 lines)
5. **Display** (3 lines)

**Total: ~15 lines to remember!**

---

# COMMON ANGLES TO REMEMBER

| Angle | cos | sin |
|-------|-----|-----|
| 30° | 0.866 | 0.5 |
| 45° | 0.707 | 0.707 |
| 60° | 0.5 | 0.866 |
| 90° | 0 | 1 |

**Memory trick:**
- 30° = "8-6-6 and 5"
- 45° = "7-0-7 both"
- 60° = reverse of 30°

---

*Print this and practice writing 3 times!*
