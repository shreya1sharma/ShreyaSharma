---
layout : page
title: Python tricks

---

1. Create a custom color map in matplotlib

```python
def generate_cmap(colors):
    values = range(len(colors))
    vmax = np.ceil(np.max(values))
    color_list = []
    for v, c in zip(values, colors):
        color_list.append( ( v/ vmax, c) )
    return LinearSegmentedColormap.from_list('custom_cmap', color_list)        


#Usage 1:   

cm  =  generate_cmap ([ 'moccasin', 'black', 'white' ]) #one color is assigned to one value in array
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
2. Making a video in OpenCV
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
