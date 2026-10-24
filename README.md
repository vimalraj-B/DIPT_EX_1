# Experiment 1 : Image Handling and Pixel Transformations Using OpenCV Assignment
### Developed By : VIMALRAJ B
### Register Number : 212224230304
### Aim :
To perform image handling and pixel transformations using OpenCV in Python, including image loading, displaying, drawing shapes, color space conversion, pixel manipulation, resizing, cropping, flipping, and saving images.

### Requirements :
- Python
- Anaconda prompt
- Jupyter Notebook
- OpenCV (`cv2`)
- Matplotlib
- Input image (`ex.jpg`)

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
img = cv2.imread('ex.jpg', cv2.IMREAD_COLOR)

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
image = cv2.imread('ex.jpg')

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
image = cv2.imread('ex.jpg') 

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
image = cv2.imread('ex.jpg') 

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
image = cv2.imread('ex.jpg') 

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
image = cv2.imread('ex.jpg')

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
image = cv2.imread('ex.jpg')

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
image = cv2.imread('ex.jpg')

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
image = cv2.imread('ex.jpg')

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
  
   <img width="279" height="329" alt="image" src="https://github.com/user-attachments/assets/3013876e-f388-4eac-b7bd-a32a6b62458e" />

* Draw a line from the top-left to the bottom-right of the image.

   <img width="273" height="326" alt="image" src="https://github.com/user-attachments/assets/0012faa1-8b7c-4596-9944-e889c446e2fa" />

* Draw a circle at the center of the image.

   <img width="283" height="329" alt="image" src="https://github.com/user-attachments/assets/80cc440b-0ae1-460f-a3e5-1aa41038c055" />

* Draw a rectangle around  the whole image

   <img width="288" height="332" alt="image" src="https://github.com/user-attachments/assets/9c30aaaa-fb65-4ca9-83fd-0d19a1ee6a4d" />

* Add the text "OpenCV Drawing" at the top-left corner of the image.

   <img width="274" height="328" alt="image" src="https://github.com/user-attachments/assets/762cdb9d-a480-4790-a02e-06d81af732be" />

* Convert the image from RGB to HSV and display it.

   <img width="280" height="326" alt="image" src="https://github.com/user-attachments/assets/94dbe7c7-3aca-4fc7-afc3-7fcb4bfb7b55" />

* Convert the image from RGB to GRAY and display it. 

   <img width="278" height="321" alt="image" src="https://github.com/user-attachments/assets/0cad5269-d60f-4289-9b21-0ccb7bb90d1b" />

* Convert the image from RGB to YCrCb and display it. 

   <img width="278" height="329" alt="image" src="https://github.com/user-attachments/assets/dbaed4e8-2367-430e-954c-49a46d8a16ec" />

* Convert the HSV image back to RGB and display it.

   <img width="283" height="329" alt="image" src="https://github.com/user-attachments/assets/be0feab0-1dc6-4a0f-97d0-ac22ea3b041f" />

* Access and print the value of the pixel at coordinates (100, 100) and Modify the color of the pixel at (200, 200) to white.

   <img width="295" height="325" alt="image" src="https://github.com/user-attachments/assets/57d1a21b-0eb4-4f08-9f26-bcdb8c0c77e0" />

* Resize the original image to half its size and display it.

   <img width="418" height="329" alt="image" src="https://github.com/user-attachments/assets/071ffc4e-b2c2-4cda-8fe5-441ca1d735d1" />

* Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.

   <img width="345" height="322" alt="image" src="https://github.com/user-attachments/assets/3a557d73-47a5-42a5-9f80-53f30b75e05e" />

* Flip the original image horizontally and display it. 

   <img width="278" height="324" alt="image" src="https://github.com/user-attachments/assets/d2a64eb5-21f3-40a0-a003-580c8f6a5a65" />

* Flip the original image vertically and display it.

   <img width="289" height="329" alt="image" src="https://github.com/user-attachments/assets/24536114-d6ba-4e9c-b63f-6d480845dac2" />


### Result

Thus, image handling and pixel transformations were implemented using Python and OpenCV. The experiment demonstrates image loading, drawing, color space conversion, pixel manipulation, resizing, cropping, flipping, and saving images successfully.


