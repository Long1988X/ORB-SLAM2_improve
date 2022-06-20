[toc]

## 1 使用OpenCV 4.5 运行ORB-SLAM2

> 1 下载orb-slam2源码
>
> 2 安装OpenCV 4.5
>
> 3 安装第三方库Eigen、g2o、Pangolin、DBow2等
>
> 4 尝试编译，并解决头文件、OpenCV枚举变量未声明等问题；

## 2 ORB-SLAM2保存地图和加载地图

1. /home/pikachu/My_test/ORB-SLAM/ORB_SLAM2/src/Tracking.cc:255:38: note: suggested alternative: ‘CV_WRAP_AS’             cvtColor(mImGray,mImGray,CV_BGRA2GRAY);

   > BGRA2GRAY: 未声明的标识符
   >
   > 在Tracking.cc文件中添加：\#include <opencv2\imgproc\types_c.h>

2. /home/pikachu/My_test/ORB-SLAM/ORB_SLAM2/src/FrameDrawer.cc:75:24: error: ‘CV_GRAY2BGR’ was not declared in this scope         cvtColor(im,im,CV_GRAY2BGR);

   > “CV_GRAY2BGR”: 未声明的标识符
   >
   > 在FrameDrawer.cc文件中添加：\#include <opencv2\imgproc\types_c.h>

3. ‘CvMat’ was not declared in this scope

   > ```cpp
   > #include <opencv2/core/types_c.h>
   > ```