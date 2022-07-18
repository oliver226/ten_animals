基于Mobilenet的图像分类应用
项目概述：
主要目的实现图像10个类的分类。利用keras现有的mobilenetv3small模型。获得tflite模型后，再通过GreenWaves的NNtool工具，移植到GAP处理器上运行。
任务细分：
下载的数据集
模型的微调
训练的代码
训练的最终结果评估
NNtool移植的过程
C代码的修改，完成整个应用
具体过程：
下载数据集，从Kaggle下载的公开数据集
Animal pictures of 10 different categories taken from google images
https://www.kaggle.com/datasets/alessiocorrado99/animals10
2.	选用keras中已有的mobilenet_v3small，这个模型本身是做1000个类的分类。我们再用一个全连接层，把类汇聚到10个分类。
3.	代码参考juypter-notebook的内容，代码主要涉及数据集的导入，模型的建立，训练的过程，最后评估准确率。
4.	训练的结果，最后的准确率在95.87%。 
5.	通过tflite_convert 工具转化为tflite模型，具体命令格式
tflite_convert --output_file=new.tflite --keras_model_file=old.h5
6.	GreenWaves NNTool工具
这个工具，接受tflite/onnx 标准的模型，在nntool工具中可以进行8bit/16bit量化。最新版本的nntool工具支持更加灵活的量化方式。因为量化过程需要一些数据，所以我们利用python工具，转化了一些图片，用于量化过程。
 
7.	具体GreenWaves SDK环境的建立，参考GreenWaves公司托管在github上的相关内容
https://github.com/GreenWaves-Technologies/gap_sdk
8.	Nntool 命令，用nntool命令打开tflite文件
nntool file.tflite
	在nntool环境下：
adjust
fusion –scale8
imageformt input_1 rgb888 offset_int8
aquant -f 8 result/*.ppm
gen_project ./project
最终将整个项目生成到project文件夹下
可以利用GreenWaves的GVSOC，在没有任何gap开发板的情况下，评估这个模型在gap处理器上的性能，命令如下
make clean all run platform=gvsoc
9.	通过将input_1 的输入，修改为从camera输入，用crop函数，将输入的数据调整为（224,224,3）的结构，就可以将数据喂给模型，获得推理的结果。
总结已学内容：
通过这个例子，你可以很容易的建议一个新应用，做10个类的分类。并且非常容易部署到GreenWaves的GAP处理器上，从而实现快速的部署实际产品。

