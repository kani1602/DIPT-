# Image-Handling-and-Pixel-Transformations-Using-OpenCV
## AIM:
Write a Python program using OpenCV that performs the following tasks:

Read and Display an Image.
Adjust the brightness of an image.
Modify the image contrast.
Generate a third image using bitwise operations.
## Software Required:
Anaconda - Python 3.7
Jupyter Notebook (for interactive development and execution)
## Algorithm:
Step 1:
Load an image from your local directory and display it.

Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.
Display the original, brighter, and darker images.

Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).
Display the original, lower contrast, and higher contrast images.

Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
### Name: KANISHKA V

### Register Number: 212224100030
## Program:
Step1:
Load an image from your local directory and display it.
```
import cv2
import matplotlib.pyplot as plt
img = cv2.imread('dog.png', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()
```
Step2:
o Draw a line from the top-left to the bottom-right of the image.

o Draw a circle at the center of the image. 

o Draw a rectangle around a specific region of interest in the image. 

o Add the text "OpenCV Drawing" at the top-left corner of the image.
```
# Load the image
image = cv2.imread('dog.png')
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

# Draw cross lines from corner to corner
h, w = img_rgb.shape[:2]
line_img = cv2.line(img_rgb.copy(), (0, 0), (w - 1, h - 1), (255, 0, 0), 3)
line_img = cv2.line(line_img, (w - 1, 0), (0, h - 1), (255, 0, 0), 3)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()
```
Draw a circle at the center of the image.
```
# Load the image
image = cv2.imread('dog.png') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

# Draw a circle in the middle of the image
h, w = img_rgb.shape[:2]
circle_img = cv2.circle(img_rgb.copy(), (w // 2, h // 2), min(h, w) // 6, (255, 0, 0), 5)
plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
```
Draw a rectangle around  the whole image
```
# Load the image
image = cv2.imread('dog.png') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape

# Draw a rectangle around the image
h, w = img_rgb.shape[:2]
rectangle_img = cv2.rectangle(img_rgb.copy(), (5, 5), (w - 6, h - 6), (0, 0, 255), 5)
plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()
```
Add the text "DOG" at the top-left corner of the image.
```
# Load the image
image = cv2.imread('dog.png') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb.copy(), "DOG", (30, 100), cv2.FONT_HERSHEY_SIMPLEX, 3, (255, 255, 255), 5)
plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
```
Step3:
o Convert the image from RGB to HSV and display it.
    
o Convert the image from RGB to GRAY and display it. 

o Convert the image from RGB to YCrCb and display it. 
    
o Convert the HSV image back to RGB and display it.
```
# Load the image
image = cv2.imread('dog.png')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
# Original RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
```
```
# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
# HSV Image
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
```
```
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
```
```
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
```
```
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
```
Step4:
o Access and print the value of the pixel at coordinates (100, 100). 

o Modify the color of the pixel at (200, 200) to white.
```
# Modify a block of pixels (300x300) to white at the center
modified_img = img_rgb.copy()
h, w = modified_img.shape[:2]
cy, cx = h // 2, w // 2
modified_img[max(0, cy-100):min(h, cy+100), max(0, cx-100):min(w, cx+100)] = [255, 255, 255]

# Display the modified image
plt.imshow(modified_img)
plt.title("Image with 300x300 White Block")
plt.axis('off')
plt.show()
```
Step5:
o Resize the original image to half its size and display it.
```
# Load the image
image = cv2.imread('dog.png')
image.shape
# Resize the image to half its size
h, w = image.shape[:2]
resized_image = cv2.resize(image, (w // 2, h // 2))  # (new_width, new_height)
# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape
# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```
Step6:
o Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.
```
# Load the image
image = cv2.imread('dog.png')
image.shape
# Crop a 300x300 region from the center of the image
h, w = img_rgb.shape[:2]
cy, cx = h // 2, w // 2
roi = img_rgb[max(0, cy-150):min(h, cy+150), max(0, cx-150):min(w, cx+150)]
# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = roi
# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```
Step7:
o Flip the original image horizontally and display it. 

o Flip the original image vertically and display it.
```
# Load the image
image = cv2.imread('dog.png')
# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)
# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)
# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
```
```
# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)
# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)
# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
```
Step8:
o Save the final modified image to your local directory.
## Output:
### Original Image
<img width="643" height="457" alt="image" src="https://github.com/user-attachments/assets/3b540915-cd4b-47f2-80a9-50457326446e" />


### Image with Line
<img width="645" height="470" alt="image" src="https://github.com/user-attachments/assets/dc5ce819-a45b-4f47-b489-7b5ea3738c7c" />


### Image with Circle
<img width="641" height="467" alt="image" src="https://github.com/user-attachments/assets/924507cb-3022-4f31-8548-1b8a22f9fa1e" />


### Image with Rectangle
<img width="642" height="463" alt="image" src="https://github.com/user-attachments/assets/2cef884c-3df4-42a7-be0f-e43593118c76" />


### Image with Text
<img width="645" height="461" alt="image" src="https://github.com/user-attachments/assets/ca01ea62-e82c-47c6-acdf-baa07465c410" />



### Original RGB Image
<img width="642" height="452" alt="image" src="https://github.com/user-attachments/assets/b8817a4e-7e1c-4a27-bdab-f99df045ba3e" />


### HSV Image
<img width="638" height="462" alt="image" src="https://github.com/user-attachments/assets/b3b820ed-9890-4cc8-ba2d-bb65d0264eab" />


### Grayscale Image
<img width="642" height="463" alt="image" src="https://github.com/user-attachments/assets/85ce1a68-cfc1-4191-a459-ddca81a26f4a" />


### YCrCb Image
<img width="642" height="457" alt="image" src="https://github.com/user-attachments/assets/8ae0c1ee-2f0b-47f5-9684-ee3aba92cfe0" />


### HSV to RGB Image
<img width="643" height="457" alt="image" src="https://github.com/user-attachments/assets/c7275cda-dd0c-4ff4-899f-67ab4fba97ec" />


### Image with 300x300 White Block
<img width="642" height="462" alt="image" src="https://github.com/user-attachments/assets/a031e907-8e3d-403d-b03f-5ed11ca81643" />


### Resized Image(Half Size)
<img width="640" height="462" alt="image" src="https://github.com/user-attachments/assets/7648ba91-5fb3-4b6e-988e-5a129cf94763" />


### Cropped Region of Interest (ROI)
<img width="487" height="507" alt="image" src="https://github.com/user-attachments/assets/467b91b9-0bc7-457f-9c69-bd11bbfeb6d2" />


### Flipped Horizontally
<img width="641" height="463" alt="image" src="https://github.com/user-attachments/assets/5b348115-3925-46cb-b4a1-7bef2ff29c01" />



### Flipped Vertically
<img width="642" height="467" alt="image" src="https://github.com/user-attachments/assets/4098a133-bc11-4e2d-b5c2-5c230887d6e2" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
