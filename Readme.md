����Mobilenet��ͼ�����Ӧ��
��Ŀ������
��ҪĿ��ʵ��ͼ��10����ķ��ࡣ����keras���е�mobilenetv3smallģ�͡����tfliteģ�ͺ���ͨ��GreenWaves��NNtool���ߣ���ֲ��GAP�����������С�
����ϸ�֣�
���ص����ݼ�
ģ�͵�΢��
ѵ���Ĵ���
ѵ�������ս������
NNtool��ֲ�Ĺ���
C������޸ģ��������Ӧ��
������̣�
�������ݼ�����Kaggle���صĹ������ݼ�
Animal pictures of 10 different categories taken from google images
https://www.kaggle.com/datasets/alessiocorrado99/animals10
2.	ѡ��keras�����е�mobilenet_v3small�����ģ�ͱ�������1000����ķ��ࡣ��������һ��ȫ���Ӳ㣬�����۵�10�����ࡣ
3.	����ο�juypter-notebook�����ݣ�������Ҫ�漰���ݼ��ĵ��룬ģ�͵Ľ�����ѵ���Ĺ��̣��������׼ȷ�ʡ�
4.	ѵ���Ľ��������׼ȷ����95.87%�� 
5.	ͨ��tflite_convert ����ת��Ϊtfliteģ�ͣ����������ʽ
tflite_convert --output_file=new.tflite --keras_model_file=old.h5
6.	GreenWaves NNTool����
������ߣ�����tflite/onnx ��׼��ģ�ͣ���nntool�����п��Խ���8bit/16bit���������°汾��nntool����֧�ָ�������������ʽ����Ϊ����������ҪһЩ���ݣ�������������python���ߣ�ת����һЩͼƬ�������������̡�
 
7.	����GreenWaves SDK�����Ľ������ο�GreenWaves��˾�й���github�ϵ��������
https://github.com/GreenWaves-Technologies/gap_sdk
8.	Nntool �����nntool�����tflite�ļ�
nntool file.tflite
	��nntool�����£�
adjust
fusion �Cscale8
imageformt input_1 rgb888 offset_int8
aquant -f 8 result/*.ppm
gen_project ./project
���ս�������Ŀ���ɵ�project�ļ�����
��������GreenWaves��GVSOC����û���κ�gap�����������£��������ģ����gap�������ϵ����ܣ���������
make clean all run platform=gvsoc
9.	ͨ����input_1 �����룬�޸�Ϊ��camera���룬��crop����������������ݵ���Ϊ��224,224,3���Ľṹ���Ϳ��Խ�����ι��ģ�ͣ��������Ľ����
�ܽ���ѧ���ݣ�
ͨ��������ӣ�����Ժ����׵Ľ���һ����Ӧ�ã���10����ķ��ࡣ���ҷǳ����ײ���GreenWaves��GAP�������ϣ��Ӷ�ʵ�ֿ��ٵĲ���ʵ�ʲ�Ʒ��

