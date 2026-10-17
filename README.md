# Experiment 1: Image Handling and Pixel Transformations Using OpenCV

**Name:** SHRIVARSHAN P G  
**Register Number:** 212225240146  
**Experiment:** Image Handling and Pixel Transformations Using OpenCV

---

## AIM

To perform image handling and pixel transformations using Python and OpenCV, including reading and displaying images, drawing shapes, adding text, color space conversion, pixel manipulation, image resizing, cropping, flipping, and saving the modified image.

## SOFTWARE REQUIRED

- Python
- OpenCV
- Matplotlib
- Jupyter Notebook
- Anaconda (optional)

## INSTALLATION

Install the required libraries using the following command:

```bash
pip install opencv-contrib-python-headless matplotlib
```

## ALGORITHM

### Step 1: Read and Display an Image

1. Import OpenCV and Matplotlib libraries.
2. Read an image from the local directory using `cv2.imread()`.
3. Convert the image from BGR to RGB.
4. Display the original image using Matplotlib.

### Step 2: Draw Shapes and Add Text

1. Draw a line from the top-left to the bottom-right of the image.
2. Draw a circle at the center of the image.
3. Draw a rectangle around the image.
4. Add the text "OpenCV Drawing" at the top-left corner.

### Step 3: Color Space Conversion

1. Convert the RGB image to HSV and display it.
2. Convert the RGB image to grayscale and display it.
3. Convert the RGB image to YCrCb and display it.
4. Convert the HSV image back to RGB and display it.

### Step 4: Pixel Manipulation

1. Access and print the pixel value at coordinates `(100, 100)`.
2. Change the pixel at coordinates `(200, 200)` to white.
3. Modify a 300 × 300 region of the image to white.
4. Display the modified image.

### Step 5: Image Resizing

1. Read the original image.
2. Resize the image to half its original width and height.
3. Display the resized image.

### Step 6: Image Cropping

1. Read the original image.
2. Extract a 300 × 300 region of interest starting at `(50, 50)`.
3. Display the cropped image.

### Step 7: Image Flipping

1. Flip the original image horizontally.
2. Flip the original image vertically.
3. Display both flipped images.

### Step 8: Save the Final Modified Image

1. Save the modified image in the local directory using `cv2.imwrite()`.
2. Verify that the image has been saved successfully.

---

## PROGRAM

### Step 1: Read and Display an Image

```python
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('varshan.jpeg', cv2.IMREAD_COLOR)

if img is None:
    raise FileNotFoundError("varshan.jpeg not found")

# Convert BGR to RGB
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display the original image
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()
```

### Step 2: Draw Shapes and Add Text

#### 2.1 Draw a Line

```python
# Load the image
image = cv2.imread('Qno. 1.jpg')

if image is None:
    raise FileNotFoundError("Qno. 1.jpg not found")

# Convert BGR to RGB
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

height, width = img_rgb.shape[:2]

# Draw a line from top-left to bottom-right
line_img = cv2.line(
    img_rgb.copy(),
    (0, 0),
    (width - 1, height - 1),
    (255, 0, 0),
    2
)

# Display the image
plt.imshow(line_img)
plt.title("Image with Line")
plt.axis('off')
plt.show()
```

#### 2.2 Draw a Circle

```python
# Draw a circle at the center of the image
circle_img = cv2.circle(
    img_rgb.copy(),
    (width // 2, height // 2),
    150,
    (255, 0, 0),
    10
)

# Display the image
plt.imshow(circle_img)
plt.title("Image with Circle")
plt.axis('off')
plt.show()
```

#### 2.3 Draw a Rectangle

```python
# Draw a rectangle around the whole image
rectangle_img = cv2.rectangle(
    img_rgb.copy(),
    (0, 0),
    (width - 1, height - 1),
    (0, 0, 255),
    10
)

# Display the image
plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()
```

#### 2.4 Add Text to the Image

```python
# Add text to the image
text_img = cv2.putText(
    img_rgb.copy(),
    "OpenCV Drawing",
    (10, 30),
    cv2.FONT_HERSHEY_SIMPLEX,
    1,
    (255, 255, 255),
    10
)

# Display the image
plt.imshow(text_img)
plt.title("Image with Text")
plt.axis('off')
plt.show()
```

### Step 3: Color Space Conversion

```python
# Read the image
image = cv2.imread('varshan.jpeg')

if image is None:
    raise FileNotFoundError("varshan.jpeg not found")

# Convert BGR to RGB
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the original RGB image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
plt.show()

# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

plt.imshow(cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB))
plt.title("HSV Image")
plt.axis("off")
plt.show()

# Convert RGB to grayscale
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
plt.show()

# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

plt.imshow(cv2.cvtColor(image_ycrcb, cv2.COLOR_YCrCb2RGB))
plt.title("YCrCb Image")
plt.axis("off")
plt.show()

# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
plt.show()
```

### Step 4: Pixel Manipulation

