<div>
    <h1> Fubon E-Bank Captcha Solver 
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/consultant.png" width = 30 height = 30> 
</div>

> This project aims to solve the captcha image on Fubon EBank Website 

> Note: This project is for academic only, any illegal behavior should be prevented

## Captcha Image Scrapped
To download the captcha image from the website, we make use of Selenium to extract the captcha images from the website. We first navigate to the website logging area. Next, we download the captcha image then save it as base64 code. Then we decode base64 code to transform it back to captcha image. So we could get a captcha image like this.

<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/image1.jpg" width = 300 height = 60>
</p>

## Create Training Set
Next, I scrapped several images to create a training set. After checking these captcha images, we could find out that most of the numbers do not overlap with each other. Therefore, my strategy is to separate each number from the training set to serve as the training image. That is, I would solve the captcha image one-by-one. To do this, I performed some image processing techniques and extrated every number from the captcha image. The flowchart shows step-by-step implementation to segment the numbers in the captcha image.

<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/messageImage_1676176378723.jpg" width = 1000 height = 250>
</p>


I performed image segmentation on several captcha images. Eventually I got 465 training image for me to predict the captcha image. You could view and download all <a href = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/training%20set/training%20image.rar">training image</a> and its <a href = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/training%20set/train%20label.csv">label</a>.

## Predicting
Next, I performed KNN to solve the captcha image. I have 196 testing image and 465 segmented training image in total. To decide how many neighbors to use in KNN, I would try on the first 50 image and loop over $k = 1$ to $k = 20$ then check the accuracy I could get under different value of $k$. The plot here is the accuracy I got under different value of $k$.



<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/messageImage_1676176771556.jpg" width = 400 height = 300>
</p>

From the plot we could observe that the accuracy would decrease as $k$ increases. Therefore, the best classifier would be 1-NN. As a result, I chose 1-NN classifier to be my captcha solver. Then I use the training set along with 1-NN classifier to test all images in testing set, you could find all <a href = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/testing%20set/testing%20image.rar">testing image</a> and its <a href = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/testing%20set/test%20label.xlsx">label</a>. As a result, I successfully solved **169 captcha images out of 196**, reaching to a **86% accuracy**. 
    
## Adjustment
To work on a better result, let's check why I failed to predict some of the captcha image. Below is a plot which 1-NN classifier failed to predict. The title of every image was the predicting result gave out by 1-NN classifier. For those image that do not have title means there was some problems when performing image segmentation, my goal here is to fix this issue.
    
<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/messageImage_1676191314940.jpg" width = 800 height = 300>
</p>
    
So let's check why the image segmentation fails to work at some of the images.

<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/messageImage_1676191600189.jpg" width = 400 height = 100>
</p>    
    
Here, we could clearly see that the problem is caused by the bounding box. When two numbers are too close to each other, then the object detection method would recognize two numbers as a same object. Nevertheless, this issue could be solved simply by dividing the bounding box into half. Although there would be some redundant area in the bounding box, it would not affect the result gave out by the classifier. That is, the adjusted image would be like this
   
<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/messageImage_1676191999372.jpg" width = 400 height = 100>
</p>  
 
After the adjustement, I successfully predict **171 captcha images out of 196**. Though it might not be a significant increase, it helps me solve a potential problem which may occur when solving the captcha.  
    
## Result
After the modification, I use my segmented training image along with the 1-NN classifier to test how well my method perfomed. Because it's difficult to test the method online, I created a simple GUI and check whether the predicting result is correct. After testing on 1130 captcha images, this method is able to solve 960 of them, which **reaches a 85% accuracy**.

<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/predict%20result.jpg" width = 700 height = 350>
</p>      

## Conclusion
This is a simple project I've done during I was affected by COVID-19 (`Definitely Suffering🤒`). Although the method I used is not really complicated, it is useful when applying to this kind of captcha image. Hope this repo could help someone who needs it 🐳    



## Link

To view complete python code in this project, click <a href = "https://wavelolz.github.io/Fubon-Ebank-Captcha-Solver/Fubon%20E-Bank%20Captcha%20Solver.html">  HERE </a> ◀️◀️◀️◀️◀️◀️    
    
To try on the captcha solver system yourself, click <a href = "https://drive.google.com/file/d/1uCpXmX3K2gVnnUv3dltZ0EXbZ4y9dLS4/view?usp=share_link">  HERE </a> ◀️◀️◀️◀️◀️◀️
    


