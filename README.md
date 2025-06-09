# IMAGE-TRANSFORMATIONS

## Aim
To perform image transformation such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping using OpenCV and Python.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:
Import necessary libraries (NumPy, OpenCV, Matplotlib).

### Step2:
Read an image, convert it to RGB format, and display it using Matplotlib.Define translation parameters (e.g., shifting by 100 pixels horizontally and 200 pixels vertically).Perform translation using cv2.warpAffine().Display the translated image using Matplotlib.

### Step3:
Obtain the dimensions (rows, cols, dim) of the input image.Define a scaling matrix M with scaling factors of 1.5 in the x-direction and 1.8 in the y-direction.Perform perspective transformation using cv2.warpPerspective(), scaling the image by a factor of 1.5 in the x-direction and 1.8 in the y-direction.Display the scaled image using Matplotlib.

### Step4:
Define shear matrices M_x and M_y for shearing along the x-axis and y-axis, respectively.Perform perspective transformation using cv2.warpPerspective() with the shear matrices to shear the image along the x-axis and y-axis.Display the sheared images along the x-axis and y-axis using Matplotlib.

### Step5:
Define reflection matrices M_x and M_y for reflection along the x-axis and y-axis, respectively.Perform perspective transformation using cv2.warpPerspective() with the reflection matrices to reflect the image along the x-axis and y-axis.Display the reflected images along the x-axis and y-axis using Matplotlib.

### Step 6 :
Define an angle of rotation in radians (here, 10 degrees).Construct a rotation matrix M using the sine and cosine of the angle.Perform perspective transformation using cv2.warpPerspective() with the rotation matrix to rotate the image.Display the rotated image using Matplotlib.
### Step 7 :
Define a region of interest by specifying the desired range of rows and columns to crop the image (here, from row 100 to row 300 and from column 100 to column 300).Use array slicing to extract the cropped region from the input image.Display the cropped image using Matplotlib.


## Program:
```
Developed By: Udayakumar R
Register Number: 212222230163
```
### i)Image Translation
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tran.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()
rows,cols,dim=input_image.shape
M = np.float32([[1, 0, 100],[0, 1, 200],[0, 0, 1]])

translated_image = cv2.warpPerspective(input_image, M, (cols, rows))
plt.axis('off')
plt.imshow(translated_image)
plt.show()
```
### ii) Image Scaling
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tran.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

rows, cols, dim = input_image.shape 
M = np.float32([[1.5, 0, 0],[0, 1.8, 0],[0, 0, 1]])

scaled_img=cv2.warpPerspective (input_image, M, (cols*2, rows*2))
plt.imshow(scaled_img)
plt.show()
```
### iii)Image shearing
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tran.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

M_x = np.float32([[1, 0.5, 0],[0, 1 ,0],[0,0,1]])
M_y =np.float32([[1, 0, 0],[0.5, 1, 0],[0, 0, 1]])

sheared_img_xaxis=cv2.warpPerspective(input_image,M_x, (int(cols*1.5), int(rows *1.5)))
sheared_img_yaxis = cv2.warpPerspective(input_image,M_y,(int(cols*1.5), int(rows*1.5)))

plt.imshow(sheared_img_xaxis)
plt.show()

plt.imshow(sheared_img_yaxis)
plt.show()
```
### iv)Image Reflection
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tran.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

M_x= np.float32([[1,0, 0],[0, -1, rows],[0, 0, 1]])
M_y =np.float32([[-1, 0, cols],[ 0, 1, 0 ],[ 0, 0, 1 ]])
# Apply a perspective transformation to the image
reflected_img_xaxis=cv2.warpPerspective (input_image, M_x,(int(cols), int(rows)))
reflected_img_yaxis= cv2.warpPerspective (input_image, M_y, (int(cols), int(rows)))

                                         
plt.imshow(reflected_img_xaxis)
plt.show()

plt.imshow(reflected_img_yaxis)
plt.show()

```
### v)Image Rotation
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tran.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

angle=np.radians(10)
M=np.float32([[np.cos(angle),-(np.sin(angle)),0],[np.sin(angle),np.cos(angle),0],[0,0,1]])
rotated_img = cv2.warpPerspective(input_image,M,(int(cols),int(rows)))

plt.imshow(rotated_img)
plt.show()

```
### vi)Image Cropping
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tran.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

cropped_img= input_image[100:300,100:300]

plt.imshow(cropped_img)
plt.show()

```


## Output:
### i)Image Translation

![Screenshot 2024-03-12 134348](https://github.com/abinayasangeetha/IMAGE-TRANSFORMATIONS/assets/119393675/063467b5-a08b-4f3f-a836-ca41e71eb94f)

### ii) Image Scaling

![Screenshot 2024-03-12 134407](https://github.com/abinayasangeetha/IMAGE-TRANSFORMATIONS/assets/119393675/ae8be2a8-0a5a-44a3-8fa7-6ae2357f2a52)


### iii)Image shearing
![Screenshot 2024-03-12 134447](https://github.com/abinayasangeetha/IMAGE-TRANSFORMATIONS/assets/119393675/474d2048-df67-4c61-9649-12b7995e02d1)


### iv)Image Reflection
![Screenshot 2024-03-12 134502](https://github.com/abinayasangeetha/IMAGE-TRANSFORMATIONS/assets/119393675/d2d72622-7d45-43d0-8aaf-724cd35eb6ef)



### v)Image Rotation


![Screenshot 2024-03-12 134515](https://github.com/abinayasangeetha/IMAGE-TRANSFORMATIONS/assets/119393675/3680907a-45da-43ad-9a07-d807c8930273)


### vi)Image Cropping
![Screenshot 2024-03-12 134523](https://github.com/abinayasangeetha/IMAGE-TRANSFORMATIONS/assets/119393675/4bebd0fe-00e5-4cb1-99c4-d370e2c614d7)






## Result: 

Thus the different image transformations such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping are done using OpenCV and python programming.