```python
# Read the image
image = cv2.imread('varshan.jpeg')

if image is None:
    raise FileNotFoundError("varshan.jpeg not found")

height, width = image.shape[:2]

# Access and print the pixel value at (100, 100)
if height > 100 and width > 100:
    pixel_value = image[100, 100]
    print("Pixel value at (100, 100):", pixel_value)

# Modify the pixel at (200, 200) to white
if height > 200 and width > 200:
    image[200, 200] = [255, 255, 255]

# Modify a 300x300 block starting at (200, 200)
image[200:min(500, height), 200:min(500, width)] = [255, 255, 255]

# Convert BGR to RGB
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with White Block")
plt.axis("off")
plt.show()
```

### Step 5: Image Resizing

```python
# Read the original image
image = cv2.imread('varshan.jpeg')

if image is None:
    raise FileNotFoundError("varshan.jpeg not found")

# Get the original dimensions
height, width = image.shape[:2]

print("Original dimensions:", image.shape)

# Resize the image to half its original dimensions
resized_image = cv2.resize(
    image,
    (width // 2, height // 2)
)

# Convert BGR to RGB
resized_image_rgb = cv2.cvtColor(
    resized_image,
    cv2.COLOR_BGR2RGB
)

print("Resized dimensions:", resized_image.shape)

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```

### Step 6: Image Cropping

```python
# Read the original image
image = cv2.imread('varshan.jpeg')

if image is None:
    raise FileNotFoundError("varshan.jpeg not found")

# Crop a 300x300 region starting at (50, 50)
roi = image[50:350, 50:350]

# Convert BGR to RGB
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```

### Step 7: Image Flipping

```python
# Read the original image
image = cv2.imread('varshan.jpeg')

if image is None:
    raise FileNotFoundError("varshan.jpeg not found")

# Flip horizontally
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB
flipped_horizontally_rgb = cv2.cvtColor(
    flipped_horizontally,
    cv2.COLOR_BGR2RGB
)

# Display the horizontally flipped image
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()

# Flip vertically
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB
flipped_vertically_rgb = cv2.cvtColor(
    flipped_vertically,
    cv2.COLOR_BGR2RGB
)

# Display the vertically flipped image
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
plt.show()
```

### Step 8: Save the Final Modified Image

```python
# Save the final modified image
output_file = 'final_modified_image.jpg'

success = cv2.imwrite(output_file, image)

if success:
    print("Image saved successfully as", output_file)
else:
    print("Failed to save the image")
```

---

## OUTPUT

The following outputs are obtained:

1. Original image displayed using OpenCV and Matplotlib.

<img width="678" height="432" alt="image" src="https://github.com/user-attachments/assets/3c9e1b80-5327-4524-bf3e-ea608081b473" />



2. Image with a line drawn from the top-left to the bottom-right.

<img width="721" height="432" alt="image" src="https://github.com/user-attachments/assets/deb7809f-a2e8-4991-afb8-2c8ffca5117a" />


3. Image with a circle at the center.

<img width="720" height="437" alt="image" src="https://github.com/user-attachments/assets/b9402871-5e57-437c-a9b6-3ad1f30c2323" />


4. Image with a rectangle around its boundary.

<img width="750" height="426" alt="image" src="https://github.com/user-attachments/assets/2ec802bc-4413-4d7d-8e52-4b473ac5b09f" />


5. Image with the text "OpenCV Drawing".

<img width="663" height="428" alt="image" src="https://github.com/user-attachments/assets/d8f9ebc8-99ea-4660-81c9-685a63477c13" />


6. HSV, grayscale, and YCrCb color space conversions.


<img width="686" height="417" alt="image" src="https://github.com/user-attachments/assets/e42fbc15-5451-4e5a-a415-d0feb7fb5323" />


<img width="717" height="430" alt="image" src="https://github.com/user-attachments/assets/a8c7cd28-f6d7-4880-88cd-12d78ce68e66" />


<img width="656" height="417" alt="image" src="https://github.com/user-attachments/assets/3e7ad44f-df51-499e-9431-38cffb50e9b8" />



7. Image converted from HSV back to RGB.

<img width="657" height="420" alt="image" src="https://github.com/user-attachments/assets/8c0beb67-2591-4ac9-b292-8164c13a0a61" />


8. Pixel value displayed and a white region added to the image.

<img width="665" height="436" alt="image" src="https://github.com/user-attachments/assets/6be15860-2780-41c2-8ac4-c9b4be4ce7b9" />


9. Image resized to half its original dimensions.

<img width="672" height="501" alt="image" src="https://github.com/user-attachments/assets/a543c77c-b33d-4ccb-8132-4f626a6fedbc" />


10. Cropped region of interest displayed.

<img width="547" height="515" alt="image" src="https://github.com/user-attachments/assets/9c8cd59c-3652-4ac1-9174-0a998dc5c800" />


11. Horizontally flipped image displayed.

<img width="722" height="425" alt="image" src="https://github.com/user-attachments/assets/6a0c6e1d-f9dc-41e4-a154-665a248da976" />

12. Vertically flipped image displayed.

<img width="662" height="417" alt="image" src="https://github.com/user-attachments/assets/7e119060-625b-4441-93b3-70ca3b04be8e" />
## RESULT

Thus, image handling and pixel transformations were performed using Python, OpenCV, and Matplotlib. The experiment demonstrated image reading, shape drawing, text insertion, color space conversion, pixel manipulation, image resizing, cropping, flipping, and saving.

---
