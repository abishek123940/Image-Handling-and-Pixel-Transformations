# Experiment 1 : Image Handling and Pixel Transformations Using OpenCV Assignment
### Developed By : ABISHEK S
### Register Number : 212224240003
### Aim :
To perform image handling and pixel transformations using OpenCV in Python, including image loading, displaying, drawing shapes, color space conversion, pixel manipulation, resizing, cropping, flipping, and saving images.

### Requirements :
- Python
- Anaconda prompt
- Jupyter Notebook
- OpenCV (`cv2`)
- Matplotlib
- Input image (`image.jpeg`)

### Procedure :
1. Import the required libraries, OpenCV and Matplotlib.
2. Load the input image using `cv2.imread()`.
3. Display the original image using Matplotlib.
4. Draw a line, circle, rectangle, and text on the image using OpenCV functions.
5. Convert the image into RGB, HSV, grayscale, and YCrCb color spaces.
6. Access the pixel value at coordinate `(100, 100)` and modify the pixel at `(200, 200)` to white.
7. Resize the image to half its original dimensions.
8. Crop a region of interest from the image.
9. Flip the image horizontally and vertically.
10. Save the modified image using `cv2.imwrite()`.

### Program :
### Step1 : Load an image from your local directory and display it.

```python
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('bro.jpeg', cv2.IMREAD_COLOR)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('on')  # Removes axis ticks and labels
plt.show()
```

### Step2 :
* Draw a line from the top-left to the bottom-right of the image.
  
```python
# Load the image
image = cv2.imread('bro.jpeg')

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2) # cv2.line(image, start_point, end_point, color, thickness)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('on')  
plt.show()
```

* Draw a circle at the center of the image.

```python
# Load the image
image = cv2.imread('bro.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

img_rgb.shape

circle_img = cv2.circle(img_rgb,(270,200),150,(255,0,0),10) # cv2.circle(image, center, radius, color, thickness)

plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('on')  
plt.show()
```

* Draw a rectangle around  the whole image.

```python
# Load the image
image = cv2.imread('bro.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

img.shape

# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (10,10), (500, 600), (0, 0, 255), 10)  # cv2.rectangle(img,s_pt,e_pt,color,thickness)

plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('on')  
plt.show()
```

* Add the text "OpenCV Drawing" at the top-left corner of the image.

```python
# Load the image
image = cv2.imread('bro.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (0,0,0), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('on')  
plt.show()
```

### Step3 :
* Convert the image from RGB to HSV and display it.

```python
image = cv2.imread('bro.jpeg')

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("on")
```

```python
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

plt.imshow(image_hsv)
```

* Convert the image from RGB to GRAY and display it.

```python
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("on")
```

* Convert the image from RGB to YCrCb and display it.

```python
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("on")
```

* Convert the HSV image back to RGB and display it.

```python
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("on")
```

### Step4 : 
* Access and print the value of the pixel at coordinates (100, 100). 
* Modify the color of the pixel at (200, 200) to white.

```python
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[100:420, 100:420] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("on")
plt.show()
```

### Step5 : Resize the original image to half its size and display it.

```python
# Load the image
image = cv2.imread('bro.jpeg')

image.shape

# Resize the image to half its size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))  # (new_width, new_height)
# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

resized_image_rgb.shape

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("on")
plt.show()
```

### Step6 : Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.

```python
# Load the image
image = cv2.imread('bro.jpeg')

image.shape

# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349

# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("on")
plt.show()
```

### Step7:
* Flip the original image horizontally and display it. 

```python
# Load the image
image = cv2.imread('bro.jpeg')

# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("on")
```

* Flip the original image vertically and display it.

```python
# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("on")
```

### Output

* Original image display
  
   <img width="338" height="254" alt="image" src="https://github.com/user-attachments/assets/95c453a6-2d2b-4dbd-b46e-16fdc3365092" />

* Draw a line from the top-left to the bottom-right of the image.

    <img width="343" height="254" alt="image" src="https://github.com/user-attachments/assets/68fc47ae-dcc6-470f-9a0b-55478cd055ce" />

* Draw a circle at the center of the image.

     <img width="317" height="251" alt="image" src="https://github.com/user-attachments/assets/56c6bbc0-7d91-4be1-8c45-cabe063f3f83" />

* Draw a rectangle around  the whole image

     <img width="359" height="257" alt="image" src="https://github.com/user-attachments/assets/10c245a8-309a-4bff-b620-89b2a07cb21e" />

* Add the text "OPENCV WITH TEXT" at the top-left corner of the image.

     <img width="356" height="261" alt="image" src="https://github.com/user-attachments/assets/d634148d-75c1-4a60-8726-fb478000fd56" />

* Convert the image from RGB to HSV and display it.

    <img width="443" height="268" alt="image" src="https://github.com/user-attachments/assets/1cdee227-7c03-402f-85c1-b4ad517e21c6" />

* Convert the image from RGB to GRAY and display it. 

     <img width="422" height="269" alt="image" src="https://github.com/user-attachments/assets/a97c43ce-be81-448a-88f4-6cfd04c2817c" />

* Convert the image from RGB to YCrCb and display it. 

     <img width="314" height="410" alt="download" src="https://github.com/user-attachments/assets/29838e3e-9686-496f-a76c-26fdb48acd9d" />

* Convert the HSV image back to RGB and display it.

     <img width="314" height="410" alt="download" src="https://github.com/user-attachments/assets/395c58b2-f354-44cb-92d7-24723cfc0b8a" />

* Access and print the value of the pixel at coordinates (100, 100) and Modify the color of the pixel at (200, 200) to white.

     <img width="314" height="410" alt="download" src="https://github.com/user-attachments/assets/14a7689d-627c-4f6e-a077-c3269f306cd7" />

* Resize the original image to half its size and display it.

     <img width="493" height="410" alt="download" src="https://github.com/user-attachments/assets/e105c4c2-9c5e-4f17-87eb-26f16fac5c86" />

* Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.

<img width="389" height="410" alt="download" src="https://github.com/user-attachments/assets/165a4576-2e1a-43b9-be4a-b6eb32b57e8c" />

* Flip the original image horizontally and display it. 

<img width="314" height="410" alt="download" src="https://github.com/user-attachments/assets/8bc213cd-4a9e-4d90-bbe5-c2854208a2b5" />

* Flip the original image vertically and display it.

     <img width="314" height="410" alt="download" src="https://github.com/user-attachments/assets/ed9bb306-26ec-46bb-b2b9-c151109093a4" />


### Result

Thus, image handling and pixel transformations were implemented using Python and OpenCV. The experiment demonstrates image loading, drawing, color space conversion, pixel manipulation, resizing, cropping, flipping, and saving images successfully.
