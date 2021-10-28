# 1、需要安装pycuda
`pip3 install pycuda`

# 2、将tensorrtx/yolov5/gen_wts.py复制到之前（上面的第5步）你下载的yolov5文件夹中。如果你上一步没有下载，也可以现在下载
`git clone https://github.com/ultralytics/yolov5.git`\
`https://github.com/wang-xinyu/tensorrtx/tree/yolov5-v5.0`下载tensorRTx

# 3、下载官方的权重文件'yolov5s.pt'
`wget https://github.com/ultralytics/yolov5/releases/download/v5.0/yolov5s.pt`\
**注意: yolov5s.pt要与tensorrtx版本匹配!!!**
# 4、执行gen_wts.py生成.wts文件。
`python gen_wts.py -w yolov5s.pt`

# 5、接下来去到目录tensorrtx下的yolov5文件夹
创建一个build文件,并生成生成makeFile\
mkdir build\
cd build\
cmake ..

# 6、执行makeFile。（每次修改为CLASS_NUM都要make一次）
make -j

# 7、将第4步生成的.wts文件复制到tensorrtx/yolov5里。

# 8、生成.engine文件（我用的是yolov5s，所以结尾用s）
`sudo ./yolov5 -s ../yolov5s.wts yolov5s.engine s`\
    如果你训练时是自定义depth_multiple 和 width_multiple就这样写：\
`sudo ./yolov5 -s ../yolov5.wts yolov5.engine c 0.17 0.25`\
    在tensorrtx 5.0里也更新了yolov5的P6模型：\
`sudo ./yolov5 -s ../yolov5.wts yolov5.engine s6`\

# 9、用他自带的图片(在samples里有两张图片)测试一下
`sudo ./yolov5 -d yolov5s.engine ../samples`

# 10、修改yolov5_trt.py