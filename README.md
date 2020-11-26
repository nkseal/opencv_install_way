# opencv_install
这里面有opencv的安装和配置方法

首先，我的OpenCV版本是release vc15 还有contribute vc16   
IDE是VS 2019和CLion
***
* ## 安装时的配置(vs)：
* ### release版
c++:
` https://blog.csdn.net/Smile_Bit_Seven/article/details/109509557  ` 
python:
`https://blog.csdn.net/qq_29519575/article/details/91398974`

* ### contribute版
**强烈建议操作前读完全过程！！！**
（由于咱们需要在cmake阶段加入额外的库，所以得把opencv重新从源码编译一遍！！！)

* **链接1：** ` https://blog.csdn.net/weijifen000/article/details/93377143 `  

在这个过程中，你如果报了could not find any instance of Visual Studio.的错，
请看：
` https://blog.csdn.net/diaodaa/article/details/106122943 `

另外，在VS里配属性不要按链接1里说的方法配，要按：
` https://blog.csdn.net/Smile_Bit_Seven/article/details/109509557 `
这里面的方法（指在视图里找其他窗口啥的）配
但内容还是按链接1里说的配
其中，附加依赖项不要按那个文件里说的配，咱们opencv版本不同所以库文件内容不同
要按下面的配：

```
opencv_calib3d450d.lib
opencv_ccalib450d.lib
opencv_core450d.lib
opencv_datasets450d.lib
opencv_dnn450d.lib
opencv_dnn_objdetect450d.lib
opencv_dpm450d.lib
opencv_face450d.lib
opencv_features2d450d.lib
opencv_flann450d.lib
opencv_fuzzy450d.lib
opencv_gapi450d.lib
opencv_hfs450d.lib
opencv_highgui450d.lib
opencv_imgcodecs450d.lib
opencv_imgproc450d.lib
opencv_img_hash450d.lib
opencv_line_descriptor450d.lib
opencv_ml450d.lib
opencv_objdetect450d.lib
opencv_optflow450d.lib
opencv_phase_unwrapping450d.lib
opencv_photo450d.lib
opencv_plot450d.lib
opencv_quality450d.lib
opencv_reg450d.lib
opencv_rgbd450d.lib
opencv_saliency450d.lib
opencv_shape450d.lib
opencv_stereo450d.lib
opencv_structured_light450d.lib
opencv_superres450d.lib
opencv_surface_matching450d.lib
opencv_text450d.lib
opencv_tracking450d.lib
opencv_video450d.lib
opencv_videoio450d.lib
opencv_videostab450d.lib
opencv_ximgproc450d.lib
opencv_xobjdetect450d.lib
opencv_xphoto450d.lib
opencv_bioinspired450d.lib
opencv_bgsegm450d.lib
opencv_aruco450d.lib

```
至此contribute版配置完成
***


* ## 如果你想用CLion也是可以的:
**但编译器不能用minGW或者其他啥的，必须是VS  
所以最好还是先配一遍VS再弄CLion**

* ### cmakelists写:
* #### release版
```cmake
#project name
PROJECT(opencv)

#requirement of cmake version
cmake_minimum_required(VERSION 3.17)

#set cmake standard
set(CMAKE_CXX_STANDARD 14)

#find required opencv
find_package(OpenCV REQUIRED)

#directory of opencv headers
include_directories(${OpenCV_INCLUDE_DIRS})

#directory of opencv library
link_directories(${OpenCV_LIBRARY_DIRS})

#name of executable file and path of source file
add_executable(opencv main.cpp)

#opencv libraries
target_link_libraries(opencv ${OpenCV_LIBS})

```
* #### contribute版
我还没搞......

***（还有一重要提示：
记得架构要先选X86点OK，再改为X64再点OK!!!
记得架构要先选X86点OK，再改为X64再点OK!!!
记得架构要先选X86点OK，再改为X64再点OK!!!
玄学呀）***


***
### 最后，给一段测试代码：


```C++
#include <iostream>
#include <opencv2/opencv.hpp>

using namespace std;
using namespace cv;

int main() {
    Mat src;
    //记得改成自己的路径!!!
    src = imread("E:\\OpenCV\\test_pictures\\Threshold.jpg");

    imshow("test", src);
    waitKey(0);
    
    return 0;
}
```
