#include<opencv2/core/core.hpp>
#include<opencv2/highgui/highgui.hpp>
#include<opencv2/imgproc/imgproc.hpp>
#define WINDOW_WIDTH 600
using namespace cv;
//--------------------------------------drawellipse----------------
//描述：自定义绘制函数
//------------------------------------------------------------------

void DrawEllipse(Mat img, double angle)
{
	int thickness = 2;
	int lineType = 8;

	ellipse(img,
		Point(WINDOW_WIDTH / 2, WINDOW_WIDTH / 2),
		Size(WINDOW_WIDTH / 4, WINDOW_WIDTH / 16),
		angle,
		0, 360,
		Scalar(255, 129, 0),
		thickness,
		lineType);


}

//-------------------------------------------------------------------------------
//描述：自定义的绘制函数
//-------------------------------------------------------------------------------
void DrawFilledCircle(Mat img, Point center)
{
	int thickness = -1;
	int LineType = -8;

	circle(img,
		center,
		WINDOW_WIDTH / 32,
		Scalar(0, 0, 255),
		thickness,
		LineType);
}


//-----------------------------------------------------------------------
//描述：
//-----------------------------------------------------------------------
void DrawLine(Mat img, Point start, Point end)
{
	int thickness = 2;
	int lineType = 8;
	line(img,
		start,
		end,
		Scalar(0, 0, 0),
		thickness,
		lineType);
}
#define WINDOW_NAME1 "【绘制图1】"
#define WINDOW_NAME2 "【绘制图2】"
int main()
{
	//创建空白mat图像
	Mat atomImage = Mat::zeros(WINDOW_WIDTH, WINDOW_WIDTH, CV_8UC3);
	Mat rookImage = Mat::zeros(WINDOW_WIDTH, WINDOW_WIDTH, CV_8UC3);
    //创建化学中的原子示意图

	//【1.2】再绘制出椭圆
	DrawEllipse(atomImage, 90);
	DrawEllipse(atomImage, 0);
	DrawEllipse(atomImage, 45);
	DrawEllipse(atomImage, -45);

	//再绘制出圆心
	DrawFilledCircle(atomImage, Point(WINDOW_WIDTH / 2, WINDOW_WIDTH / 2));
	namedWindow("name111", WINDOW_NORMAL);
	imshow("name111", atomImage);
	//moveWindow(WINDOW_NAME1, 0, 200);


	waitKey(0);
	return (0);


}





