# Digital Image Processing - Sample Papers with Detailed Solutions

This document contains questions from sample papers with comprehensive answers.

---

# Table of Contents

1. [Image Formation & Storage Calculations](#1-image-formation--storage-calculations)
2. [Homogeneous Coordinates](#2-homogeneous-coordinates)
3. [Transformation Matrices](#3-transformation-matrices)
4. [Eigenvalues of Rotation Matrices](#4-eigenvalues-of-rotation-matrices)
5. [Pseudo Inverse Solution](#5-pseudo-inverse-solution)
6. [Sampling and Quantization](#6-sampling-and-quantization)
7. [Bilinear Interpolation](#7-bilinear-interpolation)
8. [Image Rotation Size Calculation](#8-image-rotation-size-calculation)
9. [Projective Transformations](#9-projective-transformations)
10. [Reverse Warping](#10-reverse-warping)
11. [Line at Infinity](#11-line-at-infinity)
12. [SVD Decomposition](#12-svd-decomposition)
13. [Affine Transformation on Lines](#13-affine-transformation-on-lines)
14. [Camera Matrix & Null Space](#14-camera-matrix--null-space)

---

# 1. Image Formation & Storage Calculations

## Q1.1: What is the height of the inverted tree image?

**Given:**
- Tree height: 15 m
- Distance from camera: 100 m
- Image plane distance: 17 mm

**Solution:**

Using similar triangles (pinhole camera model):

```
Image Height / Focal Length = Object Height / Object Distance

h_image / 17 mm = 15 m / 100 m

h_image = (15 × 17) / 100
h_image = 255 / 100
h_image = 2.55 mm
```

**Answer: The inverted tree image height is 2.55 mm**

---

## Q1.2: Storage for RGB Image (1024 × 256, 0-255 levels)

**Given:**
- Image size: 1024 × 256 pixels
- Intensity levels: 0-255 (8 bits per channel)
- RGB color image (3 channels)

**Solution:**

```
Bits per pixel = 8 bits × 3 channels = 24 bits

Total bits = Width × Height × Bits per pixel
Total bits = 1024 × 256 × 24
Total bits = 6,291,456 bits

Total bytes = 6,291,456 / 8 = 786,432 bytes

Megabytes = 786,432 / (1024 × 1024) = 0.75 MB
```

**Answer:**
- **Bits: 6,291,456 bits**
- **Megabytes: 0.75 MB (or 768 KB)**

---

## Q1.3: Storage for RGB True Color Image (1024 × 2048, 24-bit)

**Given:**
- Image size: 1024 × 2048 pixels
- 24-bit true color (8 bits per channel × 3 channels)

**Solution:**

```
Total bits = 1024 × 2048 × 24 = 50,331,648 bits

Total bytes = 50,331,648 / 8 = 6,291,456 bytes

KB = 6,291,456 / 1024 = 6,144 KB

MB = 6,144 / 1024 = 6 MB
```

**Answer:**
- **Bits: 50,331,648 bits**
- **Megabytes: 6 MB**

---

## Q1.4: What are x, y, and f in f(x,y)?

**Question:** An image is defined as a two-dimensional function, f(x, y). What are x and y, and what is f?

**Answer:**

| Symbol | Term | Description |
|--------|------|-------------|
| **x** | Spatial coordinate (row) | Vertical position in the image |
| **y** | Spatial coordinate (column) | Horizontal position in the image |
| **f** | Intensity/Amplitude | Gray level or brightness value at position (x,y) |

- **x and y** are called **spatial coordinates**
- **f** is called the **intensity** or **gray level** of the image at that point

For color images, f(x,y) returns a vector [R, G, B] representing color intensities.

---

# 2. Homogeneous Coordinates

## Q2.1: 3D Point [30 45 75 5]ᵀ in Homogeneous Coordinates

**Question:** [30 45 75 5]ᵀ is a 3D point in homogeneous coordinates. Write three different variations and coordinates in 3D in-homogeneous (Cartesian) coordinates.

**Solution:**

**Homogeneous form:** [x, y, z, w]ᵀ = [30, 45, 75, 5]ᵀ

**Three different variations** (multiply by any scalar k ≠ 0):

| Variation | k | Homogeneous Coordinates |
|-----------|---|------------------------|
| 1 | k = 2 | [60, 90, 150, 10]ᵀ |
| 2 | k = 0.5 | [15, 22.5, 37.5, 2.5]ᵀ |
| 3 | k = 10 | [300, 450, 750, 50]ᵀ |

**In-homogeneous (Cartesian) coordinates:**

Divide by w:
```
X = x/w = 30/5 = 6
Y = y/w = 45/5 = 9
Z = z/w = 75/5 = 15
```

**Answer: Cartesian coordinates = (6, 9, 15)**

---

## Q2.2: 2D Point [30 45 0]ᵀ in Homogeneous Coordinates

**Question:** [30 45 0]ᵀ is a 2D point in homogeneous coordinates. Write three different variations and corresponding in-homogeneous coordinates.

**Solution:**

**Important:** When w = 0, the point represents a **point at infinity** (ideal point).

**Three different variations:**

| Variation | k | Homogeneous Coordinates |
|-----------|---|------------------------|
| 1 | k = 2 | [60, 90, 0]ᵀ |
| 2 | k = 5 | [150, 225, 0]ᵀ |
| 3 | k = 0.1 | [3, 4.5, 0]ᵀ |

**In-homogeneous coordinates:**

Since w = 0, we cannot divide by w. This represents a **point at infinity** in the direction (30, 45) or simplified direction (2, 3).

**Answer: This is a point at infinity in direction (30, 45). No finite Cartesian representation exists.**

---

## Q2.3: 2D Point [30 45 5]ᵀ in Homogeneous Coordinates

**Question:** [30 45 5]ᵀ is a 2D point in homogeneous coordinates. Write three variations and Cartesian coordinates.

**Solution:**

**Three different variations:**

| Variation | k | Homogeneous Coordinates |
|-----------|---|------------------------|
| 1 | k = 2 | [60, 90, 10]ᵀ |
| 2 | k = 3 | [90, 135, 15]ᵀ |
| 3 | k = 0.2 | [6, 9, 1]ᵀ |

**In-homogeneous (Cartesian) coordinates:**

```
X = x/w = 30/5 = 6
Y = y/w = 45/5 = 9
```

**Answer: Cartesian coordinates = (6, 9)**

---

# 3. Transformation Matrices

## Q3.1: Rectangle to Parallelogram Transformation

**Question:** Find the transformation matrix that transforms a rectangle to a parallelogram.

**Given points:**
- Rectangle: (0,0), (0,10), (15,0), (15,10)
- Parallelogram: (0,3), (0,13), (15,0), (15,10)

**Solution:**

This is a **shearing transformation** in the y-direction.

Observing the transformation:
- Point (0,0) → (0,3): y increased by 3
- Point (15,0) → (15,0): no change
- The shear depends on x position

The transformation can be written as:
```
x' = x
y' = y + shear_factor × (max_x - x) × (3/15)
```

For a simpler affine model:
```
x' = x
y' = y - 0.2x + 3
```

**Transformation Matrix (Homogeneous):**

```
    | 1    0    0  |
T = | -0.2  1    3  |
    | 0    0    1  |
```

**Verification:**
- (0,0,1) → (0, 3, 1) = (0, 3) ✓
- (15,0,1) → (15, -3+3, 1) = (15, 0) ✓
- (0,10,1) → (0, 13, 1) = (0, 13) ✓
- (15,10,1) → (15, 10, 1) = (15, 10) ✓

---

## Q3.2: Independent 2×2 Transformation Matrices

**Question:** Write 2×2 matrices for: 3× scaling, 15° rotation, 0.5 shearing in y-axis.

**Solution:**

### Scaling Matrix (3×):
```
S = | 3  0 |
    | 0  3 |
```

### Rotation Matrix (15°):
```
cos(15°) = 0.9659
sin(15°) = 0.2588

R = | 0.9659  -0.2588 |
    | 0.2588   0.9659 |
```

### Shearing Matrix (0.5 in y-axis):
```
Sh = | 1    0   |
     | 0.5  1   |
```

---

## Q3.3: Composite Transformation Analysis

**Question:** A planar object goes through -30° rotation, then 1.6× scaling along x-axis only, then 30° rotation. Describe the net transformation:

```
| 1.75000  0.43301 |
| 0.43301  1.25000 |
```

**Solution:**

Let's verify: R(30°) × S(1.6, 1) × R(-30°)

```
R(-30°) = | 0.866   0.5   |
          | -0.5    0.866 |

S(1.6,1) = | 1.6  0 |
           | 0    1 |

R(30°) = | 0.866  -0.5  |
         | 0.5    0.866 |
```

**Interpretation:**

The resulting matrix is **symmetric**, which indicates:
1. It's a **pure scaling** along rotated axes
2. The eigenvalues are the scale factors along principal axes
3. This is equivalent to scaling by 1.6 along a direction rotated 30° from x-axis

**The net effect is anisotropic scaling** - the object is stretched more in one direction than the other, with the principal axes rotated 30° from the original coordinate system.

---

## Q3.4: General Transformation Matrices (Homogeneous 3×3)

### Translation:
```
T(tx, ty) = | 1  0  tx |
            | 0  1  ty |
            | 0  0  1  |
```

### Rotation:
```
R(θ) = | cos(θ)  -sin(θ)  0 |
       | sin(θ)   cos(θ)  0 |
       | 0        0       1 |
```

### Scaling:
```
S(sx, sy) = | sx  0   0 |
            | 0   sy  0 |
            | 0   0   1 |
```

### Shearing (x-direction):
```
Shx(k) = | 1  k  0 |
         | 0  1  0 |
         | 0  0  1 |
```

### Shearing (y-direction):
```
Shy(k) = | 1  0  0 |
         | k  1  0 |
         | 0  0  1 |
```

---

## Q3.5: Inverse of Transformation Matrices

### Inverse of Translation:
```
T⁻¹(tx, ty) = | 1  0  -tx |
              | 0  1  -ty |
              | 0  0   1  |
```

### Inverse of Rotation:
```
R⁻¹(θ) = R(-θ) = | cos(θ)   sin(θ)  0 |
                  | -sin(θ)  cos(θ)  0 |
                  | 0        0       1 |
```

### Inverse of Scaling:
```
S⁻¹(sx, sy) = | 1/sx  0     0 |
              | 0     1/sy  0 |
              | 0     0     1 |
```

### Inverse of Shearing (x-direction):
```
Shx⁻¹(k) = | 1  -k  0 |
           | 0   1  0 |
           | 0   0  1 |
```

### Inverse of Shearing (y-direction):
```
Shy⁻¹(k) = | 1   0  0 |
           | -k  1  0 |
           | 0   0  1 |
```

---

## Q3.6: Rotation 30° followed by Scaling (2, 0.8)

**Question:** What is the 2D transformation matrix to rotate 30° about origin followed by scaling of 2 and 0.8 along x and y axes?

**Solution:**

```
cos(30°) = 0.866
sin(30°) = 0.5

R(30°) = | 0.866  -0.5  |
         | 0.5    0.866 |

S(2, 0.8) = | 2    0   |
            | 0    0.8 |

Composite = S × R = | 2×0.866   2×(-0.5)  | = | 1.732  -1.0   |
                    | 0.8×0.5   0.8×0.866 |   | 0.4     0.693 |
```

**In homogeneous coordinates (3×3):**
```
    | 1.732  -1.0   0 |
T = | 0.4    0.693  0 |
    | 0      0      1 |
```

---

## Q3.7: Butterfly Translation Transformation

**Question:** Find the transformation matrix for the butterfly diagram (translation to the right).

**Solution:**

Looking at the butterfly images, the transformation appears to be a **pure translation** along the y-axis (moving right).

Observing the displacement (approximately 4-5 units to the right):

```
    | 1  0  0  |
T = | 0  1  5  |
    | 0  0  1  |
```

**Justification:** The butterfly shape, size, and orientation remain unchanged. Only its position has shifted horizontally, which is characteristic of a pure translation transformation.

---

# 4. Eigenvalues of Rotation Matrices

## Q4.1: Eigenvalues of 3D Rotation Matrix (60° along x-axis)

**Question:** What are the eigenvalues of a 3D rotation matrix that rotates 60° along the x-axis?

**Solution:**

The 3D rotation matrix about x-axis:

```
Rx(60°) = | 1    0        0      |
          | 0    cos(60°) -sin(60°) |
          | 0    sin(60°)  cos(60°) |

        = | 1    0     0      |
          | 0    0.5   -0.866 |
          | 0    0.866  0.5   |
```

**Eigenvalues of any 3D rotation matrix:**

For rotation by angle θ, the eigenvalues are always:
- λ₁ = 1 (corresponding to the axis of rotation)
- λ₂ = cos(θ) + i·sin(θ) = e^(iθ)
- λ₃ = cos(θ) - i·sin(θ) = e^(-iθ)

For θ = 60°:
- λ₁ = **1**
- λ₂ = cos(60°) + i·sin(60°) = **0.5 + i·0.866**
- λ₃ = cos(60°) - i·sin(60°) = **0.5 - i·0.866**

**Answer: The three eigenvalues are: 1, (0.5 + 0.866i), (0.5 - 0.866i)**

---

## Q4.2: Eigenvalues of Given Rotation Matrix

**Question:** For the rotation matrix below, write the three eigenvalues (write directly):

```
    | 0.2588    0      0.9659 |
R = | 0        1.0000  0      |
    | -0.9659   0      0.2588 |
```

**Solution:**

This is a rotation about the y-axis. Observing:
- cos(θ) = 0.2588 → θ = 75°
- sin(θ) = 0.9659

**Eigenvalues:**
- λ₁ = **1** (axis of rotation is y-axis)
- λ₂ = cos(75°) + i·sin(75°) = **0.2588 + 0.9659i**
- λ₃ = cos(75°) - i·sin(75°) = **0.2588 - 0.9659i**

**The one real eigenvector** corresponds to eigenvalue 1, which is the y-axis: **[0, 1, 0]ᵀ**

---

# 5. Pseudo Inverse Solution

## Q5.1: Prove x = (AᵀA)⁻¹Aᵀb

**Question:** For a linear system Ax = b, prove that the solution through pseudo-inverse is x = (AᵀA)⁻¹Aᵀb.

**Proof:**

**Step 1:** Start with the system Ax = b

When the system is overdetermined (more equations than unknowns), we seek the least-squares solution that minimizes ||Ax - b||².

**Step 2:** The error is e = Ax - b

To minimize ||e||² = ||Ax - b||², we take the derivative and set to zero:

```
d/dx ||Ax - b||² = 0
d/dx (Ax - b)ᵀ(Ax - b) = 0
d/dx (xᵀAᵀAx - 2xᵀAᵀb + bᵀb) = 0
2AᵀAx - 2Aᵀb = 0
```

**Step 3:** Solving for x:

```
AᵀAx = Aᵀb
x = (AᵀA)⁻¹Aᵀb
```

**Step 4:** Define the pseudo-inverse:

```
A⁺ = (AᵀA)⁻¹Aᵀ
```

Therefore: **x = A⁺b = (AᵀA)⁻¹Aᵀb** ∎

**Note:** This assumes AᵀA is invertible (A has full column rank).

---

# 6. Sampling and Quantization

## Q6.1: Sampling a Function

**Question:** Given the annotated function, fill the tables for sampling.

**From the graph (approximating values):**

### Real values of y:

| x | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|---|---|
| y | 1.0 | 0.7 | 1.3 | 2.5 | 2.8 | 1.0 | 0.3 | 0.2 |

### Integer values of y (nearest):

| x | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|---|---|
| y | 1 | 1 | 1 | 2 | 3 | 1 | 0 | 0 |

### Doubled sampling rate:

| x | 0 | 0.5 | 1 | 1.5 | 2 | 2.5 | 3 | 3.5 | 4 | 4.5 | 5 | 5.5 | 6 | 6.5 | 7 |
|---|---|-----|---|-----|---|-----|---|-----|---|-----|---|-----|---|-----|---|
| y | 1 | 1 | 1 | 1 | 1 | 2 | 2 | 3 | 3 | 2 | 1 | 1 | 0 | 0 | 0 |

---

## Q6.2: Quantize Diagonal for 8 Levels

**Question:** Quantize the diagonal of the 8×8 image for 8 levels (values 0-7).

**Diagonal values:** 0.983, 0.413, 0.758, 0.069, 0.564, 0.606, 0.927, 0.115

**Quantization formula:** level = floor(value × 8)

| Original | Calculation | Quantized Level |
|----------|-------------|-----------------|
| 0.983 | 0.983 × 8 = 7.86 | **7** |
| 0.413 | 0.413 × 8 = 3.30 | **3** |
| 0.758 | 0.758 × 8 = 6.06 | **6** |
| 0.069 | 0.069 × 8 = 0.55 | **0** |
| 0.564 | 0.564 × 8 = 4.51 | **4** |
| 0.606 | 0.606 × 8 = 4.85 | **4** |
| 0.927 | 0.927 × 8 = 7.42 | **7** |
| 0.115 | 0.115 × 8 = 0.92 | **0** |

**Answer: [7, 3, 6, 0, 4, 4, 7, 0]**

---

## Q6.3: Quantize 3×3 Image for 256 Levels

**Question:** Quantize the image for 256 levels (values 0-255).

**Original:**
```
0.1671  0.0069  0.1621
0.4147  0.3485  0.6146
0.9701  0.4444  0.2256
```

**Formula:** level = floor(value × 255)

**Quantized:**
```
| 0.1671×255=42.6 → 42  | 0.0069×255=1.8 → 1   | 0.1621×255=41.3 → 41  |
| 0.4147×255=105.7 → 105| 0.3485×255=88.9 → 88 | 0.6146×255=156.7 → 156|
| 0.9701×255=247.4 → 247| 0.4444×255=113.3 → 113| 0.2256×255=57.5 → 57 |
```

**Answer:**
```
|  42  |   1  |  41  |
| 105  |  88  | 156  |
| 247  | 113  |  57  |
```

---

# 7. Bilinear Interpolation

## Q7.1: Find Intensity at Point (1.75, 1.00)

**Question:** Four neighboring pixels of point (1.75, 1.00) have intensity values:
- Top-Left (1,1): 120
- Top-Right (2,1): 125
- Bottom-Left (1,2): 115
- Bottom-Right (2,2): 110

Find intensity at (1.75, 1.00) using bilinear interpolation.

**Solution:**

**Step 1:** Identify the four corner points
```
(x1, y1) = (1, 1), f(1,1) = 120
(x2, y1) = (2, 1), f(2,1) = 125
(x1, y2) = (1, 2), f(1,2) = 115
(x2, y2) = (2, 2), f(2,2) = 110
```

**Step 2:** Calculate interpolation weights
```
x = 1.75, y = 1.00

Δx = x - x1 = 1.75 - 1 = 0.75
Δy = y - y1 = 1.00 - 1 = 0.00
```

**Step 3:** Apply bilinear interpolation formula
```
f(x,y) = f(1,1)(1-Δx)(1-Δy) + f(2,1)(Δx)(1-Δy) + f(1,2)(1-Δx)(Δy) + f(2,2)(Δx)(Δy)

f(1.75, 1.00) = 120(0.25)(1) + 125(0.75)(1) + 115(0.25)(0) + 110(0.75)(0)
              = 120(0.25) + 125(0.75) + 0 + 0
              = 30 + 93.75
              = 123.75
```

**Answer: Intensity at (1.75, 1.00) = 123.75 ≈ 124**

---

# 8. Image Rotation Size Calculation

## Q8.1: Rotated Image Size (250×110, 15°)

**Question:** An image has 250 rows and 110 columns. If rotated by 15°, find the size of the resulting image.

**Solution:**

For a rotated image, we need to find the bounding box.

**Original corners:** (0,0), (250,0), (0,110), (250,110)

**Rotation transformation:**
```
x' = x·cos(15°) - y·sin(15°)
y' = x·sin(15°) + y·cos(15°)

cos(15°) = 0.9659
sin(15°) = 0.2588
```

**Transform all corners:**

| Corner | Original | Rotated x' | Rotated y' |
|--------|----------|------------|------------|
| 1 | (0, 0) | 0 | 0 |
| 2 | (250, 0) | 241.5 | 64.7 |
| 3 | (0, 110) | -28.5 | 106.2 |
| 4 | (250, 110) | 213.0 | 170.9 |

**Bounding box:**
```
x_min = -28.5, x_max = 241.5 → Width = 270
y_min = 0, y_max = 170.9 → Height = 171
```

**Using formula:**
```
New_Width = |W × cos(θ)| + |H × sin(θ)|
          = |110 × 0.9659| + |250 × 0.2588|
          = 106.2 + 64.7 = 170.9 ≈ 171

New_Height = |W × sin(θ)| + |H × cos(θ)|
           = |110 × 0.2588| + |250 × 0.9659|
           = 28.5 + 241.5 = 270
```

**Answer: New image size = 270 rows × 171 columns**

---

# 9. Projective Transformations

## Q9.1: Find 2D Projective Transformation

**Question:** Find the projective transformation from rectangle to quadrilateral:

**Source points:**
- (0, 0) → (0, 0)
- (0, 6) → (0, 2)
- (5, 0) → (4, 0)
- (5, 6) → (8/3, 4/3)

**Solution:**

The projective transformation has the form:
```
| kx' |   | a  b  c | | x |
| ky' | = | d  e  f | | y |
| k   |   | g  h  1 | | 1 |
```

**Setting up equations from point correspondences:**

**Point (0,0) → (0,0):**
```
c = 0, f = 0
```

**Point (0,6) → (0,2):**
```
6b/(6h+1) = 0 → b = 0
6e/(6h+1) = 2 → e = (6h+1)/3
```

**Point (5,0) → (4,0):**
```
5a/(5g+1) = 4 → a = 4(5g+1)/5
5d/(5g+1) = 0 → d = 0
```

**Point (5,6) → (8/3, 4/3):**

Using the constraints and solving:

```
a = 4/5, b = 0, c = 0
d = 0, e = 1/3, f = 0
g = 1/10, h = 0
```

**Transformation Matrix:**
```
    | 4/5   0    0 |   | 0.8    0      0 |
H = | 0    1/3   0 | = | 0      0.333  0 |
    | 1/10  0    1 |   | 0.1    0      1 |
```

**Verification:**
- (5,6,1) → H×[5,6,1]ᵀ = [4, 2, 1.5]ᵀ → (4/1.5, 2/1.5) = (8/3, 4/3) ✓

---

# 10. Reverse Warping

## Q10.1: Reverse Warping with Bilinear Interpolation

**Question:** Given a 20×10 or 11×11 image and transformation matrix T, compute the value at [5, 4]ᵀ using reverse warping.

**Given transformation T:**
```
T = | 0.35355  -0.35355  -0.00000 |
    | 0.56569   0.56569  -5.65685 |
    | 0.00000   0.00000   1.00000 |

T⁻¹ = | 1.41421   0.88388   5.00000 |
      |-1.41421   0.88388   5.00000 |
      | 0.00000   0.00000   1.00000 |
```

**Solution:**

**Step 1:** Apply inverse transformation to find source coordinates
```
[x_src]       [5]
[y_src] = T⁻¹ [4]
[  1  ]       [1]

x_src = 1.41421(5) + 0.88388(4) + 5 = 7.07 + 3.54 + 5 = 15.61
y_src = -1.41421(5) + 0.88388(4) + 5 = -7.07 + 3.54 + 5 = 1.47
```

**Step 2:** Source position (15.61, 1.47) is within the image bounds

**Step 3:** Apply bilinear interpolation using the four neighboring pixels at (15,1), (16,1), (15,2), (16,2)

Look up values from the image matrix and apply bilinear interpolation formula.

**Note:** If the computed source coordinates fall outside the image bounds, the pixel cannot be computed.

---

# 11. Line at Infinity

## Q11.1: Finding Image of Line at Infinity

**Question:** If world parallelism can be observed in different directions in an image, can we find the image of line at infinity?

**Answer: YES**

**Explanation:**

**Concept:**
- In the real world, parallel lines meet at a "point at infinity"
- Each set of parallel lines has its own vanishing point
- The **line at infinity** is the line connecting all vanishing points

**How to find it:**

1. **Identify parallel lines** in the image (e.g., edges of buildings, road markings)

2. **Find vanishing points:**
   - Extend each set of parallel lines until they intersect
   - Each intersection is a vanishing point

3. **Line at infinity:**
   - Connect two or more vanishing points from different directions
   - This line is the image of the line at infinity

**Mathematical representation:**
- In homogeneous coordinates, the line at infinity is l∞ = [0, 0, 1]ᵀ
- Under projective transformation, it maps to a finite line in the image

**Practical use:**
- Used in camera calibration
- Helps determine the projective transformation (homography)
- Essential for metric rectification

---

# 12. SVD Decomposition

## Q12.1: Decompose Composite Transformation using SVD

**Question:** Given the transformation matrix and its SVD, find rotation, scaling, and translation matrices:

```
    | 0.6    -1.04   -20 |
T = | 0.693   0.4    -50 |
    | 0       0       1  |

SVD of top-left 2×2:
| 1  0 | | 1.2  0   | | 0.500  -0.866 |
| 0  1 | | 0    0.8 | | 0.866   0.500 |
  U         Σ            Vᵀ
```

**Solution:**

From SVD: A = UΣVᵀ

**Rotation Matrix (from Vᵀ):**
```
R = | 0.500  -0.866  0 |
    | 0.866   0.500  0 |
    | 0       0      1 |

This is rotation by -60° (or 300°)
since cos(-60°) = 0.5, sin(-60°) = -0.866
```

**Scaling Matrix (from Σ):**
```
S = | 1.2  0    0 |
    | 0    0.8  0 |
    | 0    0    1 |

Scale factors: 1.2 along x, 0.8 along y
```

**Translation Matrix (from last column):**
```
Tr = | 1  0  -20 |
     | 0  1  -50 |
     | 0  0   1  |
```

**Verification:** T = Tr × S × R (or different order based on interpretation)

---

# 13. Affine Transformation on Lines

## Q13.1: Slope of Transformed Line

**Question:** If a line y = mx + c undergoes an affine transformation, find the slope of the transformed line.

**Solution:**

**General affine transformation:**
```
| x' |   | a  b | | x |   | tx |
| y' | = | c  d | | y | + | ty |
```

**Take two points on the line:**
- Point 1: (x₁, y₁) where y₁ = mx₁ + c
- Point 2: (x₂, y₂) where y₂ = mx₂ + c

**Transform both points:**
```
x₁' = ax₁ + by₁ + tx = ax₁ + b(mx₁ + c) + tx = (a + bm)x₁ + bc + tx
y₁' = cx₁ + dy₁ + ty = cx₁ + d(mx₁ + c) + ty = (c + dm)x₁ + dc + ty

x₂' = (a + bm)x₂ + bc + tx
y₂' = (c + dm)x₂ + dc + ty
```

**New slope:**
```
m' = (y₂' - y₁') / (x₂' - x₁')
   = [(c + dm)(x₂ - x₁)] / [(a + bm)(x₂ - x₁)]
   = (c + dm) / (a + bm)
```

**Answer: The slope of the transformed line is m' = (c + dm) / (a + bm)**

Where a, b, c, d are elements of the affine transformation matrix.

---

# 14. Camera Matrix & Null Space

## Q14.1: Prove C is Null Space of P

**Question:** Given camera matrix P = KR[I|-C], where C = [Cx, Cy, Cz, 1]ᵀ, prove that C is the null space of P.

**Proof:**

**Step 1:** Expand the camera matrix
```
P = KR[I|-C] = KR[I | -C]

where I is 3×3 identity, C is 3×1 camera center
```

**Step 2:** Write explicitly
```
P = KR × | 1  0  0  -Cx |
         | 0  1  0  -Cy |
         | 0  0  1  -Cz |
```

**Step 3:** Multiply P by homogeneous C
```
P × | Cx |   | 1  0  0  -Cx | | Cx |   | Cx - Cx |   | 0 |
    | Cy | = | 0  1  0  -Cy | | Cy | = | Cy - Cy | = | 0 |
    | Cz |   | 0  0  1  -Cz | | Cz |   | Cz - Cz |   | 0 |
    | 1  |                    | 1  |   |         |

After premultiplying by KR (which doesn't change zero vector):
P × C_homogeneous = KR × [0, 0, 0]ᵀ = [0, 0, 0]ᵀ
```

**Step 4:** Conclusion

Since PC = 0, the camera center C (in homogeneous coordinates [Cx, Cy, Cz, 1]ᵀ) lies in the null space of P.

**Physical interpretation:** The camera center projects to no point in the image (it's behind/at the camera), hence P×C = 0.

∎

---

## Q14.2: Find Size After 3D Transformation

**Question:** Find the size of 3D snapshot after transformation. Original size: (100, 50, 80)

**Transformation matrix:**
```
    | 2  1  0   50 |
T = | 0  1  1   90 |
    | 0  2  0.5  0 |
    | 0  0  0    1 |
```

**Solution:**

Transform the 8 corners of the original bounding box and find the new bounding box.

**Original corners:** All combinations of (0,100), (0,50), (0,80) in x, y, z

**Key corners to transform:**
```
(0,0,0,1) → (50, 90, 0, 1) = (50, 90, 0)
(100,0,0,1) → (250, 90, 0, 1) = (250, 90, 0)
(0,50,0,1) → (100, 140, 100, 1) = (100, 140, 100)
(0,0,80,1) → (50, 170, 40, 1) = (50, 170, 40)
(100,50,80,1) → (300, 270, 140, 1) = (300, 270, 140)
```

**New bounding box:**
- X: min=50, max=300 → **Width = 250**
- Y: min=90, max=270 → **Depth = 180**
- Z: min=0, max=140 → **Height = 140**

**Answer: New size approximately (250, 180, 140)**

---

# 15. Image Enhancement vs Image Restoration

## Q15.1: Differentiate Enhancement and Restoration

| Aspect | Image Enhancement | Image Restoration |
|--------|-------------------|-------------------|
| **Goal** | Improve visual appearance for human perception | Recover original image from degraded version |
| **Approach** | Subjective - based on viewer preference | Objective - based on mathematical models |
| **Knowledge Required** | No prior knowledge of degradation | Requires degradation model |
| **Mathematical Model** | Heuristic techniques | Uses inverse filtering, deconvolution |
| **Examples** | Contrast stretching, sharpening, histogram equalization | Deblurring, noise removal, deconvolution |
| **Evaluation** | Subjective (looks better?) | Objective (closer to original?) |
| **Reversibility** | Not concerned with original | Aims to recover original |

**Key Difference:** Enhancement makes images "look better" while restoration tries to "undo" known degradations using mathematical models of how the image was corrupted.

---

# Quick Reference: Important Formulas

## Storage Calculation
```
Bits = M × N × k × channels
Bytes = Bits / 8
KB = Bytes / 1024
MB = KB / 1024
```

## Homogeneous to Cartesian
```
(x, y, w) → (x/w, y/w)
(x, y, z, w) → (x/w, y/w, z/w)
```

## Bilinear Interpolation
```
f(x,y) = f₁₁(1-Δx)(1-Δy) + f₂₁(Δx)(1-Δy) + f₁₂(1-Δx)(Δy) + f₂₂(Δx)(Δy)
```

## Rotation Matrix (2D)
```
R(θ) = | cos(θ)  -sin(θ) |
       | sin(θ)   cos(θ) |
```

## Eigenvalues of 3D Rotation
```
λ₁ = 1
λ₂ = cos(θ) + i·sin(θ)
λ₃ = cos(θ) - i·sin(θ)
```

## Rotated Image Size
```
New_Width = |W×cos(θ)| + |H×sin(θ)|
New_Height = |W×sin(θ)| + |H×cos(θ)|
```

## Pseudo-Inverse
```
x = (AᵀA)⁻¹Aᵀb = A⁺b
```

---

*Document prepared for exam preparation - Digital Image Processing*
