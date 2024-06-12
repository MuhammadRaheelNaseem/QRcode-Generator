![image](https://github.com/MuhammadRaheelNaseem/QRcode-Generator/assets/63813881/cbb5c64f-e2db-4c1b-802f-b8c423dd838d)# Generating Stylish QR Codes with Python

This repository demonstrates how to generate QR codes with various styles using Python. QR codes can be customized with different module drawers and color masks to achieve unique appearances.

## Overview

QR (Quick Response) codes are two-dimensional barcodes that store data in a matrix pattern of black squares on a white background. This repository provides Python scripts to generate QR codes with different visual styles, showcasing the versatility of the qrcode library.

## Table of Contents

1. [Introduction](#introduction)
2. [Requirements](#requirements)
3. [Usage](#usage)
4. [Styles](#styles)
    - [Module Drawers](#module-drawers)
    - [Color Masks](#color-masks)
5. [Examples](#examples)
6. [Contributing](#contributing)
7. [License](#license)

## Introduction

In this repository, you'll find Python scripts that utilize the qrcode library to create customized QR codes. These QR codes can be styled with different module drawers and color masks to achieve visually appealing results. This README provides an overview of the scripts and demonstrates the various styles available.

## Requirements

To run the scripts in this repository, you'll need:

- Python 3.x
- qrcode library
- matplotlib library

You can install the required libraries via pip:

```bash
pip install qrcode matplotlib
```

## Usage

To generate QR codes with different styles, simply run the Python script provided in this repository. The script will generate QR code images with various visual effects based on the specified module drawers and color masks.

```bash
python generate_qr_codes.py
```

## Styles

### Module Drawers

Module drawers determine the shape of the individual squares (modules) in the QR code. The following module drawers are available:

- Square Module Drawer
- Gapped Square Module Drawer
- Circle Module Drawer
- Rounded Module Drawer
- Vertical Bars Drawer
- Horizontal Bars Drawer

### Color Masks

Color masks add color and gradients to the QR code. The following color masks are available:

- Solid Fill Color Mask
- Radial Gradient Color Mask
- Square Gradient Color Mask
- Horizontal Gradient Color Mask
- Vertical Gradient Color Mask

### Lets Code Know
```python
import qrcode
from qrcode.image.styledpil import StyledPilImage
from qrcode.image.styles.moduledrawers import (
    SquareModuleDrawer, GappedSquareModuleDrawer, CircleModuleDrawer, 
    RoundedModuleDrawer, VerticalBarsDrawer, HorizontalBarsDrawer
)
from qrcode.image.styles.colormasks import (
    SolidFillColorMask, RadialGradiantColorMask, SquareGradiantColorMask, 
    HorizontalGradiantColorMask, VerticalGradiantColorMask, ImageColorMask
)
import matplotlib.pyplot as plt

# List of module drawers and color masks to use
module_drawers = [
    ("SquareModuleDrawer", SquareModuleDrawer()),
    ("GappedSquareModuleDrawer", GappedSquareModuleDrawer()),
    ("CircleModuleDrawer", CircleModuleDrawer()),
    ("RoundedModuleDrawer", RoundedModuleDrawer()),
    ("VerticalBarsDrawer", VerticalBarsDrawer()),
    ("HorizontalBarsDrawer", HorizontalBarsDrawer())
]

color_masks = [
    ("SolidFillColorMask", SolidFillColorMask()),
    ("RadialGradiantColorMask", RadialGradiantColorMask()),
    ("SquareGradiantColorMask", SquareGradiantColorMask()),
    ("HorizontalGradiantColorMask", HorizontalGradiantColorMask()),
    ("VerticalGradiantColorMask", VerticalGradiantColorMask()),
    # Replace '/path/to/image.png' with a valid image path
    # ("ImageColorMask", ImageColorMask(back_color=(255, 255, 255), image_path='/path/to/image.png'))
]

# Data to encode in the QR code
data = 'https://xpacetechnologies.com'

# Function to generate QR code image
# Function to generate QR code image
def generate_qr(module_drawer=None, color_mask=None):
    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_L,
        box_size=10,
        border=4,
    )
    qr.add_data(data)
    qr.make(fit=True)
    kwargs = {}
    if module_drawer is not None:
        kwargs['module_drawer'] = module_drawer
    if color_mask is not None:
        kwargs['color_mask'] = color_mask
    img = qr.make_image(image_factory=StyledPilImage, **kwargs)
    return img


# Plot QR codes
fig, axes = plt.subplots(nrows=3, ncols=4, figsize=(20, 15))
fig.suptitle('QR Code Styles', fontsize=20)

# Plot QR codes with different module drawers
for i, (name, drawer) in enumerate(module_drawers):
    img = generate_qr(module_drawer=drawer)
    ax = axes[i // 4, i % 4]
    ax.imshow(img)
    ax.set_title(name)
    ax.axis('off')

# Plot QR codes with different color masks
for i, (name, mask) in enumerate(color_masks):
    img = generate_qr(color_mask=mask)
    ax = axes[(i + len(module_drawers)) // 4, (i + len(module_drawers)) % 4]
    ax.imshow(img)
    ax.set_title(name)
    ax.axis('off')

plt.tight_layout(rect=[0, 0, 1, 0.96])
plt.show()
```
![image](https://github.com/MuhammadRaheelNaseem/QRcode-Generator/assets/63813881/4402d04b-f997-4229-b1ab-a46006a1ee26)

### Explaination
### Importing Libraries:
```python
import qrcode
from qrcode.image.styledpil import StyledPilImage
from qrcode.image.styles.moduledrawers import (
    SquareModuleDrawer, GappedSquareModuleDrawer, CircleModuleDrawer, 
    RoundedModuleDrawer, VerticalBarsDrawer, HorizontalBarsDrawer
)
from qrcode.image.styles.colormasks import (
    SolidFillColorMask, RadialGradiantColorMask, SquareGradiantColorMask, 
    HorizontalGradiantColorMask, VerticalGradiantColorMask, ImageColorMask
)
import matplotlib.pyplot as plt
```
- The script starts by importing necessary libraries.
- `qrcode` is used for generating QR codes.
- `StyledPilImage` is an image factory provided by `qrcode` library for creating styled QR code images.
- `moduledrawers` and `colormasks` contain various styles for drawing modules (QR code squares) and applying color masks to QR codes, respectively.
- `matplotlib.pyplot` is imported for plotting the QR codes.

### Configuration:
```python
# List of module drawers and color masks to use
module_drawers = [
    ("SquareModuleDrawer", SquareModuleDrawer()),
    ("GappedSquareModuleDrawer", GappedSquareModuleDrawer()),
    ("CircleModuleDrawer", CircleModuleDrawer()),
    ("RoundedModuleDrawer", RoundedModuleDrawer()),
    ("VerticalBarsDrawer", VerticalBarsDrawer()),
    ("HorizontalBarsDrawer", HorizontalBarsDrawer())
]

color_masks = [
    ("SolidFillColorMask", SolidFillColorMask()),
    ("RadialGradiantColorMask", RadialGradiantColorMask()),
    ("SquareGradiantColorMask", SquareGradiantColorMask()),
    ("HorizontalGradiantColorMask", HorizontalGradiantColorMask()),
    ("VerticalGradiantColorMask", VerticalGradiantColorMask()),
    # Replace '/path/to/image.png' with a valid image path
    # ("ImageColorMask", ImageColorMask(back_color=(255, 255, 255), image_path='/path/to/image.png'))
]
```
- Lists are created to hold different module drawers and color masks along with their names.

### Data:
```python
# Data to encode in the QR code
data = 'https://xpacetechnologies.com'
```
- The URL to be encoded into the QR code is defined here.

### Function for Generating QR Codes:
```python
# Function to generate QR code image
def generate_qr(module_drawer=None, color_mask=None):
    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_L,
        box_size=10,
        border=4,
    )
    qr.add_data(data)
    qr.make(fit=True)
    kwargs = {}
    if module_drawer is not None:
        kwargs['module_drawer'] = module_drawer
    if color_mask is not None:
        kwargs['color_mask'] = color_mask
    img = qr.make_image(image_factory=StyledPilImage, **kwargs)
    return img
```
- This function generates a QR code image with optional styling parameters.
- It initializes a QRCode object with specified parameters like version, error correction level, box size, and border.
- Data is added to the QRCode object.
- The `make()` method generates the QR code pattern.
- Styling parameters like module drawer and color mask are applied if provided.
- Finally, the image is generated using the `make_image()` method of the QRCode object.

### Plotting QR Codes:
```python
# Plot QR codes
fig, axes = plt.subplots(nrows=3, ncols=4, figsize=(20, 15))
fig.suptitle('QR Code Styles', fontsize=20)

# Plot QR codes with different module drawers
for i, (name, drawer) in enumerate(module_drawers):
    img = generate_qr(module_drawer=drawer)
    ax = axes[i // 4, i % 4]
    ax.imshow(img)
    ax.set_title(name)
    ax.axis('off')

# Plot QR codes with different color masks
for i, (name, mask) in enumerate(color_masks):
    img = generate_qr(color_mask=mask)
    ax = axes[(i + len(module_drawers)) // 4, (i + len(module_drawers)) % 4]
    ax.imshow(img)
    ax.set_title(name)
    ax.axis('off')

plt.tight_layout(rect=[0, 0, 1, 0.96])
plt.show()
```
- Subplots are created using `plt.subplots()` with a grid layout.
- The title for the plot is set.
- QR codes with different module drawers are plotted first, followed by QR codes with different color masks.
- For each QR code, the `generate_qr()` function is called with appropriate parameters, and the resulting image is plotted on a subplot.
- Titles are set for each subplot, and axis visibility is turned off.
- Finally, the plot is displayed using `plt.show()`.

### Script
```python
import qrcode
from qrcode.image.styledpil import StyledPilImage
from qrcode.image.styles.moduledrawers import (
    SquareModuleDrawer, GappedSquareModuleDrawer, CircleModuleDrawer, 
    RoundedModuleDrawer, VerticalBarsDrawer, HorizontalBarsDrawer
)
from qrcode.image.styles.colormasks import (
    SolidFillColorMask, RadialGradiantColorMask, SquareGradiantColorMask, 
    HorizontalGradiantColorMask, VerticalGradiantColorMask, ImageColorMask
)
import matplotlib.pyplot as plt

# URL to encode in the QR code
url = 'https://xpacetechnologies.com'

# Generate QR code with SquareModuleDrawer
def generate_square_qr():
    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_L,
        box_size=10,
        border=2,
    )
    qr.add_data(url)
    qr.make(fit=True)
    img = qr.make_image(image_factory=StyledPilImage, module_drawer=SquareModuleDrawer())
    return img

# Plot each QR code individually
def plot_qr(img, title):
    plt.figure(figsize=(15, 15))
    plt.imshow(img)
    plt.title(title)
    plt.axis('off')
    plt.show()

# Generate and plot each QR code
plot_qr(generate_square_qr(), "SquareModuleDrawer")
```
![image](https://github.com/MuhammadRaheelNaseem/QRcode-Generator/assets/63813881/d45f774a-4975-40ef-8b28-c0120f97264b)

```python
import qrcode
from qrcode.image.styledpil import StyledPilImage
from qrcode.image.styles.moduledrawers import (
    SquareModuleDrawer, GappedSquareModuleDrawer, CircleModuleDrawer, 
    RoundedModuleDrawer, VerticalBarsDrawer, HorizontalBarsDrawer
)
from qrcode.image.styles.colormasks import (
    SolidFillColorMask, RadialGradiantColorMask, SquareGradiantColorMask, 
    HorizontalGradiantColorMask, VerticalGradiantColorMask, ImageColorMask
)
import matplotlib.pyplot as plt

# URL to encode in the QR code
url = 'https://xpacetechnologies.com'

# Generate QR code with GappedSquareModuleDrawer
def generate_gapped_square_qr():
    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_L,
        box_size=10,
        border=4,
    )
    qr.add_data(url)
    qr.make(fit=True)
    img = qr.make_image(image_factory=StyledPilImage, module_drawer=GappedSquareModuleDrawer())
    return img


# Plot each QR code individually
def plot_qr(img, title):
    plt.figure(figsize=(15, 15))
    plt.imshow(img)
    plt.title(title)
    plt.axis('off')
    plt.show()

# Generate and plot each QR code
plot_qr(generate_gapped_square_qr(), "GappedSquareModuleDrawer")
```

![image](https://github.com/MuhammadRaheelNaseem/QRcode-Generator/assets/63813881/6ca139d9-6694-44b6-a590-7e0468c57183)


### Script
```python
import qrcode
from qrcode.image.styledpil import StyledPilImage
from qrcode.image.styles.moduledrawers import (
    SquareModuleDrawer, GappedSquareModuleDrawer, CircleModuleDrawer, 
    RoundedModuleDrawer, VerticalBarsDrawer, HorizontalBarsDrawer
)
from qrcode.image.styles.colormasks import (
    SolidFillColorMask, RadialGradiantColorMask, SquareGradiantColorMask, 
    HorizontalGradiantColorMask, VerticalGradiantColorMask, ImageColorMask
)
import matplotlib.pyplot as plt

# URL to encode in the QR code
url = 'https://xpacetechnologies.com'


# Generate QR code with CircleModuleDrawer
def generate_circle_qr():
    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_L,
        box_size=10,
        border=4,
    )
    qr.add_data(url)
    qr.make(fit=True)
    img = qr.make_image(image_factory=StyledPilImage, module_drawer=CircleModuleDrawer())
    return img


# Plot each QR code individually
def plot_qr(img, title):
    plt.figure(figsize=(15, 15))
    plt.imshow(img)
    plt.title(title)
    plt.axis('off')
    plt.show()

# Generate and plot each QR code
plot_qr(generate_circle_qr(), "CircleModuleDrawer")
```
![image](https://github.com/MuhammadRaheelNaseem/QRcode-Generator/assets/63813881/17a0fef6-9d97-4b76-a43f-7d99d3226b61)

### Script
```python
import qrcode
from qrcode.image.styledpil import StyledPilImage
from qrcode.image.styles.moduledrawers import (
    SquareModuleDrawer, GappedSquareModuleDrawer, CircleModuleDrawer, 
    RoundedModuleDrawer, VerticalBarsDrawer, HorizontalBarsDrawer
)
from qrcode.image.styles.colormasks import (
    SolidFillColorMask, RadialGradiantColorMask, SquareGradiantColorMask, 
    HorizontalGradiantColorMask, VerticalGradiantColorMask, ImageColorMask
)
import matplotlib.pyplot as plt

# URL to encode in the QR code
url = 'https://xpacetechnologies.com'

# Generate QR code with RoundedModuleDrawer
def generate_rounded_qr():
    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_L,
        box_size=10,
        border=4,
    )
    qr.add_data(url)
    qr.make(fit=True)
    img = qr.make_image(image_factory=StyledPilImage, module_drawer=RoundedModuleDrawer())
    return img


# Plot each QR code individually
def plot_qr(img, title):
    plt.figure(figsize=(15, 15))
    plt.imshow(img)
    plt.title(title)
    plt.axis('off')
    plt.show()

# Generate and plot each QR code
plot_qr(generate_rounded_qr(), "RoundedModuleDrawer")
```
![image](https://github.com/MuhammadRaheelNaseem/QRcode-Generator/assets/63813881/98493794-cc8d-4bbd-9622-7b94279f2498)

### Script
```python
import qrcode
from qrcode.image.styledpil import StyledPilImage
from qrcode.image.styles.moduledrawers import (
    SquareModuleDrawer, GappedSquareModuleDrawer, CircleModuleDrawer, 
    RoundedModuleDrawer, VerticalBarsDrawer, HorizontalBarsDrawer
)
from qrcode.image.styles.colormasks import (
    SolidFillColorMask, RadialGradiantColorMask, SquareGradiantColorMask, 
    HorizontalGradiantColorMask, VerticalGradiantColorMask, ImageColorMask
)
import matplotlib.pyplot as plt

# URL to encode in the QR code
url = 'https://xpacetechnologies.com'

# Generate QR code with VerticalBarsDrawer
def generate_vertical_bars_qr():
    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_L,
        box_size=10,
        border=4,
    )
    qr.add_data(url)
    qr.make(fit=True)
    img = qr.make_image(image_factory=StyledPilImage, module_drawer=VerticalBarsDrawer())
    return img


# Plot each QR code individually
def plot_qr(img, title):
    plt.figure(figsize=(15, 15))
    plt.imshow(img)
    plt.title(title)
    plt.axis('off')
    plt.show()

# Generate and plot each QR code
plot_qr(generate_vertical_bars_qr(), "VerticalBarsDrawer")
```

![image](https://github.com/MuhammadRaheelNaseem/QRcode-Generator/assets/63813881/9e40b677-e614-4552-a7c6-60ac4ff98df9)


### Script
```python
import qrcode
from qrcode.image.styledpil import StyledPilImage
from qrcode.image.styles.moduledrawers import (
    SquareModuleDrawer, GappedSquareModuleDrawer, CircleModuleDrawer, 
    RoundedModuleDrawer, VerticalBarsDrawer, HorizontalBarsDrawer
)
from qrcode.image.styles.colormasks import (
    SolidFillColorMask, RadialGradiantColorMask, SquareGradiantColorMask, 
    HorizontalGradiantColorMask, VerticalGradiantColorMask, ImageColorMask
)
import matplotlib.pyplot as plt

# URL to encode in the QR code
url = 'https://xpacetechnologies.com'

# Generate QR code with HorizontalBarsDrawer
def generate_horizontal_bars_qr():
    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_L,
        box_size=10,
        border=4,
    )
    qr.add_data(url)
    qr.make(fit=True)
    img = qr.make_image(image_factory=StyledPilImage, module_drawer=HorizontalBarsDrawer())
    return img

# Plot each QR code individually
def plot_qr(img, title):
    plt.figure(figsize=(15, 15))
    plt.imshow(img)
    plt.title(title)
    plt.axis('off')
    plt.show()

# Generate and plot each QR code
plot_qr(generate_horizontal_bars_qr(), "HorizontalBarsDrawer")
```
![image](https://github.com/MuhammadRaheelNaseem/QRcode-Generator/assets/63813881/033bf5f5-a35e-4af1-99b7-15e25a5b3974)


