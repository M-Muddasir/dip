# Digital Image Processing - Exam Preparation Guide
## Chapters 1 & 2: Complete Study Material

**Textbook:** Digital Image Processing, 4th Edition
**Authors:** Rafael C. Gonzalez & Richard E. Woods
**Chapters Covered:** 1 (Introduction) & 2 (Digital Image Fundamentals)

---

# Table of Contents

1. [Chapter 1: Introduction](#chapter-1-introduction)
   - [1.1 What is Digital Image Processing?](#11-what-is-digital-image-processing)
   - [1.2 Origins of Digital Image Processing](#12-origins-of-digital-image-processing)
   - [1.3 Examples of Fields Using DIP](#13-examples-of-fields-using-digital-image-processing)
   - [1.4 Fundamental Steps in DIP](#14-fundamental-steps-in-digital-image-processing)
   - [1.5 Components of an Image Processing System](#15-components-of-an-image-processing-system)

2. [Chapter 2: Digital Image Fundamentals](#chapter-2-digital-image-fundamentals)
   - [2.1 Elements of Visual Perception](#21-elements-of-visual-perception)
   - [2.2 Light and the Electromagnetic Spectrum](#22-light-and-the-electromagnetic-spectrum)
   - [2.3 Image Sensing and Acquisition](#23-image-sensing-and-acquisition)
   - [2.4 Image Sampling and Quantization](#24-image-sampling-and-quantization)
   - [2.5 Relationships Between Pixels](#25-some-basic-relationships-between-pixels)
   - [2.6 Mathematical Tools in DIP](#26-introduction-to-mathematical-tools)

3. [Formula Sheet](#formula-sheet)
4. [Practice Problems with Solutions](#practice-problems-with-solutions)
5. [Multiple Choice Questions](#multiple-choice-questions)
6. [Short Answer Questions](#short-answer-questions)
7. [Previous Year Question Patterns](#previous-year-question-patterns)
8. [Quick Revision Notes](#quick-revision-notes)

---

# Chapter 1: Introduction

## 1.1 What is Digital Image Processing?

### Definition of a Digital Image

A **digital image** is a two-dimensional function, f(x, y), where:
- **x** and **y** are spatial (plane) coordinates
- The amplitude of f at any pair of coordinates (x, y) is called the **intensity** or **gray level** of the image at that point
- When x, y, and the intensity values of f are all **finite, discrete quantities**, we call the image a **digital image**

### Definition of Digital Image Processing

**Digital image processing** refers to processing digital images by means of a digital computer.

> **Key Point:** A digital image is composed of a finite number of elements, each of which has a particular location and value. These elements are called **picture elements**, **image elements**, **pels**, or **pixels**.

### Three Levels of Image Processing

| Level | Input | Output | Examples |
|-------|-------|--------|----------|
| **Low-level** | Image | Image | Noise reduction, contrast enhancement, sharpening |
| **Mid-level** | Image | Attributes | Segmentation, classification, recognition of individual objects |
| **High-level** | Attributes | Understanding | Making sense of an ensemble of recognized objects, cognitive functions |

### Continuum from Image Processing to Computer Vision

```
Image Processing ←————————————————————————→ Computer Vision
     |                    |                        |
 Low-level            Mid-level               High-level
 (Images)            (Attributes)          (Understanding)
```

---

## 1.2 Origins of Digital Image Processing

### Historical Timeline

| Year/Period | Milestone | Significance |
|-------------|-----------|--------------|
| **1920s** | Bartlane cable picture transmission | First digital images transmitted between London and New York |
| **1921** | First Bartlane picture | Used 5 distinct intensity levels |
| **1929** | Improved Bartlane | Increased to 15 intensity levels |
| **1960s** | Jet Propulsion Laboratory | Processed images from Ranger 7 spacecraft (first US spacecraft to reach the Moon) |
| **1964** | Ranger 7 mission | Computer techniques used to enhance lunar images |
| **1970s** | CT Scanner invention | Godfrey N. Hounsfield invented the first commercial CT scanner |
| **1979** | Nobel Prize | Hounsfield and Cormack awarded Nobel Prize in Medicine for CT |

### Key Historical Facts (Exam Important)

1. **First digital picture transmission:** 1920s via submarine cable (Bartlane system)
2. **Initial intensity levels:** 5 levels, later improved to 15 levels
3. **Space imaging breakthrough:** 1964, Ranger 7 lunar mission
4. **Medical imaging revolution:** 1970s, CT scanner by Hounsfield
5. **First successful image processing application:** Improving newspaper image transmission quality

---

## 1.3 Examples of Fields Using Digital Image Processing

### Organization by Electromagnetic Spectrum

The electromagnetic spectrum is the primary basis for categorizing imaging applications:

```
Gamma Rays → X-rays → Ultraviolet → Visible → Infrared → Microwave → Radio Waves
   |           |          |           |          |           |           |
  PET        CT/X-ray   Microscopy  Camera    Thermal    Radar        MRI
  SPECT      Medical    Litho       Remote    Night      SAR
  Astronomy  Industrial            Sensing    Vision
```

### Detailed Application Areas

#### 1. Gamma-Ray Imaging
- **Sources:** Radioactive isotopes, nuclear reactions
- **Applications:**
  - Nuclear medicine (PET - Positron Emission Tomography)
  - SPECT (Single Photon Emission Computed Tomography)
  - Astronomical observations
  - Detection of radioactive materials

#### 2. X-Ray Imaging
- **Applications:**
  - Medical diagnostics (chest X-rays, dental X-rays)
  - CT scanning (Computed Tomography)
  - Industrial inspection
  - Airport security (baggage scanning)
  - Angiography (blood vessel imaging)

#### 3. Ultraviolet Imaging
- **Applications:**
  - Fluorescence microscopy
  - Lithography in semiconductor manufacturing
  - Astronomical imaging
  - Document verification (currency, security documents)

#### 4. Visible Light Imaging
- **Wavelength Range:** 400-700 nm
- **Applications:**
  - Photography and videography
  - Microscopy (light microscopy)
  - Remote sensing
  - Industrial inspection
  - Entertainment and media
  - Surveillance and security

#### 5. Infrared Imaging
- **Types:**
  - Near-infrared (NIR): 0.7-1.0 μm
  - Mid-infrared: 1.0-5.0 μm
  - Far-infrared (thermal): 5.0-100 μm
- **Applications:**
  - Thermal imaging (night vision)
  - Remote sensing
  - Weather forecasting
  - Medical thermography
  - Industrial heat detection

#### 6. Microwave Imaging
- **Applications:**
  - Radar imaging
  - SAR (Synthetic Aperture Radar)
  - Remote sensing through clouds
  - Weather monitoring

#### 7. Radio Wave Imaging
- **Primary Application:** MRI (Magnetic Resonance Imaging)
- **Principle:** Uses radio waves and magnetic fields
- **Advantage:** No ionizing radiation, excellent soft tissue contrast

### Non-Electromagnetic Imaging

| Type | Principle | Applications |
|------|-----------|--------------|
| **Ultrasound** | Sound waves (2-20 MHz) | Medical imaging, fetal monitoring, echocardiography |
| **Electron Microscopy** | Electron beams | Nanoscale imaging, materials science |
| **Synthetic/Computer Graphics** | Mathematical models | Simulation, visualization, virtual reality |

---

## 1.4 Fundamental Steps in Digital Image Processing

### The Image Processing Pipeline

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         IMAGE PROCESSING PIPELINE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│    ┌──────────────┐     ┌──────────────┐     ┌──────────────┐              │
│    │    Image     │────▶│    Image     │────▶│    Image     │              │
│    │ Acquisition  │     │ Enhancement  │     │ Restoration  │              │
│    └──────────────┘     └──────────────┘     └──────────────┘              │
│           │                                          │                       │
│           ▼                                          ▼                       │
│    ┌──────────────┐     ┌──────────────┐     ┌──────────────┐              │
│    │    Color     │────▶│   Wavelets   │────▶│ Compression  │              │
│    │  Processing  │     │ & Transforms │     │              │              │
│    └──────────────┘     └──────────────┘     └──────────────┘              │
│           │                                          │                       │
│           ▼                                          ▼                       │
│    ┌──────────────┐     ┌──────────────┐     ┌──────────────┐              │
│    │Morphological │────▶│ Segmentation │────▶│Representation│              │
│    │  Processing  │     │              │     │ & Description│              │
│    └──────────────┘     └──────────────┘     └──────────────┘              │
│           │                                          │                       │
│           ▼                                          ▼                       │
│    ┌──────────────┐     ┌──────────────┐                                   │
│    │   Feature    │────▶│   Pattern    │                                   │
│    │  Extraction  │     │ Recognition  │                                   │
│    └──────────────┘     └──────────────┘                                   │
│                                                                              │
│                    ┌──────────────────────┐                                 │
│                    │   Knowledge Base     │ (Guides all processes)          │
│                    └──────────────────────┘                                 │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Detailed Description of Each Step

#### 1. Image Acquisition
- **Definition:** The process of capturing an image using a sensor
- **Components:** Imaging sensor + digitizer
- **Output:** Digital image in numerical form
- **Examples:** Camera, scanner, X-ray detector, MRI scanner

#### 2. Image Enhancement
- **Definition:** Process of manipulating an image to make it more suitable for a specific application
- **Characteristics:**
  - Subjective process
  - Application-dependent
  - No universal "best" method
- **Techniques:** Contrast stretching, histogram equalization, filtering, sharpening

#### 3. Image Restoration
- **Definition:** Process of improving the appearance of an image based on mathematical or probabilistic models of image degradation
- **Characteristics:**
  - Objective process
  - Uses a model of the degradation
  - Attempts to recover the original image
- **Techniques:** Inverse filtering, Wiener filtering, blind deconvolution

#### 4. Color Image Processing
- **Definition:** Processing of color images
- **Components:** Color models (RGB, HSI, CMYK), color transformations
- **Applications:** Color correction, color enhancement, pseudocolor processing

#### 5. Wavelets and Multi-resolution Processing
- **Definition:** Representing images at multiple resolutions
- **Key Concept:** Wavelet transforms decompose images into different frequency components
- **Applications:** Compression, denoising, feature extraction

#### 6. Compression
- **Definition:** Reducing the storage required for an image
- **Types:**
  - **Lossless:** Perfect reconstruction (PNG, GIF)
  - **Lossy:** Approximate reconstruction (JPEG)
- **Metrics:** Compression ratio, image quality

#### 7. Morphological Processing
- **Definition:** Tools for extracting image components useful for shape representation
- **Basic Operations:** Erosion, dilation, opening, closing
- **Applications:** Boundary extraction, region filling, connected components

#### 8. Segmentation
- **Definition:** Partitioning an image into its constituent regions or objects
- **Approaches:**
  - Edge-based
  - Region-based
  - Thresholding
  - Clustering
- **Challenge:** One of the most difficult tasks in image processing

#### 9. Representation and Description
- **Representation:** How to represent a region (boundary vs. interior)
- **Description:** Extracting features (shape descriptors, texture features)

#### 10. Feature Extraction
- **Definition:** Extracting attributes that result in quantitative information of interest
- **Types:** Shape features, texture features, color features

#### 11. Pattern Recognition/Classification
- **Definition:** Assigning a label to an object based on its features
- **Approaches:** Statistical, structural, neural networks, deep learning

---

## 1.5 Components of an Image Processing System

### System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                  IMAGE PROCESSING SYSTEM                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌─────────────┐                          ┌─────────────┐       │
│  │   Image     │                          │   Display   │       │
│  │  Sensors    │                          │  (Monitor)  │       │
│  └──────┬──────┘                          └──────▲──────┘       │
│         │                                        │               │
│         ▼                                        │               │
│  ┌─────────────┐    ┌─────────────┐    ┌───────┴───────┐       │
│  │ Specialized │───▶│  Computer   │───▶│   Software    │       │
│  │  Hardware   │    │             │    │               │       │
│  └─────────────┘    └──────┬──────┘    └───────────────┘       │
│                            │                                     │
│                            ▼                                     │
│         ┌─────────────────────────────────────┐                 │
│         │            Storage                   │                 │
│         │  ┌─────────┐ ┌─────────┐ ┌────────┐│                 │
│         │  │ Short-  │ │ Online  │ │Archival││                 │
│         │  │  term   │ │         │ │        ││                 │
│         │  └─────────┘ └─────────┘ └────────┘│                 │
│         └─────────────────────────────────────┘                 │
│                            │                                     │
│                            ▼                                     │
│                   ┌─────────────┐                                │
│                   │  Network    │                                │
│                   └─────────────┘                                │
└─────────────────────────────────────────────────────────────────┘
```

### Component Details

| Component | Function | Examples |
|-----------|----------|----------|
| **Image Sensors** | Convert optical energy to electrical signals | CCD, CMOS sensors |
| **Specialized Hardware** | Perform specific operations at high speed | Digitizers, frame grabbers, ALUs |
| **Computer** | General-purpose processing | PC, workstation, embedded systems |
| **Software** | Implement algorithms | MATLAB, OpenCV, custom code |
| **Storage** | Store images and data | RAM, HDD, SSD, optical media |
| **Display** | Visualize images | LCD monitors, printers |
| **Network** | Transmit images | LAN, Internet, dedicated links |

### Storage Hierarchy

| Type | Purpose | Speed | Capacity | Examples |
|------|---------|-------|----------|----------|
| **Short-term** | Frame buffer, immediate processing | Very Fast | Limited | Video RAM |
| **Online** | Frequently accessed data | Fast | Medium | SSD, HDD |
| **Archival** | Long-term storage | Slow | Large | Tape, Optical discs, Cloud |

---

# Chapter 2: Digital Image Fundamentals

## 2.1 Elements of Visual Perception

### Structure of the Human Eye

```
                    CROSS-SECTION OF HUMAN EYE

                         Vitreous humor
                              │
    Light ──────▶  ┌─────────┼─────────┐
                   │    ┌────┴────┐    │
              Cornea    │         │    Retina
                   │    │  Lens   │    │
                   │    │         │    │◄── Fovea (center)
                   │    └────┬────┘    │
                   │         │         │
                   │      Iris/Pupil   │
                   │         │         │
                   └─────────┼─────────┘
                             │
                        Optic Nerve
                             │
                             ▼
                          Brain
```

### Eye Components and Functions

| Component | Function |
|-----------|----------|
| **Cornea** | Outer transparent membrane; provides most of the eye's optical power |
| **Sclera** | White outer covering (protective) |
| **Choroid** | Contains blood vessels; provides nutrients |
| **Iris** | Colored part; controls pupil size |
| **Pupil** | Opening in iris; controls amount of light entering |
| **Lens** | Focuses light onto retina; adjustable focal length |
| **Retina** | Contains photoreceptors; converts light to neural signals |
| **Fovea** | Central pit in retina; highest visual acuity |
| **Optic Nerve** | Transmits signals to brain |

### Photoreceptors: Rods and Cones

| Property | Cones | Rods |
|----------|-------|------|
| **Number** | 6-7 million | 75-150 million |
| **Location** | Concentrated in fovea | Distributed throughout retina |
| **Absent from** | Periphery of retina | Center of fovea |
| **Function** | Color vision, high acuity | Night vision, peripheral vision |
| **Light Sensitivity** | Low (photopic) | High (scotopic) |
| **Color Perception** | Yes (3 types: R, G, B) | No (monochromatic) |
| **Resolution** | High | Low |

### Key Visual Parameters

**1. Focal Length of Eye:** Approximately 17 mm (14-17 mm range)

**2. Fovea Dimensions:** Approximately 1.5 mm × 1.5 mm

**3. Cone Density in Fovea:** ~150,000 cones/mm²

### Brightness Adaptation

The human visual system can adapt to an enormous range of light intensities:

```
Intensity Scale (log scale):
│
│  ←── Scotopic (rod) vision ──→│←── Photopic (cone) vision ──→
│                               │
10⁻⁶ ────────────────────────── 10⁰ ────────────────────────── 10⁶
    Starlight        Moonlight      Indoor      Sunlight    Glare
```

**Key Facts:**
- Total adaptation range: ~10¹⁰ (10 billion to 1)
- Simultaneous discrimination: ~10² levels at any adaptation level
- Subjective brightness is logarithmic function of intensity

### Weber Ratio and Just Noticeable Difference (JND)

**Weber's Law:**
```
ΔI_c / I ≈ constant (approximately 0.02 at moderate intensities)
```

Where:
- ΔI_c = Just noticeable increment in intensity (Weber fraction)
- I = Background intensity

**Interpretation:** At moderate light levels, the eye can detect about 2% change in intensity.

**Graph of Weber Ratio:**

```
ΔI_c/I
  │
  │
0.1├────╮
  │     ╰──────────────────────────────────────
  │                  ≈ 0.02
  │
0.0├─────────────────────────────────────────▶ log(I)
        Low              Moderate           High
     Intensity          Intensity        Intensity
```

### Important Visual Phenomena

#### 1. Mach Bands

**Definition:** The apparent presence of bright or dark bands near intensity transitions that do not actually exist in the image.

```
Actual Intensity Profile:          Perceived Intensity:
        │                                  │
   High ├────────┐                    High ├────────╮ Bright band
        │        │                         │        │
        │        │                         │        │
   Low  │        └────────            Low  │        ╰──────── Dark band
        └─────────────────▶               └─────────────────▶
              Position                          Position
```

**Cause:** Lateral inhibition in the retina - neurons inhibit neighboring neurons.

**Significance:** Shows that what we perceive is not always what is physically present.

#### 2. Simultaneous Contrast

**Definition:** The phenomenon where the perceived brightness of a region depends on the intensity of surrounding regions.

```
┌───────────────────┬───────────────────┐
│                   │                   │
│    Dark Gray      │    Light Gray     │
│   Background      │   Background      │
│                   │                   │
│      ┌───┐        │      ┌───┐        │
│      │ A │        │      │ B │        │
│      └───┘        │      └───┘        │
│                   │                   │
└───────────────────┴───────────────────┘

Squares A and B have IDENTICAL intensity values,
but A appears lighter than B due to contrast with backgrounds.
```

**Implication:** Absolute intensity judgments are unreliable; the visual system responds to relative intensities.

#### 3. Optical Illusions

The visual system can be deceived by:
- Geometric illusions (size, length, angle misperception)
- Brightness illusions (Mach bands, simultaneous contrast)
- Motion illusions
- Color illusions

---

## 2.2 Light and the Electromagnetic Spectrum

### The Electromagnetic Spectrum

```
          ELECTROMAGNETIC SPECTRUM

Wavelength:  10⁻¹² m                                    10³ m
             │                                           │
             ▼                                           ▼
┌────────┬────────┬────────┬────────┬────────┬────────┬────────┐
│ Gamma  │ X-rays │   UV   │Visible │   IR   │Micro-  │ Radio  │
│ Rays   │        │        │ Light  │        │ wave   │ Waves  │
└────────┴────────┴────────┴────────┴────────┴────────┴────────┘
             │                 │
             │    ┌────────────┴────────────┐
             │    │     VISIBLE SPECTRUM     │
             │    │                          │
             │    │  400nm ──────────▶ 700nm │
             │    │   V  B  G  Y  O  R       │
             │    │   │  │  │  │  │  │       │
             │    │   ▼  ▼  ▼  ▼  ▼  ▼       │
             │    └────────────────────────────┘
```

### Fundamental Relationship

```
λ = c / ν

Where:
λ = wavelength (meters)
c = speed of light in vacuum ≈ 3 × 10⁸ m/s
ν = frequency (Hz or cycles/second)
```

**Also:**
```
E = h × ν = h × c / λ

Where:
E = energy of a photon
h = Planck's constant ≈ 6.626 × 10⁻³⁴ J·s
```

### Visible Light Spectrum Details

| Color | Wavelength Range (nm) | Frequency Range (THz) |
|-------|----------------------|----------------------|
| Violet | 380-450 | 668-789 |
| Blue | 450-490 | 612-668 |
| Green | 490-560 | 536-612 |
| Yellow | 560-590 | 508-536 |
| Orange | 590-630 | 476-508 |
| Red | 630-700 | 428-476 |

### Light Characteristics

#### Monochromatic (Achromatic) Light
- Single wavelength
- Described only by **intensity** (gray level)
- Range: black (no intensity) to white (maximum intensity)

#### Chromatic Light
- Multiple wavelengths or band of wavelengths
- Described by three quantities:
  1. **Radiance:** Total energy emitted (watts)
  2. **Luminance:** Energy perceived by observer (lumens)
  3. **Brightness:** Subjective perception (achromatic notion of intensity)

### Important Conversions

| Quantity | Symbol | Units |
|----------|--------|-------|
| Wavelength | λ | meters (m), nanometers (nm), micrometers (μm) |
| Frequency | ν | Hertz (Hz), cycles/second |
| Energy | E | Joules (J), electron-volts (eV) |

**Conversion factors:**
- 1 nm = 10⁻⁹ m
- 1 μm = 10⁻⁶ m
- 1 Å (angstrom) = 10⁻¹⁰ m

---

## 2.3 Image Sensing and Acquisition

### Image Formation Model

The intensity of a monochromatic image at any point (x, y) is given by:

```
┌─────────────────────────────────────────────────────────────┐
│                                                              │
│           f(x, y) = i(x, y) × r(x, y)                       │
│                                                              │
│   Where:                                                     │
│   • f(x, y) = Image intensity at point (x, y)               │
│   • i(x, y) = Illumination component (light source)         │
│   • r(x, y) = Reflectance component (object properties)     │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Component Ranges

| Component | Symbol | Range | Physical Meaning |
|-----------|--------|-------|------------------|
| Illumination | i(x, y) | (0, ∞) | Amount of light incident on scene |
| Reflectance | r(x, y) | (0, 1) | Fraction of light reflected by object |
| Image | f(x, y) | (0, ∞) | Resulting intensity |

### Typical Values

**Illumination i(x, y):**
| Condition | Illumination (lm/m²) |
|-----------|---------------------|
| Bright sunny day | ~90,000 |
| Cloudy day | ~10,000 |
| Full moon | ~0.1 |
| Starlight | ~0.001 |
| Overcast night | ~0.0001 |

**Reflectance r(x, y):**
| Surface | Reflectance |
|---------|-------------|
| Black velvet | 0.01 |
| Stainless steel | 0.65 |
| Flat white paint | 0.80 |
| Snow | 0.93 |
| Silver-coated mirror | 0.90-0.95 |

### Image Sensing Geometries

#### 1. Single Sensing Element (Point Sensor)

```
        Light Source
             │
             ▼
        ┌─────────┐
        │ Object  │
        └────┬────┘
             │
             ▼
        ┌─────────┐
        │ Single  │──────▶ Electrical Signal
        │ Sensor  │
        └─────────┘
```

- Used with mechanical scanning
- Example: Microdensitometer for film scanning

#### 2. Line Sensor (1D Array)

```
        ┌───┬───┬───┬───┬───┬───┬───┬───┐
        │ S │ S │ S │ S │ S │ S │ S │ S │  ◀── Linear array of sensors
        └───┴───┴───┴───┴───┴───┴───┴───┘
              │
              ▼
        Motion of object OR sensor creates 2D image
```

- Applications: Flatbed scanners, satellite imaging, industrial inspection
- Requires relative motion between sensor and object

#### 3. Array Sensor (2D Array)

```
        ┌───┬───┬───┬───┬───┐
        │ S │ S │ S │ S │ S │
        ├───┼───┼───┼───┼───┤
        │ S │ S │ S │ S │ S │
        ├───┼───┼───┼───┼───┤
        │ S │ S │ S │ S │ S │
        ├───┼───┼───┼───┼───┤
        │ S │ S │ S │ S │ S │
        └───┴───┴───┴───┴───┘

        Entire 2D image captured simultaneously
```

- Most common configuration
- Types: CCD (Charge-Coupled Device), CMOS (Complementary Metal-Oxide Semiconductor)
- Applications: Digital cameras, webcams, medical imaging

### Image Acquisition Process

```
┌──────────┐    ┌───────────┐    ┌───────────┐    ┌──────────┐
│  Scene   │───▶│  Optical  │───▶│  Sensor   │───▶│ Digital  │
│          │    │  System   │    │  Array    │    │  Image   │
│          │    │  (Lens)   │    │           │    │          │
└──────────┘    └───────────┘    └───────────┘    └──────────┘
     │               │                │                │
     │               │                │                │
  Physical       Focuses          Converts         Discrete
   World         light           light to          array of
                                electrical        numbers
                                 signals
```

---

## 2.4 Image Sampling and Quantization

### The Digitization Process

Converting a continuous image to digital form requires two processes:

```
┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
│   Continuous    │         │   Continuous    │         │    Digital      │
│     Image       │──────▶  │     Image       │──────▶  │     Image       │
│    f(x, y)      │ Sampling│  (Discrete x,y) │Quantize │  (Discrete all) │
└─────────────────┘         └─────────────────┘         └─────────────────┘

     SAMPLING: Discretize spatial coordinates (x, y)
     QUANTIZATION: Discretize intensity values
```

### Sampling

**Definition:** The process of converting continuous spatial coordinates into discrete coordinates.

```
Continuous signal           Sampled signal
      │                          │
      │    ╭─╮                   │    •
      │   ╱   ╲                  │    •  •
      │  ╱     ╲                 │   •    •
      │ ╱       ╲                │  •      •
      │╱         ╲               │ •        •
      └───────────▶              └───────────▶
          x                          x

  Continuous in x              Discrete samples at
                               regular intervals
```

**Sampling Rate:** Number of samples per unit distance

### Quantization

**Definition:** The process of converting continuous intensity values into discrete values.

```
Continuous intensity        Quantized intensity
      │                          │
      │    ╭─────────            │    ┌─────────
      │   ╱                      │    │
      │  ╱                       │  ──┤
      │ ╱                        │    │
      │╱                         │────┤
      └───────────▶              └───────────▶
          f                          f

  Continuous amplitude       Discrete levels (e.g., 0-255)
```

**Number of levels:** L = 2^k, where k = bits per pixel

### Digital Image Representation

An image sampled into M rows and N columns, with L intensity levels:

```
         Column (y)
         0    1    2   ...  N-1
      ┌─────┬─────┬─────┬─────┬─────┐
    0 │f(0,0)│f(0,1)│f(0,2)│ ... │f(0,N-1)│
      ├─────┼─────┼─────┼─────┼─────┤
Row 1 │f(1,0)│f(1,1)│f(1,2)│ ... │f(1,N-1)│
(x)   ├─────┼─────┼─────┼─────┼─────┤
    2 │f(2,0)│f(2,1)│f(2,2)│ ... │f(2,N-1)│
      ├─────┼─────┼─────┼─────┼─────┤
   ...│ ... │ ... │ ... │ ... │ ... │
      ├─────┼─────┼─────┼─────┼─────┤
  M-1 │f(M-1,0)│f(M-1,1)│...│...│f(M-1,N-1)│
      └─────┴─────┴─────┴─────┴─────┘
```

**Matrix Notation:**
```
        ┌                                        ┐
        │ f(0,0)    f(0,1)    ...    f(0,N-1)   │
        │ f(1,0)    f(1,1)    ...    f(1,N-1)   │
f(x,y) =│   ⋮         ⋮       ⋱        ⋮        │
        │ f(M-1,0)  f(M-1,1)  ...  f(M-1,N-1)  │
        └                                        ┘
```

### Storage Requirements

```
┌─────────────────────────────────────────────────────────────┐
│                                                              │
│              b = M × N × k   (bits)                         │
│                                                              │
│   Where:                                                     │
│   • M = number of rows                                       │
│   • N = number of columns                                    │
│   • k = bits per pixel                                       │
│   • L = 2^k = number of intensity levels                    │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

**Example Calculations:**

| Image Size | Bits/Pixel | Gray Levels | Storage |
|------------|------------|-------------|---------|
| 256 × 256 | 8 | 256 | 512 KB |
| 512 × 512 | 8 | 256 | 2 MB |
| 1024 × 1024 | 8 | 256 | 8 MB |
| 1024 × 1024 | 24 (color) | 16.7M | 24 MB |
| 1920 × 1080 | 24 (color) | 16.7M | 47.5 MB |

### Spatial Resolution

**Definition:** The smallest discernible detail in an image.

**Measures:**
1. **Line pairs per mm (lp/mm):** Number of distinguishable line pairs per millimeter
2. **Dots per inch (DPI):** Number of dots per inch (for printing)
3. **Pixels per inch (PPI):** Number of pixels per inch (for displays)

**Relationship:**
```
1 line pair = 2 pixels (one dark + one light)

lp/mm = pixels / (2 × distance in mm)

DPI = pixels / distance in inches

1 inch = 25.4 mm
```

### Intensity (Gray-Level) Resolution

**Definition:** The smallest discernible change in intensity.

| Bits (k) | Levels (L = 2^k) | Intensity Range |
|----------|------------------|-----------------|
| 1 | 2 | Binary (black/white) |
| 2 | 4 | 0, 85, 170, 255 |
| 4 | 16 | 0, 17, 34, ..., 255 |
| 8 | 256 | 0, 1, 2, ..., 255 |
| 12 | 4096 | Medical imaging |
| 16 | 65536 | High dynamic range |

### Nyquist Sampling Theorem

```
┌─────────────────────────────────────────────────────────────┐
│                                                              │
│           f_sampling ≥ 2 × f_max                            │
│                                                              │
│   To accurately reconstruct a signal, the sampling          │
│   frequency must be at least twice the highest              │
│   frequency component in the signal.                        │
│                                                              │
│   Nyquist frequency = f_max                                 │
│   Nyquist rate = 2 × f_max                                  │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Aliasing

**Definition:** Artifacts that occur when sampling frequency is too low.

```
Original signal:           Undersampled (aliased):
      │    ╭─╮ ╭─╮              │
      │   ╱ ╲╱ ╲              │    •     •
      │  ╱     ╲              │     •   •
      │ ╱       ╲             │      • •
      │╱         ╲            │       •
      └───────────▶           └───────────▶

High frequency appears as    The reconstructed signal
different (lower) frequency  has wrong frequency
```

**Prevention:**
1. Sample at or above Nyquist rate
2. Use anti-aliasing filter before sampling

### False Contouring

**Definition:** Artificial edges that appear in smoothly varying regions due to insufficient gray levels.

```
Sufficient levels:          Insufficient levels:
      │                          │
      │   ╱                      │   ┌──┐
      │  ╱                       │   │  │
      │ ╱                        │ ──┤  └──┐
      │╱                         │   │     │
      └───────────▶              └───────────▶

  Smooth gradient            Step-like appearance
                             (false contours)
```

**When it occurs:**
- Low k (few bits per pixel)
- Smooth gradient regions
- Large uniform areas

### Interpolation (for Zooming/Resizing)

#### 1. Nearest Neighbor Interpolation

```
Assigns the intensity of the nearest pixel

Original 2×2:        Zoomed 4×4 (Nearest):
┌───┬───┐           ┌───┬───┬───┬───┐
│ A │ B │           │ A │ A │ B │ B │
├───┼───┤    ──▶    ├───┼───┼───┼───┤
│ C │ D │           │ A │ A │ B │ B │
└───┴───┘           ├───┼───┼───┼───┤
                    │ C │ C │ D │ D │
                    ├───┼───┼───┼───┤
                    │ C │ C │ D │ D │
                    └───┴───┴───┴───┘
```

- **Pros:** Simple, fast
- **Cons:** Blocky appearance, jagged edges

#### 2. Bilinear Interpolation

Uses weighted average of 4 nearest neighbors:

```
        (x, y)               (x, y+1)
           ┌──────────────────┐
           │                  │
           │     (x', y')     │
           │        ●         │
           │                  │
           └──────────────────┘
        (x+1, y)           (x+1, y+1)
```

```
v(x', y') = (1-a)(1-b)v(x,y) + a(1-b)v(x+1,y)
          + (1-a)b·v(x,y+1) + ab·v(x+1,y+1)

Where: a = fractional part of x'
       b = fractional part of y'
```

- **Pros:** Smoother than nearest neighbor
- **Cons:** Some blurring

#### 3. Bicubic Interpolation

Uses 16 nearest neighbors (4×4 grid):

```
┌───┬───┬───┬───┐
│   │   │   │   │
├───┼───┼───┼───┤
│   │ ● │ ● │   │  ● = 4 nearest neighbors
├───┼───┼───┼───┤      (as in bilinear)
│   │ ● │ ● │   │
├───┼───┼───┼───┤  All 16 cells are used
│   │   │   │   │  in bicubic interpolation
└───┴───┴───┴───┘
```

- Uses cubic polynomials for smooth interpolation
- **Pros:** Highest quality, smooth results
- **Cons:** Most computationally expensive

#### Comparison Table

| Method | Neighbors | Quality | Speed | Best For |
|--------|-----------|---------|-------|----------|
| Nearest | 1 | Low | Fastest | Speed-critical, pixel art |
| Bilinear | 4 | Medium | Medium | General use |
| Bicubic | 16 | High | Slowest | High-quality resizing |

---

## 2.5 Some Basic Relationships Between Pixels

### Pixel Coordinates

A pixel p at coordinates (x, y) has:
- Row index: x
- Column index: y
- Intensity value: f(x, y)

### Neighbors of a Pixel

For a pixel p at (x, y):

#### 4-Neighbors (N₄)

```
          (x-1, y)
             │
             ▼
        ┌────────┐
        │   N    │
(x, y-1)│ W  p  E │(x, y+1)
        │   S    │
        └────────┘
             │
             ▼
          (x+1, y)

N₄(p) = {(x-1,y), (x+1,y), (x,y-1), (x,y+1)}
```

The 4-neighbors share an **edge** with p (horizontal or vertical neighbors).

#### Diagonal Neighbors (N_D)

```
        (x-1, y-1)     (x-1, y+1)
              ╲           ╱
               ╲         ╱
                ┌───────┐
                │       │
                │   p   │
                │       │
                └───────┘
               ╱         ╲
              ╱           ╲
        (x+1, y-1)     (x+1, y+1)

N_D(p) = {(x-1,y-1), (x-1,y+1), (x+1,y-1), (x+1,y+1)}
```

The diagonal neighbors share a **corner** with p.

#### 8-Neighbors (N₈)

```
        ┌─────┬─────┬─────┐
        │NW   │  N  │  NE │
        │(-1,-1)│(-1,0)│(-1,+1)│
        ├─────┼─────┼─────┤
        │ W   │  p  │  E  │
        │(0,-1)│(0,0)│(0,+1)│
        ├─────┼─────┼─────┤
        │SW   │  S  │  SE │
        │(+1,-1)│(+1,0)│(+1,+1)│
        └─────┴─────┴─────┘

N₈(p) = N₄(p) ∪ N_D(p)
```

### Adjacency

Let V be the set of intensity values used to define adjacency.

#### 4-Adjacency
Two pixels p and q with values from V are **4-adjacent** if q is in N₄(p).

```
Example with V = {1}:
        ┌───┬───┬───┐
        │ 0 │ 1 │ 0 │
        ├───┼───┼───┤        Pixels at (0,1) and (1,1)
        │ 0 │ 1 │ 0 │   ──▶  are 4-adjacent because
        ├───┼───┼───┤        they share a vertical edge
        │ 0 │ 0 │ 0 │        and both have value in V
        └───┴───┴───┘
```

#### 8-Adjacency
Two pixels p and q with values from V are **8-adjacent** if q is in N₈(p).

```
Example with V = {1}:
        ┌───┬───┬───┐
        │ 1 │ 0 │ 0 │
        ├───┼───┼───┤        Pixels at (0,0) and (1,1)
        │ 0 │ 1 │ 0 │   ──▶  are 8-adjacent because
        ├───┼───┼───┤        they share a corner
        │ 0 │ 0 │ 0 │        and both have value in V
        └───┴───┴───┘
```

#### m-Adjacency (Mixed Adjacency)

Two pixels p and q with values from V are **m-adjacent** if:
1. q is in N₄(p), OR
2. q is in N_D(p) AND N₄(p) ∩ N₄(q) has no pixels with values from V

```
Purpose: Eliminate ambiguity in 8-adjacency

Example showing why m-adjacency is needed:

With V = {1}:
        ┌───┬───┐
        │ 1 │ 1 │
        ├───┼───┤
        │ 1 │ 1 │
        └───┴───┘

8-adjacency: Multiple paths from (0,0) to (1,1)
             Path 1: (0,0)→(0,1)→(1,1)
             Path 2: (0,0)→(1,0)→(1,1)
             Path 3: (0,0)→(1,1) [diagonal]

m-adjacency: Only allows:
             Path 1: (0,0)→(0,1)→(1,1)
             Path 2: (0,0)→(1,0)→(1,1)
             (diagonal blocked because 4-neighbors exist)
```

### Connectivity

**Definition:** Two pixels are **connected** if there exists a path between them consisting of adjacent pixels.

**Types:**
- **4-connected:** Path uses only 4-adjacency
- **8-connected:** Path uses 8-adjacency
- **m-connected:** Path uses m-adjacency

### Regions and Boundaries

**Region:** A connected set of pixels.

```
        ┌───┬───┬───┬───┬───┐
        │ 0 │ 0 │ 0 │ 0 │ 0 │
        ├───┼───┼───┼───┼───┤
        │ 0 │ 1 │ 1 │ 1 │ 0 │     Region R (shaded)
        ├───┼───┼───┼───┼───┤     is the set of all
        │ 0 │ 1 │ 1 │ 1 │ 0 │     connected 1-pixels
        ├───┼───┼───┼───┼───┤
        │ 0 │ 0 │ 0 │ 0 │ 0 │
        └───┴───┴───┴───┴───┘
```

**Boundary (Border):** The set of pixels in a region that have at least one neighbor not in the region.

```
        ┌───┬───┬───┬───┬───┐
        │ 0 │ 0 │ 0 │ 0 │ 0 │
        ├───┼───┼───┼───┼───┤
        │ 0 │ B │ B │ B │ 0 │     B = Boundary pixels
        ├───┼───┼───┼───┼───┤     I = Interior pixels
        │ 0 │ B │ I │ B │ 0 │     (for a larger region)
        ├───┼───┼───┼───┼───┤
        │ 0 │ B │ B │ B │ 0 │
        ├───┼───┼───┼───┼───┤
        │ 0 │ 0 │ 0 │ 0 │ 0 │
        └───┴───┴───┴───┴───┘
```

### Distance Measures

For pixels p at (x, y) and q at (s, t):

#### Euclidean Distance (D_e)

```
D_e(p, q) = √[(x - s)² + (y - t)²]
```

- Actual geometric distance
- Irrational values possible

#### City-Block Distance (D₄)

```
D₄(p, q) = |x - s| + |y - t|
```

- Also called Manhattan distance or L₁ norm
- Distance measured along axes only
- Integer values

#### Chessboard Distance (D₈)

```
D₈(p, q) = max(|x - s|, |y - t|)
```

- Also called Chebyshev distance or L∞ norm
- Maximum of horizontal and vertical distances
- Integer values

#### Visual Comparison

```
Distance from center pixel (shown as numbers):

Euclidean:              City-Block (D₄):         Chessboard (D₈):
┌─────┬─────┬─────┐    ┌─────┬─────┬─────┐    ┌─────┬─────┬─────┐
│√2≈1.4│  1  │√2≈1.4│    │  2  │  1  │  2  │    │  1  │  1  │  1  │
├─────┼─────┼─────┤    ├─────┼─────┼─────┤    ├─────┼─────┼─────┤
│  1  │  0  │  1  │    │  1  │  0  │  1  │    │  1  │  0  │  1  │
├─────┼─────┼─────┤    ├─────┼─────┼─────┤    ├─────┼─────┼─────┤
│√2≈1.4│  1  │√2≈1.4│    │  2  │  1  │  2  │    │  1  │  1  │  1  │
└─────┴─────┴─────┘    └─────┴─────┴─────┘    └─────┴─────┴─────┘
```

#### Properties

| Property | D_e | D₄ | D₈ |
|----------|-----|-----|-----|
| Integer values | No | Yes | Yes |
| Computation | Slow (√) | Fast | Fast |
| Unit circle shape | Circle | Diamond | Square |
| 4-connected path | No | Yes | No |
| 8-connected path | No | No | Yes |

---

## 2.6 Introduction to Mathematical Tools

### Linear vs. Nonlinear Operations

#### Linear Operation Definition

An operator H is **linear** if and only if:

```
H[a₁f₁(x,y) + a₂f₂(x,y)] = a₁H[f₁(x,y)] + a₂H[f₂(x,y)]
```

This can be separated into two properties:

1. **Additivity:** H[f₁ + f₂] = H[f₁] + H[f₂]
2. **Homogeneity:** H[af] = aH[f]

#### Examples

| Operation | Linear? | Reason |
|-----------|---------|--------|
| Addition (f + g) | Yes | Satisfies both properties |
| Subtraction (f - g) | Yes | Satisfies both properties |
| Scaling (a × f) | Yes | Satisfies both properties |
| Multiplication (f × g) | No | H[2f] = 2f × g ≠ 2(f × g) |
| Division (f / g) | No | Similar to multiplication |
| Average | Yes | Sum divided by constant |
| Median | No | Order-dependent |
| Maximum/Minimum | No | Not additive |

### Arithmetic Operations on Images

#### Image Addition

```
g(x, y) = f(x, y) + h(x, y)
```

**Application: Noise Reduction by Averaging**

If we have K noisy images of the same scene:
```
gᵢ(x, y) = f(x, y) + ηᵢ(x, y)

Where: f(x, y) = true image
       ηᵢ(x, y) = noise (random, zero mean)
```

**Averaging:**
```
ḡ(x, y) = (1/K) × Σᵢ₌₁ᴷ gᵢ(x, y)
```

**Result:**
```
E[ḡ(x, y)] = f(x, y)           (expected value equals true image)

σ²_ḡ(x,y) = σ²_η(x,y) / K      (variance reduced by factor K)

SNR improvement = √K            (signal-to-noise ratio)
```

**Example:**
- Original noise σ = 20
- After averaging 16 images: σ_avg = 20/√16 = 20/4 = 5
- SNR improved by factor of 4

#### Image Subtraction

```
g(x, y) = f(x, y) - h(x, y)
```

**Applications:**
1. **Change detection:** Comparing images taken at different times
2. **Background removal:** Subtracting a reference background
3. **Motion detection:** Difference between consecutive frames
4. **Digital subtraction angiography:** Medical imaging of blood vessels

**Example: Mask Mode Radiography**
```
g(x, y) = f(x, y) - h(x, y)

Where: f(x, y) = image after contrast injection
       h(x, y) = mask image (before injection)
       g(x, y) = enhanced blood vessel image
```

#### Image Multiplication

```
g(x, y) = f(x, y) × h(x, y)    (element-wise)
```

**Applications:**
1. **Shading correction:** Correcting non-uniform illumination
2. **Masking (ROI operations):** Selecting regions of interest

**Shading Correction:**
```
Observed: g(x, y) = f(x, y) × h(x, y)   (h = shading pattern)

Corrected: f(x, y) = g(x, y) / h(x, y)  (divide by shading)
```

**Masking:**
```
Result: g(x, y) = f(x, y) × m(x, y)

Where: m(x, y) = 1 in region of interest
       m(x, y) = 0 elsewhere
```

#### Image Division

```
g(x, y) = f(x, y) / h(x, y)    (element-wise)
```

**Applications:**
1. Shading correction (as above)
2. Ratio imaging

**Note:** Add small constant to avoid division by zero.

### Set Operations

#### Basic Set Theory

| Notation | Meaning |
|----------|---------|
| a ∈ A | a is an element of set A |
| a ∉ A | a is not an element of A |
| ∅ | Empty (null) set |
| Ω | Sample space (universe) |
| A ⊆ B | A is a subset of B |

#### Set Operations

```
UNION:        A ∪ B = {x | x ∈ A OR x ∈ B}

INTERSECTION: A ∩ B = {x | x ∈ A AND x ∈ B}

COMPLEMENT:   Aᶜ = {x | x ∉ A, x ∈ Ω}

DIFFERENCE:   A - B = A ∩ Bᶜ = {x | x ∈ A AND x ∉ B}
```

#### Venn Diagrams

```
UNION (A ∪ B):           INTERSECTION (A ∩ B):    COMPLEMENT (Aᶜ):
    ┌───────────┐            ┌───────────┐           ┌───────────┐
    │  ╭───────╮│            │  ╭───────╮│           │███████████│
    │ ╱░░░░░░░░╲│            │ ╱       ╱╲│           │███╭───╮███│
    │╱░░░░░░░░░░╲            │╱       ╱██╲│          │███│   │███│
    │░░░A░░░B░░░│            │   A   │██│B│          │███│ A │███│
    │╲░░░░░░░░░╱│            │╲      ╲██╱│           │███╰───╯███│
    │ ╲░░░░░░░╱ │            │ ╲      ╲╱ │           │███████████│
    │  ╰───────╯ │            │  ╰───────╯│           └───────────┘
    └───────────┘            └───────────┘
    (shaded area)            (shaded area)           (shaded area)


DIFFERENCE (A - B):      DIFFERENCE (B - A):
    ┌───────────┐            ┌───────────┐
    │  ╭───────╮│            │  ╭───────╮│
    │ ╱███    ╱╲│            │ ╱    ███╱╲│
    │╱███    ╱  ╲            │╱    ███╱  ╲
    │███A   │   B│           │   A │███B │
    │╲███    ╲  ╱│            │╲   ███╲  ╱│
    │ ╲███    ╲╱ │            │ ╲   ███╲╱ │
    │  ╰───────╯ │            │  ╰───────╯│
    └───────────┘            └───────────┘
```

#### Important Set Properties

| Property | Expression |
|----------|------------|
| Commutative | A ∪ B = B ∪ A; A ∩ B = B ∩ A |
| Associative | (A ∪ B) ∪ C = A ∪ (B ∪ C) |
| Distributive | A ∩ (B ∪ C) = (A ∩ B) ∪ (A ∩ C) |
| Identity | A ∪ ∅ = A; A ∩ Ω = A |
| Complement | A ∪ Aᶜ = Ω; A ∩ Aᶜ = ∅ |
| **DeMorgan's** | **(A ∪ B)ᶜ = Aᶜ ∩ Bᶜ** |
| **DeMorgan's** | **(A ∩ B)ᶜ = Aᶜ ∪ Bᶜ** |

### Logical Operations

#### Truth Table

| a | b | a AND b | a OR b | NOT a | a XOR b |
|---|---|---------|--------|-------|---------|
| 0 | 0 | 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 | 0 | 0 |

#### Application to Binary Images

```
Image A:          Image B:          A AND B:
┌───┬───┬───┐    ┌───┬───┬───┐    ┌───┬───┬───┐
│ 1 │ 1 │ 0 │    │ 1 │ 0 │ 0 │    │ 1 │ 0 │ 0 │
├───┼───┼───┤    ├───┼───┼───┤    ├───┼───┼───┤
│ 1 │ 1 │ 0 │ AND│ 1 │ 1 │ 1 │ =  │ 1 │ 1 │ 0 │
├───┼───┼───┤    ├───┼───┼───┤    ├───┼───┼───┤
│ 0 │ 0 │ 0 │    │ 0 │ 1 │ 1 │    │ 0 │ 0 │ 0 │
└───┴───┴───┘    └───┴───┴───┘    └───┴───┴───┘

A OR B:           NOT A:            A XOR B:
┌───┬───┬───┐    ┌───┬───┬───┐    ┌───┬───┬───┐
│ 1 │ 1 │ 0 │    │ 0 │ 0 │ 1 │    │ 0 │ 1 │ 0 │
├───┼───┼───┤    ├───┼───┼───┤    ├───┼───┼───┤
│ 1 │ 1 │ 1 │    │ 0 │ 0 │ 1 │    │ 0 │ 0 │ 1 │
├───┼───┼───┤    ├───┼───┼───┤    ├───┼───┼───┤
│ 0 │ 1 │ 1 │    │ 1 │ 1 │ 1 │    │ 0 │ 1 │ 1 │
└───┴───┴───┘    └───┴───┴───┘    └───┴───┴───┘
```

### Geometric Transformations

#### Affine Transformations

Affine transformations preserve:
- Points
- Straight lines
- Planes
- Parallelism

Using **homogeneous coordinates**:

```
┌───┐   ┌─────────────────┐   ┌───┐
│ x'│   │ a₁₁  a₁₂  a₁₃  │   │ x │
│ y'│ = │ a₂₁  a₂₂  a₂₃  │ × │ y │
│ 1 │   │  0    0    1   │   │ 1 │
└───┘   └─────────────────┘   └───┘
```

#### Transformation Matrices

**Identity:**
```
┌─────────┐
│ 1  0  0 │
│ 0  1  0 │
│ 0  0  1 │
└─────────┘

x' = x, y' = y (no change)
```

**Scaling:**
```
┌─────────┐
│ sₓ 0  0 │
│ 0  sᵧ 0 │
│ 0  0  1 │
└─────────┘

x' = sₓ·x, y' = sᵧ·y

sₓ, sᵧ > 1: Enlargement
sₓ, sᵧ < 1: Shrinking
```

**Translation:**
```
┌─────────┐
│ 1  0  tₓ│
│ 0  1  tᵧ│
│ 0  0  1 │
└─────────┘

x' = x + tₓ, y' = y + tᵧ
```

**Rotation (counterclockwise by θ):**
```
┌──────────────────┐
│ cosθ  -sinθ   0  │
│ sinθ   cosθ   0  │
│  0      0     1  │
└──────────────────┘

x' = x·cosθ - y·sinθ
y' = x·sinθ + y·cosθ
```

**Horizontal Shear:**
```
┌─────────┐
│ 1  shₓ 0│
│ 0   1  0│
│ 0   0  1│
└─────────┘

x' = x + shₓ·y, y' = y
```

**Vertical Shear:**
```
┌─────────┐
│ 1   0  0│
│shᵧ  1  0│
│ 0   0  1│
└─────────┘

x' = x, y' = shᵧ·x + y
```

#### Composite Transformations

Multiple transformations can be combined by matrix multiplication:

```
T_combined = T_n × T_{n-1} × ... × T_2 × T_1
```

**Important:** Order matters! Matrix multiplication is not commutative.

**Example: Scale then Translate**
```
T = Translation × Scaling

┌─────────┐   ┌─────────┐   ┌──────────┐
│ 1  0  tₓ│   │ sₓ 0  0 │   │ sₓ 0  tₓ │
│ 0  1  tᵧ│ × │ 0  sᵧ 0 │ = │ 0  sᵧ tᵧ │
│ 0  0  1 │   │ 0  0  1 │   │ 0  0  1  │
└─────────┘   └─────────┘   └──────────┘
```

#### Inverse Transformations

For inverse mapping (output to input):

```
[x, y, 1]ᵀ = A⁻¹ × [x', y', 1]ᵀ
```

**Inverse Matrices:**

| Transform | Inverse |
|-----------|---------|
| Scale(sₓ, sᵧ) | Scale(1/sₓ, 1/sᵧ) |
| Translate(tₓ, tᵧ) | Translate(-tₓ, -tᵧ) |
| Rotate(θ) | Rotate(-θ) |

### Image Transforms

#### 2-D Discrete Fourier Transform (DFT)

**Forward Transform:**
```
F(u, v) = Σₓ₌₀^{M-1} Σᵧ₌₀^{N-1} f(x, y) × e^{-j2π(ux/M + vy/N)}
```

**Inverse Transform:**
```
f(x, y) = (1/MN) Σᵤ₌₀^{M-1} Σᵥ₌₀^{N-1} F(u, v) × e^{j2π(ux/M + vy/N)}
```

Where: j = √(-1)

**Key Properties:**
- Separable: Can compute as two 1-D transforms
- Symmetric: Forward and inverse have similar form
- Converts spatial domain to frequency domain

---

# Formula Sheet

## Quick Reference - All Important Formulas

### Electromagnetic Spectrum
```
λ = c/ν          where c = 3×10⁸ m/s
E = hν = hc/λ    where h = 6.626×10⁻³⁴ J·s
```

### Image Formation
```
f(x,y) = i(x,y) × r(x,y)
```

### Storage
```
b = M × N × k bits
L = 2^k levels
Range: [0, L-1]
```

### Resolution
```
lp/mm = pixels / (2 × mm)
DPI = pixels / inches
1 inch = 25.4 mm
```

### Sampling
```
f_sampling ≥ 2 × f_max (Nyquist)
```

### Distance Measures
```
D_e(p,q) = √[(x-s)² + (y-t)²]
D_4(p,q) = |x-s| + |y-t|
D_8(p,q) = max(|x-s|, |y-t|)
```

### Noise Reduction
```
ḡ = (1/K) Σgᵢ
σ²_avg = σ²/K
SNR improvement = √K
```

### Transformations
```
[x']   [a₁₁ a₁₂ a₁₃] [x]
[y'] = [a₂₁ a₂₂ a₂₃] [y]
[1 ]   [0   0   1  ] [1]
```

### Weber Ratio
```
ΔI_c/I ≈ 0.02
```

### DeMorgan's Laws
```
(A ∪ B)ᶜ = Aᶜ ∩ Bᶜ
(A ∩ B)ᶜ = Aᶜ ∪ Bᶜ
```

---

# Practice Problems with Solutions

## Problem Set 1: Basic Calculations

### Problem 1.1: Wavelength Calculation
**Question:** Calculate the wavelength of radio waves with frequency 100 MHz.

**Solution:**
```
λ = c/ν
λ = (3 × 10⁸ m/s) / (100 × 10⁶ Hz)
λ = (3 × 10⁸) / (10⁸)
λ = 3 meters
```

---

### Problem 1.2: Storage Calculation
**Question:** Calculate the storage required for:
(a) A 640×480 grayscale image with 256 levels
(b) A 1920×1080 RGB color image (24 bits per pixel)
(c) A 2-hour movie at 30 fps, 1080p, 24-bit color

**Solution:**
```
(a) k = log₂(256) = 8 bits
    Storage = 640 × 480 × 8 bits = 2,457,600 bits
    = 307,200 bytes = 300 KB

(b) Storage = 1920 × 1080 × 24 bits
    = 49,766,400 bits
    = 6,220,800 bytes ≈ 5.93 MB per frame

(c) Frames = 2 hours × 60 min × 60 sec × 30 fps = 216,000 frames
    Total = 216,000 × 5.93 MB = 1,280,880 MB ≈ 1.22 TB
```

---

### Problem 1.3: Resolution Calculation
**Question:** An image of 4096×4096 pixels must fit in a 10×10 cm area. Calculate:
(a) Resolution in lp/mm
(b) Resolution in DPI

**Solution:**
```
(a) Line pairs = 4096/2 = 2048 lp per direction
    Physical size = 100 mm
    Resolution = 2048/100 = 20.48 lp/mm

(b) 10 cm = 100 mm = 100/25.4 inches ≈ 3.937 inches
    DPI = 4096/3.937 ≈ 1040 DPI
```

---

### Problem 1.4: Distance Calculations
**Question:** Calculate D_e, D_4, and D_8 between p=(2,5) and q=(7,2).

**Solution:**
```
D_e = √[(7-2)² + (2-5)²] = √[25 + 9] = √34 ≈ 5.83

D_4 = |7-2| + |2-5| = 5 + 3 = 8

D_8 = max(|7-2|, |2-5|) = max(5, 3) = 5
```

---

### Problem 1.5: Noise Reduction
**Question:** An image has noise with σ = 30. How many images must be averaged to reduce noise to σ ≤ 6?

**Solution:**
```
σ_avg = σ/√K
6 = 30/√K
√K = 30/6 = 5
K = 25 images
```

---

## Problem Set 2: Geometric Transformations

### Problem 2.1: Composite Transformation
**Question:** Find the composite transformation matrix for:
1. Scale by factor 2 in both directions
2. Rotate by 45°
3. Translate by (10, 5)

**Solution:**
```
Step 1: Scaling matrix
S = [2  0  0]
    [0  2  0]
    [0  0  1]

Step 2: Rotation matrix (45° = π/4, cos45° = sin45° = √2/2 ≈ 0.707)
R = [0.707  -0.707  0]
    [0.707   0.707  0]
    [0       0      1]

Step 3: Translation matrix
T = [1  0  10]
    [0  1   5]
    [0  0   1]

Composite: C = T × R × S (applied right to left)

First: R × S
RS = [0.707  -0.707  0]   [2  0  0]   [1.414  -1.414  0]
     [0.707   0.707  0] × [0  2  0] = [1.414   1.414  0]
     [0       0      1]   [0  0  1]   [0       0      1]

Then: T × RS
C = [1  0  10]   [1.414  -1.414  0]   [1.414  -1.414  10]
    [0  1   5] × [1.414   1.414  0] = [1.414   1.414   5]
    [0  0   1]   [0       0      1]   [0       0       1]
```

---

### Problem 2.2: Point Transformation
**Question:** Apply the following transformations to point P=(4, 3):
(a) Rotation by 90° counterclockwise
(b) Scale by (2, 0.5)
(c) Translation by (-3, 2)

**Solution:**
```
(a) Rotation 90° (cos90°=0, sin90°=1):
    [x']   [0  -1  0]   [4]   [-3]
    [y'] = [1   0  0] × [3] = [4 ]
    [1 ]   [0   0  1]   [1]   [1 ]
    Result: (-3, 4)

(b) Scaling:
    [x']   [2    0   0]   [4]   [8  ]
    [y'] = [0   0.5  0] × [3] = [1.5]
    [1 ]   [0    0   1]   [1]   [1  ]
    Result: (8, 1.5)

(c) Translation:
    [x']   [1  0  -3]   [4]   [1]
    [y'] = [0  1   2] × [3] = [5]
    [1 ]   [0  0   1]   [1]   [1]
    Result: (1, 5)
```

---

## Problem Set 3: Paths and Adjacency

### Problem 3.1: Path Finding
**Question:** Given the following image with V={1,2}, find the shortest 4-path, 8-path, and m-path from p to q.

```
    0   1   2
  ┌───┬───┬───┐
0 │ 2 │ 1 │ 2 │  p = (0,0), q = (2,2)
  ├───┼───┼───┤
1 │ 0 │ 2 │ 0 │
  ├───┼───┼───┤
2 │ 1 │ 0 │ 1 │
  └───┴───┴───┘
```

**Solution:**
```
Valid pixels (values in V={1,2}): (0,0)=2, (0,1)=1, (0,2)=2, (1,1)=2, (2,0)=1, (2,2)=1

4-path: Must use only horizontal/vertical moves
(0,0)→(0,1)→(0,2): Can't continue to (2,2) via 4-adjacency
(0,0)→(0,1)→(1,1): Then stuck (can't reach (2,2))
No 4-path exists from p to q.

8-path: Can use diagonal moves
(0,0)→(1,1)→(2,2): Length = 2

m-path:
(0,0)→(0,1): 4-adjacent (allowed)
(0,1)→(1,1): 4-adjacent (allowed)
But (0,0)→(1,1) diagonal: Check if N₄(0,0)∩N₄(1,1) has values in V
N₄(0,0)={(−1,0),(1,0),(0,−1),(0,1)} → valid: (0,1)=1 ∈ V
So diagonal (0,0)→(1,1) NOT allowed in m-adjacency

m-path: (0,0)→(0,1)→(1,1)→(2,2) [need to check (1,1)→(2,2)]
N₄(1,1)∩N₄(2,2) = {(1,2),(2,1)} → both are 0, not in V
So diagonal (1,1)→(2,2) IS allowed
m-path: (0,0)→(0,1)→(1,1)→(2,2), Length = 3
```

---

## Problem Set 4: Set Operations

### Problem 4.1: Venn Diagram
**Question:** Shade the region representing (A ∪ B) - C

**Solution:**
```
Step 1: A ∪ B (union of A and B)
Step 2: Subtract C from the result

    ┌────────────────────────┐
    │         C              │
    │    ┌─────────┐         │
    │    │░░░░░░░░░│         │
    │  ┌─┴───┐░░░░░│         │
    │  │░░A░░│░░B░░│         │
    │  │░░░░░│░░░░░│         │
    │  └─────┴─────┘         │
    └────────────────────────┘

Shaded region = (A ∪ B) - C
= Parts of A and B that are NOT in C
```

---

### Problem 4.2: DeMorgan's Law Verification
**Question:** Verify using truth tables that (A ∩ B)ᶜ = Aᶜ ∪ Bᶜ

**Solution:**
```
| A | B | A∩B | (A∩B)ᶜ | Aᶜ | Bᶜ | Aᶜ∪Bᶜ |
|---|---|-----|--------|----|----|-------|
| 0 | 0 |  0  |   1    | 1  | 1  |   1   |
| 0 | 1 |  0  |   1    | 1  | 0  |   1   |
| 1 | 0 |  0  |   1    | 0  | 1  |   1   |
| 1 | 1 |  1  |   0    | 0  | 0  |   0   |

Columns (A∩B)ᶜ and Aᶜ∪Bᶜ are identical. ✓
```

---

## Problem Set 5: Transmission and Bandwidth

### Problem 5.1: Transmission Time
**Question:** Calculate time to transmit 50 images of size 800×600, 8 bits/pixel at 5 Mbps. Include 20% overhead.

**Solution:**
```
Data per image = 800 × 600 × 8 = 3,840,000 bits
Total data = 50 × 3,840,000 = 192,000,000 bits
With overhead = 192,000,000 × 1.2 = 230,400,000 bits
Time = 230,400,000 / (5 × 10⁶) = 46.08 seconds
```

---

# Multiple Choice Questions

## Chapter 1 MCQs (25 Questions)

**1.** The first digital images were transmitted using the:
- (a) Wireless telegraph
- (b) Bartlane cable picture transmission system ✓
- (c) Satellite communication
- (d) Fiber optic cable

**2.** CT scanner was invented in the:
- (a) 1950s
- (b) 1960s
- (c) 1970s ✓
- (d) 1980s

**3.** PET imaging uses:
- (a) X-rays
- (b) Ultrasound
- (c) Gamma rays ✓
- (d) Radio waves

**4.** MRI imaging uses:
- (a) X-rays
- (b) Gamma rays
- (c) Infrared
- (d) Radio waves ✓

**5.** Low-level image processing produces:
- (a) Attributes from images
- (b) Images from images ✓
- (c) Understanding from images
- (d) Images from attributes

**6.** Image segmentation is an example of:
- (a) Low-level processing
- (b) Mid-level processing ✓
- (c) High-level processing
- (d) Pre-processing

**7.** Which is NOT a fundamental step in digital image processing?
- (a) Image acquisition
- (b) Image enhancement
- (c) Image printing ✓
- (d) Image segmentation

**8.** The visible light spectrum spans approximately:
- (a) 100-400 nm
- (b) 400-700 nm ✓
- (c) 700-1000 nm
- (d) 1000-1500 nm

**9.** Thermal imaging uses:
- (a) Ultraviolet
- (b) Visible light
- (c) Infrared ✓
- (d) X-rays

**10.** The wavelength of light is related to frequency by:
- (a) λ = c × ν
- (b) λ = c / ν ✓
- (c) λ = c + ν
- (d) λ = c - ν

**11.** Image enhancement is:
- (a) An objective process
- (b) A subjective process ✓
- (c) Always mathematical
- (d) Fully automated

**12.** Image restoration:
- (a) Is subjective
- (b) Uses degradation models ✓
- (c) Always improves aesthetics
- (d) Requires no mathematical model

**13.** The first successful application of digital image processing was:
- (a) Medical imaging
- (b) Newspaper image transmission ✓
- (c) Satellite imaging
- (d) Microscopy

**14.** SAR imaging uses:
- (a) Visible light
- (b) Infrared
- (c) Microwave ✓
- (d) Ultraviolet

**15.** Which component stores images temporarily during processing?
- (a) Archival storage
- (b) Frame buffer ✓
- (c) Hard disk
- (d) Optical disc

**16.** Godfrey Hounsfield is known for inventing:
- (a) MRI
- (b) CT scanner ✓
- (c) X-ray
- (d) Ultrasound

**17.** The knowledge base in image processing:
- (a) Stores images
- (b) Guides processing operations ✓
- (c) Performs filtering
- (d) Displays images

**18.** Which imaging modality does NOT use electromagnetic radiation?
- (a) X-ray
- (b) MRI
- (c) Ultrasound ✓
- (d) Infrared

**19.** Feature extraction belongs to which processing level?
- (a) Low-level
- (b) Mid-level ✓
- (c) High-level
- (d) Pre-processing

**20.** The output of pattern recognition is:
- (a) An image
- (b) Image attributes
- (c) Class labels ✓
- (d) Transformed image

**21.** CCD and CMOS are types of:
- (a) Displays
- (b) Image sensors ✓
- (c) Storage devices
- (d) Processors

**22.** Morphological processing is used for:
- (a) Color correction
- (b) Shape analysis ✓
- (c) Noise reduction
- (d) Compression

**23.** Wavelets are used in:
- (a) Image acquisition
- (b) Multi-resolution processing ✓
- (c) Display
- (d) Networking

**24.** Which has the shortest wavelength?
- (a) Radio waves
- (b) Infrared
- (c) X-rays
- (d) Gamma rays ✓

**25.** Image compression reduces:
- (a) Image quality only
- (b) Storage requirements ✓
- (c) Image dimensions
- (d) Number of colors

---

## Chapter 2 MCQs (50 Questions)

**26.** The fovea is located in the:
- (a) Cornea
- (b) Lens
- (c) Retina ✓
- (d) Iris

**27.** Cones are responsible for:
- (a) Night vision
- (b) Color vision ✓
- (c) Peripheral vision
- (d) All of the above

**28.** The number of cones in the human eye is approximately:
- (a) 6-7 thousand
- (b) 6-7 million ✓
- (c) 75-150 million
- (d) 600-700 million

**29.** Rods are most sensitive to:
- (a) Color
- (b) Fine detail
- (c) Low light levels ✓
- (d) Bright light

**30.** The Weber ratio at moderate intensities is approximately:
- (a) 0.002
- (b) 0.02 ✓
- (c) 0.2
- (d) 2.0

**31.** Mach bands are caused by:
- (a) Camera defects
- (b) Lateral inhibition ✓
- (c) Noise
- (d) Aliasing

**32.** In the image formation model f(x,y) = i(x,y) × r(x,y), r(x,y) represents:
- (a) Illumination
- (b) Reflectance ✓
- (c) Image intensity
- (d) Noise

**33.** The reflectance r(x,y) has values in the range:
- (a) (-∞, ∞)
- (b) (0, ∞)
- (c) (0, 1) ✓
- (d) (0, 255)

**34.** An 8-bit image has how many gray levels?
- (a) 8
- (b) 64
- (c) 128
- (d) 256 ✓

**35.** The storage for a 512×512, 8-bit image is:
- (a) 256 KB ✓
- (b) 512 KB
- (c) 1 MB
- (d) 2 MB

**36.** According to Nyquist theorem, to avoid aliasing:
- (a) f_s = f_max
- (b) f_s ≥ 2×f_max ✓
- (c) f_s ≤ 2×f_max
- (d) f_s = f_max/2

**37.** False contouring is caused by:
- (a) Undersampling
- (b) Insufficient gray levels ✓
- (c) Noise
- (d) Motion blur

**38.** The 4-neighbors of a pixel include:
- (a) Diagonal neighbors
- (b) Horizontal and vertical neighbors ✓
- (c) All 8 surrounding pixels
- (d) Corner neighbors

**39.** How many 8-neighbors does a pixel have?
- (a) 4
- (b) 6
- (c) 8 ✓
- (d) 9

**40.** m-adjacency is used to:
- (a) Increase connectivity
- (b) Eliminate path ambiguity ✓
- (c) Reduce computation
- (d) Improve image quality

**41.** The city-block distance between (0,0) and (3,4) is:
- (a) 5
- (b) 7 ✓
- (c) 4
- (d) 3

**42.** The chessboard distance between (0,0) and (3,4) is:
- (a) 7
- (b) 5
- (c) 4 ✓
- (d) 3

**43.** The Euclidean distance between (0,0) and (3,4) is:
- (a) 7
- (b) 5 ✓
- (c) 4
- (d) 3

**44.** Bilinear interpolation uses how many neighbors?
- (a) 1
- (b) 4 ✓
- (c) 8
- (d) 16

**45.** Bicubic interpolation uses how many neighbors?
- (a) 4
- (b) 8
- (c) 12
- (d) 16 ✓

**46.** Which interpolation method is fastest?
- (a) Nearest neighbor ✓
- (b) Bilinear
- (c) Bicubic
- (d) All are equal

**47.** Which interpolation method produces the highest quality?
- (a) Nearest neighbor
- (b) Bilinear
- (c) Bicubic ✓
- (d) All are equal

**48.** Which operation is LINEAR?
- (a) Image multiplication
- (b) Image division
- (c) Image addition ✓
- (d) Finding median

**49.** Which operation is NONLINEAR?
- (a) Averaging
- (b) Subtraction
- (c) Median filtering ✓
- (d) Scaling

**50.** To reduce noise variance by factor of 9, average:
- (a) 3 images
- (b) 9 images ✓
- (c) 27 images
- (d) 81 images

**51.** The complement of (A ∪ B) equals:
- (a) Aᶜ ∪ Bᶜ
- (b) Aᶜ ∩ Bᶜ ✓
- (c) A ∩ B
- (d) (A ∩ B)ᶜ

**52.** The complement of (A ∩ B) equals:
- (a) Aᶜ ∩ Bᶜ
- (b) Aᶜ ∪ Bᶜ ✓
- (c) A ∪ B
- (d) (A ∪ B)ᶜ

**53.** A - B is equivalent to:
- (a) A ∪ Bᶜ
- (b) A ∩ Bᶜ ✓
- (c) Aᶜ ∩ B
- (d) Aᶜ ∪ B

**54.** In rotation transformation, element a₁₁ equals:
- (a) sin θ
- (b) cos θ ✓
- (c) -sin θ
- (d) -cos θ

**55.** In rotation transformation, element a₁₂ equals:
- (a) sin θ
- (b) cos θ
- (c) -sin θ ✓
- (d) -cos θ

**56.** Translation is represented in homogeneous coordinates by elements:
- (a) a₁₁ and a₂₂
- (b) a₁₃ and a₂₃ ✓
- (c) a₁₂ and a₂₁
- (d) a₁₁ and a₁₂

**57.** The inverse of scaling by 2 is scaling by:
- (a) -2
- (b) 2
- (c) 0.5 ✓
- (d) 1

**58.** The inverse of rotation by θ is rotation by:
- (a) θ
- (b) -θ ✓
- (c) 90-θ
- (d) 180-θ

**59.** Matrix multiplication for transformations is:
- (a) Commutative
- (b) Not commutative ✓
- (c) Always identity
- (d) Undefined

**60.** Simultaneous contrast refers to:
- (a) Mach bands
- (b) Perceived brightness depending on surroundings ✓
- (c) Color mixing
- (d) Motion perception

**61.** A connected set of pixels forms a:
- (a) Path
- (b) Region ✓
- (c) Boundary
- (d) Neighborhood

**62.** The boundary of a region consists of pixels that:
- (a) Are inside the region
- (b) Have neighbors outside the region ✓
- (c) Are outside the region
- (d) Have maximum intensity

**63.** Speed of light is approximately:
- (a) 3 × 10⁶ m/s
- (b) 3 × 10⁷ m/s
- (c) 3 × 10⁸ m/s ✓
- (d) 3 × 10⁹ m/s

**64.** Focal length of human eye is approximately:
- (a) 5 mm
- (b) 17 mm ✓
- (c) 50 mm
- (d) 100 mm

**65.** Line pair resolution formula: lp/mm = pixels / (2 × mm) because:
- (a) One line pair = 1 pixel
- (b) One line pair = 2 pixels ✓
- (c) One line pair = 4 pixels
- (d) Resolution is doubled

**66.** The XOR operation produces 1 when:
- (a) Both inputs are 0
- (b) Both inputs are 1
- (c) Inputs are different ✓
- (d) At least one input is 1

**67.** AND, OR, NOT are called functionally complete because:
- (a) They are fast
- (b) They can construct any logical operation ✓
- (c) They are simple
- (d) They use less memory

**68.** Which is true about illumination i(x,y)?
- (a) 0 ≤ i(x,y) ≤ 1
- (b) 0 < i(x,y) < ∞ ✓
- (c) -∞ < i(x,y) < ∞
- (d) i(x,y) = 1 always

**69.** Forward mapping in geometric transformation:
- (a) Goes from output to input coordinates
- (b) Goes from input to output coordinates ✓
- (c) Uses inverse matrix
- (d) Is always preferred

**70.** Inverse mapping is preferred because:
- (a) It's faster
- (b) It avoids holes in output ✓
- (c) It's simpler
- (d) It uses less memory

**71.** The human eye can simultaneously discriminate approximately:
- (a) 10 intensity levels
- (b) 100 intensity levels ✓
- (c) 1000 intensity levels
- (d) 10000 intensity levels

**72.** Aliasing appears as:
- (a) False contours
- (b) Wrong frequencies ✓
- (c) Color shifts
- (d) Brightness changes

**73.** The identity transformation matrix has:
- (a) All zeros
- (b) All ones
- (c) 1s on diagonal, 0s elsewhere ✓
- (d) Random values

**74.** Shear transformation affects:
- (a) Size only
- (b) Rotation only
- (c) Shape (slanting) ✓
- (d) Translation only

**75.** Which photoreceptor is absent from the fovea center?
- (a) Cones
- (b) Rods ✓
- (c) Both
- (d) Neither

---

# Short Answer Questions

## Theory Questions with Model Answers

### Q1: Define digital image and digital image processing.
**Answer:**
A **digital image** is a two-dimensional function f(x,y) where x and y are spatial coordinates, and the amplitude of f at any coordinate pair is called the intensity. When x, y, and intensity values are all finite discrete quantities, the image is a digital image.

**Digital image processing** refers to processing digital images by means of a digital computer. It encompasses operations from simple point operations to complex pattern recognition.

---

### Q2: Explain the three levels of image processing with examples.
**Answer:**

| Level | Input | Output | Examples |
|-------|-------|--------|----------|
| **Low-level** | Image | Image | Noise reduction, contrast enhancement, sharpening, filtering |
| **Mid-level** | Image | Attributes | Segmentation, edge detection, object recognition, feature extraction |
| **High-level** | Attributes | Understanding | Scene understanding, autonomous navigation, medical diagnosis |

---

### Q3: What is the image formation model? Explain with typical values.
**Answer:**
The image formation model describes how image intensity is formed:

**f(x,y) = i(x,y) × r(x,y)**

Where:
- **f(x,y)**: Resulting image intensity
- **i(x,y)**: Illumination component (light falling on scene)
  - Range: (0, ∞)
  - Typical: 0 (darkness) to 90,000 lm/m² (bright sunlight)
- **r(x,y)**: Reflectance component (fraction of light reflected)
  - Range: (0, 1)
  - Typical: 0.01 (black velvet) to 0.93 (snow)

---

### Q4: Differentiate between sampling and quantization.
**Answer:**

| Aspect | Sampling | Quantization |
|--------|----------|--------------|
| **Definition** | Digitizing spatial coordinates | Digitizing intensity values |
| **Determines** | Spatial resolution | Intensity resolution |
| **Parameter** | M × N (image dimensions) | k (bits per pixel) |
| **Insufficient leads to** | Aliasing | False contouring |
| **Related theorem** | Nyquist sampling theorem | Bit depth |
| **Unit** | Pixels, samples/mm | Bits, gray levels |

---

### Q5: State and explain the Nyquist sampling theorem.
**Answer:**
**Nyquist Sampling Theorem:** To accurately reconstruct a continuous signal from its samples, the sampling frequency must be at least twice the highest frequency component in the signal.

**Mathematically:** f_sampling ≥ 2 × f_max

**Terms:**
- Nyquist frequency = f_max
- Nyquist rate = 2 × f_max

**Consequence:** If sampling is below Nyquist rate, aliasing occurs where high frequencies appear as lower frequencies, causing artifacts.

---

### Q6: Explain 4-adjacency, 8-adjacency, and m-adjacency.
**Answer:**
Let V be the set of intensity values defining adjacency.

**4-Adjacency:** Two pixels p and q with values from V are 4-adjacent if q is in the 4-neighborhood of p (sharing a horizontal or vertical edge).

**8-Adjacency:** Two pixels p and q with values from V are 8-adjacent if q is in the 8-neighborhood of p (sharing an edge or corner).

**m-Adjacency (Mixed):** Two pixels p and q are m-adjacent if:
1. q is in N₄(p), OR
2. q is in N_D(p) AND the set N₄(p) ∩ N₄(q) contains no pixels from V

**Purpose of m-adjacency:** Eliminates ambiguous multiple paths that exist in 8-adjacency.

---

### Q7: Define and give formulas for three distance measures.
**Answer:**
For pixels p=(x,y) and q=(s,t):

**1. Euclidean Distance (D_e):**
D_e(p,q) = √[(x-s)² + (y-t)²]
- Actual geometric distance
- Non-integer values possible

**2. City-Block Distance (D₄):**
D₄(p,q) = |x-s| + |y-t|
- Sum of absolute differences
- Always integer
- Forms diamond-shaped equidistant points

**3. Chessboard Distance (D₈):**
D₈(p,q) = max(|x-s|, |y-t|)
- Maximum of absolute differences
- Always integer
- Forms square-shaped equidistant points

---

### Q8: What is false contouring? When does it occur and how can it be prevented?
**Answer:**
**False contouring** is the appearance of artificial edges or contour lines in regions that should have smooth intensity gradients.

**Cause:** Insufficient number of gray levels (low bits per pixel) to represent smooth gradients.

**When it occurs:**
- Low k value (few bits per pixel)
- Smooth gradient regions
- Large uniform areas
- Images with subtle intensity variations

**Prevention:**
1. Increase bits per pixel (use higher k)
2. Add small amount of noise (dithering)
3. Use error diffusion techniques
4. Apply spatial filtering

---

### Q9: Explain linear and nonlinear operations with examples.
**Answer:**
**Linear Operation:** An operator H is linear if:
H[a₁f₁ + a₂f₂] = a₁H[f₁] + a₂H[f₂]

This requires:
- Additivity: H[f₁ + f₂] = H[f₁] + H[f₂]
- Homogeneity: H[af] = aH[f]

**Linear Examples:**
- Addition: g = f₁ + f₂
- Subtraction: g = f₁ - f₂
- Scaling: g = a × f
- Averaging: g = (1/n)Σfᵢ

**Nonlinear Examples:**
- Multiplication: g = f₁ × f₂
- Division: g = f₁ / f₂
- Median filtering
- Maximum/Minimum operations
- Thresholding

---

### Q10: Explain noise reduction by image averaging with mathematical proof.
**Answer:**
**Principle:** If we have K noisy images of the same static scene:
gᵢ(x,y) = f(x,y) + ηᵢ(x,y)

Where:
- f(x,y) = true image
- ηᵢ(x,y) = additive noise (random, zero mean, uncorrelated)

**Averaging:**
ḡ(x,y) = (1/K) × Σᵢ₌₁ᴷ gᵢ(x,y)

**Expected Value:**
E[ḡ(x,y)] = E[(1/K)Σgᵢ]
          = (1/K)Σ E[f + ηᵢ]
          = (1/K)Σ [f + 0]    (since E[η] = 0)
          = f(x,y)

**Variance:**
σ²_ḡ = Var[(1/K)Σgᵢ]
     = (1/K²) × K × σ²_η     (uncorrelated noise)
     = σ²_η / K

**Conclusion:** Averaging K images reduces noise standard deviation by √K.

---

### Q11: State and prove DeMorgan's Laws.
**Answer:**
**DeMorgan's Laws:**
1. (A ∪ B)ᶜ = Aᶜ ∩ Bᶜ
2. (A ∩ B)ᶜ = Aᶜ ∪ Bᶜ

**Proof using Truth Tables:**

| A | B | A∪B | (A∪B)ᶜ | Aᶜ | Bᶜ | Aᶜ∩Bᶜ |
|---|---|-----|--------|----|----|-------|
| 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 | 0 | 0 |
| 1 | 0 | 1 | 0 | 0 | 1 | 0 |
| 1 | 1 | 1 | 0 | 0 | 0 | 0 |

Columns (A∪B)ᶜ and Aᶜ∩Bᶜ are identical, proving Law 1.

Similar proof for Law 2.

---

### Q12: Describe the three interpolation methods used in image resizing.
**Answer:**

**1. Nearest Neighbor Interpolation:**
- Uses value of closest pixel
- Pros: Simple, fast, preserves sharp edges
- Cons: Blocky appearance, jagged edges
- Best for: Speed-critical applications, pixel art

**2. Bilinear Interpolation:**
- Uses weighted average of 4 nearest neighbors
- Formula: v(x',y') = (1-a)(1-b)v₀₀ + a(1-b)v₁₀ + (1-a)b·v₀₁ + ab·v₁₁
- Pros: Smoother than nearest neighbor
- Cons: Some blurring at edges
- Best for: General purpose resizing

**3. Bicubic Interpolation:**
- Uses 16 nearest neighbors (4×4 grid)
- Uses cubic polynomial fitting
- Pros: Highest quality, smooth results
- Cons: Most computationally expensive
- Best for: High-quality image processing

---

### Q13: Explain Mach bands and simultaneous contrast.
**Answer:**

**Mach Bands:**
- Apparent bright/dark bands at intensity transitions that don't physically exist
- Cause: Lateral inhibition in retina (neurons inhibit neighbors)
- Effect: Edge enhancement in visual system
- Significance: Perception differs from physical reality

**Simultaneous Contrast:**
- Same gray appears different against different backgrounds
- A gray square looks darker on light background, lighter on dark background
- Cause: Lateral inhibition and relative intensity processing
- Significance: Absolute intensity judgments are unreliable

**Common Feature:** Both demonstrate that human vision responds to relative, not absolute, intensities.

---

### Q14: Describe geometric transformations and their matrix representations.
**Answer:**
Using homogeneous coordinates [x', y', 1]ᵀ = A × [x, y, 1]ᵀ

**1. Scaling:**
```
[sₓ  0   0]
[0   sᵧ  0]
[0   0   1]
```
Effect: x' = sₓ·x, y' = sᵧ·y

**2. Translation:**
```
[1  0  tₓ]
[0  1  tᵧ]
[0  0  1]
```
Effect: x' = x + tₓ, y' = y + tᵧ

**3. Rotation (by θ counterclockwise):**
```
[cosθ  -sinθ  0]
[sinθ   cosθ  0]
[0      0     1]
```
Effect: x' = x·cosθ - y·sinθ, y' = x·sinθ + y·cosθ

**4. Shearing:**
Horizontal: x' = x + sh·y
Vertical: y' = sh·x + y

**Composite Transformations:** Multiply matrices (order matters!)

---

### Q15: What are rods and cones? Compare their properties.
**Answer:**

| Property | Cones | Rods |
|----------|-------|------|
| Number | 6-7 million | 75-150 million |
| Location | Concentrated in fovea | Distributed in retina |
| Absent from | Extreme periphery | Center of fovea |
| Light sensitivity | Low (bright light) | High (dim light) |
| Color vision | Yes (3 types) | No |
| Resolution | High | Low |
| Vision type | Photopic (day) | Scotopic (night) |
| Response speed | Fast | Slow |

**Significance:** Different receptors optimize vision for different conditions.

---

# Previous Year Question Patterns

## Typical Exam Structure

### Short Questions (2-3 marks each)
1. Define digital image
2. List components of image processing system
3. State Nyquist theorem
4. Define 4-adjacency and 8-adjacency
5. Give formula for city-block distance
6. What is false contouring?
7. State DeMorgan's laws
8. Define linear operation

### Medium Questions (5-6 marks each)
1. Explain image formation model with diagram
2. Compare sampling and quantization
3. Describe three interpolation methods
4. Explain noise reduction by averaging (with derivation)
5. Differentiate between rods and cones
6. Calculate storage for given image specifications
7. Find distances between two points using all three measures

### Long Questions (10-12 marks each)
1. Explain fundamental steps in digital image processing with diagram
2. Describe elements of visual perception including eye structure
3. Explain all types of adjacency with examples and m-path finding
4. Derive noise reduction formula and solve numerical
5. Explain geometric transformations with all matrix forms
6. Prove DeMorgan's laws and apply to binary images

## Common Numerical Problems

1. **Storage calculation:** Given M, N, k, find storage in KB/MB
2. **Resolution calculation:** Given pixels and physical size, find lp/mm or DPI
3. **Distance calculation:** Find D_e, D_4, D_8 between two points
4. **Noise reduction:** Find K for desired noise reduction
5. **Path finding:** Find shortest 4/8/m-path in given grid
6. **Transformation:** Apply scaling/rotation/translation to points
7. **Transmission time:** Given image specs and bandwidth, find time

---

# Quick Revision Notes

## One-Page Summary

### Chapter 1 Key Points
- Digital image: f(x,y) with discrete values
- Processing levels: Low→Mid→High
- Historical: 1920s Bartlane, 1970s CT scanner
- Applications span entire EM spectrum
- Pipeline: Acquire→Enhance→Restore→Segment→Recognize

### Chapter 2 Key Points

**Visual System:**
- Cones: 6-7M, color, fovea
- Rods: 75-150M, night vision
- Weber ratio ≈ 0.02
- Mach bands, simultaneous contrast

**Image Formation:**
- f(x,y) = i(x,y) × r(x,y)
- i: illumination (0,∞)
- r: reflectance (0,1)

**Digitization:**
- Sampling: spatial discretization
- Quantization: intensity discretization
- b = M × N × k bits
- L = 2^k levels
- Nyquist: f_s ≥ 2f_max

**Pixel Relationships:**
- N₄: 4-neighbors (edges)
- N_D: diagonal neighbors
- N₈ = N₄ ∪ N_D
- m-adjacency: eliminates ambiguity

**Distances:**
- D_e = √[(x-s)² + (y-t)²]
- D₄ = |x-s| + |y-t|
- D₈ = max(|x-s|, |y-t|)

**Operations:**
- Linear: addition, subtraction, averaging
- Nonlinear: multiplication, median
- Noise reduction: σ_avg = σ/√K

**Transformations:**
- Scale: diag(sₓ, sᵧ, 1)
- Translate: [1,0,tₓ; 0,1,tᵧ; 0,0,1]
- Rotate: [cosθ,-sinθ; sinθ,cosθ]

**Set Operations:**
- (A∪B)ᶜ = Aᶜ∩Bᶜ
- (A∩B)ᶜ = Aᶜ∪Bᶜ

---

## Must-Remember Formulas

```
λ = c/ν                    (c = 3×10⁸ m/s)
f(x,y) = i(x,y) × r(x,y)
b = M × N × k bits
L = 2^k levels
f_s ≥ 2×f_max              (Nyquist)
D_e = √[(x-s)² + (y-t)²]
D₄ = |x-s| + |y-t|
D₈ = max(|x-s|, |y-t|)
σ²_avg = σ²/K
SNR improvement = √K
```

---

## Last-Minute Tips

1. **Know formulas** - Practice calculations
2. **Understand concepts** - Don't just memorize
3. **Draw diagrams** - Eye structure, Venn diagrams, neighborhoods
4. **Practice numericals** - Storage, resolution, distance, noise
5. **Review adjacency** - 4/8/m paths are commonly asked
6. **Transformation matrices** - Know all four types
7. **DeMorgan's laws** - Can be asked as proof or application

---

**Good Luck with Your Exam!**

---
*Document prepared for exam preparation - Chapters 1 & 2*
*Digital Image Processing, 4th Edition by Gonzalez & Woods*
