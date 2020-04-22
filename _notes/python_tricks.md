---
layout : page
title: Python tricks

---

<details>
<summary> Create a custom color map in matplotlib</summary>

```python
def generate_cmap(colors):
	values = range(len(colors))
    vmax = np.ceil(np.max(values))
    color_list = []
    for v, c in zip(values, colors):
    	color_list.append( ( v/ vmax, c) )
    
    return LinearSegmentedColormap.from_list('custom_cmap', color_list)        

#Usage 1:   

cm  =  generate_cmap ([ 'moccasin', 'black', 'white' ]) #one color is assigned to one integer value in array
plt.imshow(array, cmap = cm)
plt.show() 

#Usage 2: to create an image highlighting FP, FN, TP and TN

def assign_value_for_cmap(y_actual, y_pred):
    row, column = initial_shape
    color_map = np.zeros((row, column))
    for i in range(len(y_pred)): 
        x = locations[i][0]
        y = locations[i][1]
        if y_actual[i]==y_pred[i]==0:
           color_map[x,y]= 1
        if y_actual[i]==y_pred[i]==1:
           color_map[x,y]= 2
        if y_pred[i]==1 and y_actual[i]!=y_pred[i]:
           color_map[x,y]= 3
        if y_pred[i]==0 and y_actual[i]!=y_pred[i]:
           color_map[x,y]= 4
        return color_map

color_map = assign_value_for_cmap(y_actual, y_pred, locations) 
cm  =  generate_cmap ([ 'moccasin', 'black', 'white', 'green', 'red' ]) #one color is assigned to one value
plt.imshow(color_map, cmap = cm)
plt.show() 
```
</details>

<details>
<summary> Making a video in OpenCV </summary>
  
```python

#variables
image_folder = "enter the name of image folder"
video_name = "demo_video.avi"
fps = 1

output_folder= "enter the name of image folder"

files= sorted(os.listdir(image_folder))
images = [img for img in files if img.endswith(".png")]
frame = cv2.imread(os.path.join(image_folder, images[0]))
height, width, depth = frame.shape

fourcc= cv2.VideoWriter_fourcc(*'DIB ') #check codec and file extension very carefully
video= cv2.VideoWriter(video_name, fourcc, fps, (width, height))

for image in images:  
        video.write(cv2.imread(os.path.join(image_folder, image))) 

del images
cv2.destroyAllWindows()
video.release()
```
</details>

<details>
<summary> Unzip a directory</summary> 
	
```python
import zipfile
with zipfile.ZipFile(path_to_zip_file, 'r') as zip_ref:
    zip_ref.extractall(path_to_save_at)
```
</details>

<details>
<summary> Progress bar in python</summary> 
	
```python
from tqdm import tqdm
for i in tqdm(range(10)):
    print('hi')
```
</details>

<details>
<summary> Iterating over an iterator of unknown length using next()</summary> 
	
```python
# Python code to demonstrate 
# working of next() 
list1 = [1, 2, 3, 4, 5]  
# converting list to iterator 
list1 = iter(list1)  
print ("The contents of list are : ") 
# printing using next() 
# using default 
while (1) : 
    val = next(list1,'end') 
    if val == 'end': 
        print ('list end') 
        break
    else : 
        print (val) 
```
</details>

<details>
<summary> Creating patches from images</summary> 
	
```python
# over-lapping patches - 1) extract_patches_2d (single image), 2) Patch_Extractor (many images)
# https://scikit-learn.org/stable/modules/feature_extraction.html#image-feature-extraction

from sklearn.feature_extraction import image
patch_size = 64
patches = image.extract_patches_2d(arr, (patch_size, patch_size))
patches = image.PatchExtractor((patch_size, patch_size)).transform(arr)

# non- overlapping patches 
#method 1: blockfy (custom function)
def blockfy(a, p, q):
    '''
    Divides array a into subarrays of size p-by-q
    p: block row size
    q: block column size
    '''
    m = a.shape[0]  #image row size
    n = a.shape[1]  #image column size

    # pad array with NaNs so it can be divided by p row-wise and by q column-wise
    bpr = ((m-1)//p + 1) #blocks per row
    bpc = ((n-1)//q + 1) #blocks per column
    M = p * bpr
    N = q * bpc

    A = np.nan* np.ones([M,N])
    A[:a.shape[0],:a.shape[1]] = a

    block_list = []
    previous_row = 0
    for row_block in range(bpc):
        previous_row = row_block * p   
        previous_column = 0
        for column_block in range(bpr):
            previous_column = column_block * q
            block = A[previous_row:previous_row+p, previous_column:previous_column+q]

            # remove nan columns and nan rows
            nan_cols = np.all(np.isnan(block), axis=0)
            block = block[:, ~nan_cols]
            nan_rows = np.all(np.isnan(block), axis=1)
            block = block[~nan_rows, :]

            ## append
            if block.size:
                block_list.append(block)

    return block_list

# Usage:
patches = blockfy(train[i], patch_size, patch_size)

#method 2 : view_as_blocks (skimage function), comment out size assert error if patch size is not evenly divided
from sklearn.utils import view_as_blocks # https://scikit-image.org/docs/dev/api/skimage.util.html#skimage.util.view_as_blocks
patches = view_as_blocks(arr,(patch_size, patch_size))
```
