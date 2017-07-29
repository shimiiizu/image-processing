# image-processing
//************************
//openCV練習用のプロジェクト
//2017.7.27
//
//一応成功している
//**************************

#include "stdafx.h"
#include "opencv2\\opencv.hpp"
#include<math.h>

#ifdef _DEBUG
    //Debugモード
    #pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_core220d.lib") 
    #pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_imgproc220d.lib")
    #pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_highgui220d.lib") 
    #pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_objdetect220d.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_ml220d.lib") 
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_features2d220d.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_video220d.lib") 
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_calib3d220d.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_flann220d.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_contrib220d.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_legacy220d.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_gpu220d.lib") 
#else
    //Releaseモード
    #pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_core220.lib")  
    #pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_imgproc220.lib")
    #pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_highgui220.lib")
    #pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_objdetect220.lib") 
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_ml220.lib") 
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_features2d220.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_video220.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_calib3d220.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_flann220.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_contrib220.lib") 
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_legacy220.lib")
    //#pragma comment(lib,"C:\\OpenCV2.2\\lib\\opencv_gpu220.lib")
#endif

void CBGR( IplImage *img );//****< BGR入れ替え処理 >**** 

int main()
{
	IplImage *Image = cvLoadImage( "画像/入力画像.tif",CV_LOAD_IMAGE_ANYDEPTH | CV_LOAD_IMAGE_ANYCOLOR );
	CBGR(Image);cvSaveImage("画像/出力画像3.bmp",Image);

	return 0;
}


//****< BGR入れ替え処理 >**** 
void CBGR( IplImage *img )
{
		int x;
		//画素値のx座標　画素値のy座標

		int X = img->width, Y = img->height;
		//画像の横長X　画像の縦長Y

		uchar p[4];
		//画素値を入れる配列/

		int cnt;
		cnt=0;
		
		int startx; 
		int endx;


		//解析範囲を指定		
		startx = 100;
		endx = 200;

		for( x = startx; x < endx; x++)
		{

//(1/)----< 入力画像から画素値を読み込む >----

			p[0] = img -> imageData[img->widthStep* 0 + x*3 ];     //B（青色）
			p[1] = img -> imageData[img->widthStep* 0 + x*3 + 1 ]; //G（緑色）
			p[2] = img -> imageData[img->widthStep* 0 + x*3 + 2 ]; //R（赤色）

//(/1)---------------------
				cout <<"ピクセル位置 : x= "<<x<< " B= "<< int(p[0]) << " G= "<< int(p[1])<< " R= "<< int(p[2])<< endl;
				
				cnt = cnt +1;

//(3/)/----------< 出力画像を入れ込む >---------------
			/*
			img -> imageData[img->widthStep* y + x*3 ]     = p[2]/2;  //Bへ代入
			img -> imageData[img->widthStep* y + x*3 + 1 ] = p[0]/2;  //Gへ代入
			img -> imageData[img->widthStep* y + x*3 + 2 ] = p[1]/2;  //Rへ代入 
			*/
//(3/)--------------------------------

		}


	cout<<"ピクセル数は全部で"<<cnt<<"です"<< endl;
	cout<<"X="<<X<<endl;
	cout<<"Y="<<Y<<endl;
	
	system("pause");

}
 
