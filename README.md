<div>
    <h1> Fubon E-Bank Captcha Solver 
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/consultant.png" width = 30 height = 30> 
</div>
# This project aims to solve the captcha image on Fubon EBank Website 
# Note: This project is for academic only, any illegal behavior should be prevented

## Captcha Image Scrapped
To download the captcha image from the website, we make use of Selenium to extract the captcha image from the website. We first navigate to the website logging area. Next, we download the captcha image then save it as base64 code. Then we decode base64 code to transform it back to captcha image. So we could get a captcha image like this.

<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/image1.jpg" width = 300 height = 60>
</p>

## Create Training Set
Next, I scrapped several images to create a training set. After checking the captcha image, we could find out that most of the numbers do not overlap with each other. Therefore, my strategy is to separate each number from the training set to serve as the training image. That is, I would solve the captcha image one-by-one. To do this, I performed some image processing techniques and extrated every number from the captcha image. The flowchart shows step-by-step implementation to segment the numbers in the captcha image.

<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/messageImage_1676176378723.jpg" width = 1000 height = 300>
</p>


So I perform image segmentation on several captcha image. Eventually I got 465 training image for me to predict the captcha image.

## Predicting
Next, I perform KNN to solve the captcha image. I have 196 testing image and 465 segmented training image in total. To decide how many neighbor to use in KNN, I would try on the first 50 image and loop over $k = 1$ to $k = 20$ and check the accuracy I could get under different value of $k$. The plot here is the accuracy I got under different value of $k$.



<p align = "center">
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/messageImage_1676176771556.jpg" width = 400 height = 300>
</p>




## For a thorough contents, please visit this link

<div>
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/down-arrow%20(1).png" width = 25 height = 25>
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/down-arrow%20(1).png" width = 25 height = 25>
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/down-arrow%20(1).png" width = 25 height = 25>
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/down-arrow%20(1).png" width = 25 height = 25>
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/down-arrow%20(1).png" width = 25 height = 25>
    <img src = "https://github.com/wavelolz/Fubon-Ebank-Captcha-Solver/blob/main/picture/down-arrow%20(1).png" width = 25 height = 25>
</div>

<a href = "https://wavelolz.github.io/Fubon-Ebank-Captcha-Solver/Fubon%20E-Bank%20Captcha%20Solver.html"> Fubon E-Bank Captcha Solver </a>
