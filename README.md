## NAME:SHARVESHWARAN M
## REG NO:212224240150
# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

## Program:
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
img=cv2.imread("0.jpg")
plt.imshow(img[:,:,::-1]);plt.title("Face");plt.axis("off")
```
<img width="735" height="525" alt="image" src="https://github.com/user-attachments/assets/0f794587-118c-4ad9-952a-a204f700e98a" />

```
img.shape
```

```
glass = cv2.imread("glass.png",-1)
plt.imshow(glass[:,:,::-1]);plt.title("glass");plt.axis("on")
```
<img width="822" height="360" alt="image" src="https://github.com/user-attachments/assets/8c4f3bca-1d81-4584-8c0e-a65157e7a32f" />

```
glass = cv2.resize(glass,(190,50))
print("image Dimension ={}".format(glass.shape))
```

```
glassBGR = glass[:,:,0:3]
glassMask = glass[:,:,3]
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask,cmap='gray');plt.title('Sunglass Alpha channel');
```
<img width="1306" height="225" alt="image" src="https://github.com/user-attachments/assets/f379f726-5e52-4164-b25c-e1f34fbe2c7e" />

```
faceWithGlass = img.copy()
faceWithGlass[160:210,115:305]=glassBGR
plt.imshow(faceWithGlass[...,::-1])
```

<img width="617" height="452" alt="image" src="https://github.com/user-attachments/assets/20a8dcc8-e6f0-4aee-a0d7-6c704fb6d92e" />

```
glassM = cv2.merge((glassMask,glassMask,glassMask))
glassM = np.uint8(glassM/255)
faceWithGlassesArithmetic = img.copy()
eyeROI= faceWithGlassesArithmetic[160:210,115:305]
maskedEye = cv2.multiply(eyeROI,(1-  glassM ))
maskedGlass = cv2.multiply(glassBGR,glassM)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
```
<img width="1385" height="197" alt="image" src="https://github.com/user-attachments/assets/3a16e122-89eb-4bcf-add3-4618e5e60fa7" />

```
faceWithGlassesArithmetic[160:210,115:305]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(img[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");
```

## Output:
<img width="1257" height="662" alt="image" src="https://github.com/user-attachments/assets/786d82c5-3939-4e24-bd9e-30e04714656d" />


## RESULT:
 Thus Adding Sunglasses to Your Passport Photo Using OpenCV is done successfully.
