# OpenCV

#### 安装环境

Z：下载安装Anaconda，该软件中安装以下环境：

- TensorFlow
- openCV
- notebook

#### openCV

Z：读取显示图片代码如下：

```python
import cv2
//图片读取
img = cv2.imread('Demo.jpg',1)
//图片显示
cv2.imshow('image',img)
cv2.waitKey(0)
```

Z：图片写入代码如下：

```python
import cv2
img = cv2.imread('Demo.jpg',1)
cv2.imwrite('image1.jpg',img)
```

Z：设定指定的质量输出：

jpge

```python
import cv2
img = cv2.imread('image0.jpg',1)
cv2.imwrite('imageTest.jpg',img,[cv2.IMWRITE_JPEG_QUALITY,50])
```

png

```python
import cv2
img = cv2.imread('image0.jpg',1)
cv2.imwrite('imageTest.png',img,[cv2.IMWRITE_PNG_COMPRESSION,0])
```

M：要怎么在图片上进行像素操作呢？

Z：如下代码

```python
import cv2
# 读取图片
img = cv2.imread('image0.jpg',1)
# 获取指定像素点BGR颜色
(b,g,r) = img[100,100]
print(b,g,r)# bgr
#10 100 --- 110 100
# 循环给像素点赋值蓝色
for i in range(1,100):
    img[10+i,100] = (255,0,0)
# 显示图片    
cv2.imshow('image',img)
cv2.waitKey(0) 
```
