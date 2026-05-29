### Image-Handling-and-Pixel-Transformations-Using-OpenCV
## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** [Your Name Here]  
- **Register Number:** [Your Register Number Here]

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread(r"WhatsApp Image 2026-04-28 at 2.38.24 PM.jpeg", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 2. Print the image width, height & Channel.
```python
img.shape
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img_rgb)
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite("Eagle.png", img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img = cv2.imread("Eagle.png")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img_rgb)
plt.show()
img.shape
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
plt.imshow(crop)
plt.title("Cropped Region")
plt.axis("off")
plt.show()

crop.shape
```

#### 8. Resize the image up by a factor of 2x.
```python
res = cv2.resize(crop, (400, 400))
```

#### 9. Flip the cropped/resized image horizontally.
```python
flip = cv2.flip(res, 1)

plt.imshow(flip)
plt.title("Flipped Horizontally")
plt.axis("off")
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
img = cv2.imread(r"C:\Users\admin\Downloads\WhatsApp Image 2026-04-28 at 2.38.24 PM.jpeg", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = cv2.putText(img_rgb, "Eagle Image", (200, 700),
                   cv2.FONT_HERSHEY_SIMPLEX, 1,
                   (255, 255, 255), 2)

plt.imshow(text)
plt.title("New Image")
plt.show()
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
img = cv2.imread(r"WhatsApp Image 2026-04-28 at 2.38.24 PM.jpeg", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

rcol = (255, 0, 255)

# Correct rectangle around eagle
cv2.rectangle(img_rgb, (200, 30), (550, 450), rcol, 4)
```

#### 13. Display the final annotated image.
```python
plt.figure(figsize=(8,6))
plt.imshow(img_rgb)
plt.title("Annotated Image")
plt.axis("on")
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```python

img = cv2.imread(r"WhatsApp Image 2026-04-28 at 2.38.24 PM.jpeg", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 15. Adjust the brightness of the image.
```python
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img_rgb, m)
img_darker = cv2.subtract(img_rgb, m)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(img_darker)
plt.title("Darker Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(img_brighter)
plt.title("Brighter Image")
plt.axis("off")

plt.show()
```

#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2

# Apply contrast
img_higher1 = cv2.multiply(img_rgb.astype("float32"), matrix1)
img_higher2 = cv2.multiply(img_rgb.astype("float32"), matrix2)

# Convert back to uint8
img_higher1 = np.clip(img_higher1, 0, 255).astype("uint8")
img_higher2 = np.clip(img_higher2, 0, 255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(10,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(img_higher1)
plt.title("Higher Contrast (1.1x)")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(img_higher2)
plt.title("Higher Contrast (1.2x)")
plt.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(img)

plt.figure(figsize=(10,5))

plt.subplot(1,3,1)
plt.imshow(b, cmap='gray')
plt.title("Blue Channel")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(g, cmap='gray')
plt.title("Green Channel")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(r, cmap='gray')
plt.title("Red Channel")
plt.axis("off")

plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_rgb = cv2.merge([r, g, b])

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")

plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)

plt.figure(figsize=(10,5))

plt.subplot(1,3,1)
plt.imshow(h, cmap='gray')
plt.title("Hue Channel")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(s, cmap='gray')
plt.title("Saturation Channel")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(v, cmap='gray')
plt.title("Value Channel")
plt.axis("off")

plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.merge([h, s, v])
merged_rgb_from_hsv = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB)

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(merged_rgb_from_hsv)
plt.title("Merged HSV Image")
plt.axis("off")

plt.show()
```

## Output:
- **i)** 1) Print Image Width, Height & Channels
<img width="130" height="33" alt="image" src="https://github.com/user-attachments/assets/93cb19de-4a6b-4ad7-9b74-f52c406b6fa6" />

- **i)** 2) Display the Image
- <img width="529" height="418" alt="download" src="https://github.com/user-attachments/assets/2494f756-53ce-4ac8-bf83-b1fde716a07a" />

- **i)** 3) Save the Image as PNG
- <img width="84" height="28" alt="image" src="https://github.com/user-attachments/assets/c42ef042-ecfa-4ba3-8a0c-e097012e94f0" />

- **i)** 4) Display the Colour Image & Shape
-<img width="529" height="418" alt="download" src="https://github.com/user-attachments/assets/9d47a02e-da70-4298-87bb-5db1b5544301" />
-<img width="439" height="409" alt="download" src="https://github.com/user-attachments/assets/bce94bd3-669b-42fd-ba5f-7ec945c6d8b0" />
-<img width="150" height="43" alt="image" src="https://github.com/user-attachments/assets/5d883c6d-8ee6-4687-a6d0-b2e84b39fccd" />


- **i)** 6) Flip the Image Horizontally
<img width="389" height="409" alt="download" src="https://github.com/user-attachments/assets/7df8047e-847b-401c-adee-e070f1249930" />

- **i)** 7)Add Text to Image
<img width="155" height="39" alt="image" src="https://github.com/user-attachments/assets/19db0ebe-c302-4691-b7bb-f33b7e9b637e" />

- **i)** 8) Draw Rectangle
- <img width="344" height="708" alt="image" src="https://github.com/user-attachments/assets/b53b882b-10d5-4425-98f4-485430e9b68d" />

- **i)** 9) Display the final annotated image
- <img width="647" height="526" alt="download" src="https://github.com/user-attachments/assets/15b55aaf-48ed-44ff-a2df-e0f3ab218a30" />

- **i)** 10) Display the images (Original, Darker, Brighter)

- <img width="794" height="218" alt="download" src="https://github.com/user-attachments/assets/69d169f1-21df-4c16-9eeb-7a7b7b7247de" />

- **i)** 11) Display the images (Original, Lower Contrast, Higher Contrast)
- <img width="794" height="218" alt="download" src="https://github.com/user-attachments/assets/fb822d51-b418-4995-ba64-1376d1242457" />

- **i)** 12)Split the image into B, G, R channels
- <img width="794" height="218" alt="download" src="https://github.com/user-attachments/assets/cae89766-071a-45f9-85df-3c9cb3770e4e" />
- <img width="794" height="315" alt="download" src="https://github.com/user-attachments/assets/2516108d-ea71-470b-bc59-13721c880f1a" />
- **i)** 12) Split into H, S, Vc
- 
-<img width="794" height="218" alt="download" src="https://github.com/user-attachments/assets/5369463a-55ba-4284-9d61-001e203924bb" />
- **i)** 12) Merge H, S, V and display with original

<img width="794" height="315" alt="download" src="https://github.com/user-attachments/assets/1e90759a-b85f-4ae8-8130-56f09c726c1d" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

